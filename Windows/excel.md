Excel has this great feature that can fill out values of cells based on a pattern from some other cells. It's a very capable feature and I'm sure it has some advanced tricks.

One trick that I always wanted to know was how to keep a variable constant in a formula, while let Excel know that it can increment the other variable as usual.

Apparently, `$` is the key. If you put `$` before a variable, it will stay constant. Keep in mind that a cell is determined by two variables, a row variable and a column variable. 

I found out about this feature from [this SO answer](https://stackoverflow.com/questions/2156563/how-to-keep-one-variable-constant-with-other-one-changing-with-row-in-excel).
