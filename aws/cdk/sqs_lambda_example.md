# AWS CDK: SQS Event Source for Lambda Example
Basic example of configuring SQS as an event source to trigger a Lambda execution with [[cdk]]...

```python
from aws_cdk import (
    core,
    aws_lambda as _lambda,
    aws_lambda_event_sources as lambda_event,
    aws_sqs as sqs
)

class SomeStack(core.Stack):

    def __init__(self, scope: core.Construct, id: str, **kwargs) -> None:
        super().__init__(scope, id, **kwargs)

        sqs_queue = sqs.Queue.from_queue_arn(
            self, 'queue-1.fifo',
            'arn:aws:sqs:us-west-2:xxx:queue-1.fifo'
        )
        sqs_source = lambda_event.SqsEventSource(
            queue=sqs_queue,
            batch_size=1
        )

        # testo Lambda Function to execute queued DMS tasks
        testo_executor_fn = _lambda.Function(
            self, 'Testo',
            code=_lambda.AssetCode.asset('lambda'),
            handler='testo.lambda_handler',
            events=[
                sqs_source
            ],
            environment={
                'SOME_ENVVAR': '3'
            },
            runtime=_lambda.Runtime.PYTHON_3_7,
            role=task_executor_role, # defined elsewhere
            timeout=core.Duration.minutes(1)
        )
```

Invocation Example:

```
| 1594244454449 | START RequestId: 2b803f11-a6dd-55c9-8c30-68919978ce77 Version: $LATEST
| 1594244454450 | DEBUG: us-west-2
| 1594244454450 | event:
| 1594244454450 | { 'Records': [ { 'attributes': { 'ApproximateFirstReceiveTimestamp': '1594242299213',
| 1594244454450 | 'ApproximateReceiveCount': '2',
| 1594244454450 | 'SenderId': 'somesenderid',
| 1594244454450 | 'SentTimestamp': '1594242224523'},
| 1594244454450 | 'awsRegion': 'us-west-2',
| 1594244454450 | 'body': '{"s3_bucket": "somebucket", "log_folder": '
| 1594244454450 | '"somefolder", "year": "2020", "month": '
| 1594244454450 | '"07", "day": "08", "hour": "14"}',
| 1594244454450 | 'eventSource': 'aws:sqs',
| 1594244454450 | 'eventSourceARN': 'arn:aws:sqs:us-west-2:55555555555:somelambda',
| 1594244454450 | 'md5OfBody': 'somemd5',
| 1594244454450 | 'messageAttributes': {},
| 1594244454450 | 'messageId': 'c6fa904f-4d73-4197-9035-14672415c785',
| 1594244454450 | 'receiptHandle': 'AQEBi30vRzsnKj5PRfbumCWlNStRE3+IQEwpr5TUT/yQ4jBbKzaoRFToB9e3aUM+xCbNI11O04odFC1CDXxiwCENCaDw2K+MRuRTC3xhRJxeuQgLBAq4tYt9+U23hJ+CWAkYw8hiYveQiuzbAtKPJbMn/9eER8D4lg0V0fhn9x6HgE3htDeWGHep5Sq1ggLWiORei0VY/eN80b2YRUPMvUks1Ky41HFN9/RueZZZYGEI2/nc6d1o5K1ik9Gzb1rI2hl7bus2Aa8EtDcI4Mwt3b3cr4JTT2swoGCMI3IHjV9ZNZ5dkkWPtMkQ7Zq7k385QJ6/PXAIYXS1Q3dgetpApm12uq5HvlPfYGwolihvHahc+1d5eMK7gMGY/l2c6s6QXfz50I/eoQL7Z0Zb2dcoRez2ZXzv//Mhdxxqy77C419dVyxsmNmOmou2cLouzvQ9Xt66'}]}
| 1594244454450 | context:
| 1594244454450 | <bootstrap.LambdaContext object at 0x7f3494d450d0>
| 1594244454466 | END RequestId: 2b803f11-a6dd-55c9-8c30-68919978ce77
| 1594244454466 | REPORT RequestId: 2b803f11-a6dd-55c9-8c30-68919978ce77 Duration: 16.42 ms Billed Duration: 100 ms Memory Size: 128 MB Max Memory Used: 75 MB Init Duration: 406.66 ms
```
