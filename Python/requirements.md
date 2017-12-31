I don't know how to create `requiremenets.txt` file, at least I didn't know, and I now know, thanks to [this post](http://www.idiotinside.com/2015/05/10/python-auto-generate-requirements-txt/).

You first need to install `pipreqs` package
```bash
$ pip install pipreqs
```
and then by using the following command, a `requirements.txt` file will be created automatically.
```bash
$ pipreqs path/to/project
```
