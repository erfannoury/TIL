To output a particular line range from a file, you can use `sed`.
Imaging that you want to extract lines 100 through 200 of a file. You can use the following command:
```
$ sed -n '100,200p;201q' <somefile>
```

You can also add `>` to write the results into a file
```
$ sed -n '100,200p;201q' <somefile> > <newfile>
```
[Source](https://stackoverflow.com/a/83347/5069650)
