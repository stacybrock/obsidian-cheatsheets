Troubleshooting weird [[python]] 2.7 install issues...

https://github.com/pyenv/pyenv/issues/273#issuecomment-477106650

> Well, `brew install python` and setting `CFLAGS`/`LDFLAGS` did not help.
> ## Working solution
> 
> First, we confirm the issue
> 
> ```shell
> $ pyenv install 2.7.6
> $ pyenv virtualenv 2.7.6 testme
> $ pyenv activate testme
> $ pip install --no-cache lxml
>     ...
>     ld: file not found: python.exe
>     clang: error: linker command failed with exit code 1 (use -v to see invocation)
>     error: command 'clang' failed with exit status 1
> ```
> 
> Then, as @yyuu [has mentioned](https://github.com/pyenv/pyenv/issues/273#issuecomment-67719984) in this thread in 2014, that `sysconfig` produces incorrect output. Let's see where it's stored:
> 
> ```shell
> $ grep bundle_loader /Users/andrei/.pyenv/versions/2.7.6/lib/python2.7/_sysconfigdata.py
> ./lib/python2.7/_sysconfigdata.py: 'BLDSHARED': 'clang -bundle -bundle_loader python.exe -L/usr/local/opt/readline/lib -L/usr/local/opt/readline/lib -L/usr/local/opt/openssl/lib -L/Users/andrei/.pyenv/versions/2.7.6/lib',
> ./lib/python2.7/_sysconfigdata.py: 'LDCXXSHARED': 'c++ -bundle -bundle_loader /Users/andrei/.pyenv/versions/2.7.6/bin/python2.7',
> ./lib/python2.7/_sysconfigdata.py: 'LDSHARED': 'clang -bundle -bundle_loader python.exe -L/usr/local/opt/readline/lib -L/usr/local/opt/readline/lib -L/usr/local/opt/openssl/lib -L/Users/andrei/.pyenv/versions/2.7.6/lib',
> ```
> 
> Now, if we try removing `bundle_loader` from `clang` arguments since Python 2.7.8+ does not have it there (DON'T DO IT YOURSELF):
> 
> ```shell
> $ sed -i -e "s/-bundle_loader python.exe//g" \ 
>   /Users/andrei/.pyenv/versions/2.7.6/lib/python2.7/_sysconfigdata.py
> 
> $ pip install --no-cache lxml
>     ...
>     ld: symbol(s) not found for architecture x86_64
>     clang: error: linker command failed with exit code 1 (use -v to see invocation)
>     error: command 'clang' failed with exit status 1
> ```
> 
> It seems needed, so we use another way.
> 
> As you may have noticed, `LDCXXSHARED` points to Python correctly, so we try patching the others (in the original `_sysconfigdata.py`, so you have to restore the file manually or reinstall Python if you did the previous step 😄 ):
> 
> ```shell
> $ export p=/Users/andrei/.pyenv/versions/2.7.6
> $ sed -i -e "s~-bundle_loader python.exe~-bundle_loader ${p}/bin/python2.7~g" \ 
>   "$p/lib/python2.7/_sysconfigdata.py"
> ```
> 
> Or more aggressively, if you want to fix all `python.exe` cases in the file:
> 
> ```shell
> $ sed -i -e "s~python.exe~${p}/bin/python2.7~g" "$p/lib/python2.7/_sysconfigdata.py"
> ```
> 
> Now try installing:
> 
> ```shell
> $ pip install --no-cache lxml
> Collecting lxml
>   Downloading lxml-3.7.3.tar.gz (3.8MB)
>     100% |████████████████████████████████| 3.8MB 49.0MB/s
> Installing collected packages: lxml
>   Running setup.py install for lxml ... done
> Successfully installed lxml-3.7.3
> ```
> 
> Done!
