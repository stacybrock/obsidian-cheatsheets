# Python Tricks

Some handy [[python]] tricks...

## Deserialize Bad Single-Quoted "JSON" Strings
Use `ast.literal_eval()`:

```python
> import ast
> s = "{'CreationTime': '2019-09-17T15:14:02', 'Id': 'xxxxxxa9-1d17-4705-d991-08d73b81ac26', 'Operation': 'Start-MigrationUser'}"
> x = ast.literal_eval(s)
> x
{ 'CreationTime': '2019-09-17T15:14:02', 'Id': 'xxxxxxa9-1d17-4705-d991-08d73b81ac26', 'Operation': 'Start-MigrationUser' }
```
## Run a Mock SMTP Server
```
$ python -m smtpd -n -c DebuggingServer localhost:2525
```
