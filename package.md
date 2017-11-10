# 包管理

go语言的包管理有如下特点：

+ 每个go语言源文件开头，都用`package`语句，标明本文件所属的包。
+ go语言中，一个package可以由多个文件组成，经过编译后，其实和一个文件类似。同一个package的不同文件之间可以直接引用变量和函数。
+ go语言中，不强制要求package和所在的目录同名，但是最好保持一致。
+ go语言中，一个子目录只能存在一个package
+ go语言中，package是以绝对路径`GOPATH`来寻址。 

要生成go可执行文件，必须有一个package名为`main`，并且该package中必须有一个名为`main`的函数，作为程序的入口。

`import`语句中指定的是package所在的目录名；而在程序中，通过package名来使用package。这二者往往是同名的，虽然并不强制要求。

go语言规定：在package中，首字母**大写**的标识符(变量，函数等)是公开的，可以被外界访问；首字母**小写**的标识符是package私有的。

> go语言规定`import`导入的package，必须被使用，否则会编译不过。可以使用空白标识符`_`来重命名不用的package


## package的init函数

每个package都可以包含**任意多个**`init`函数，这些`init`函数会在`main`之前执行。`init`函数被用来作初始化工作。

