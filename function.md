# 函数

## 函数的定义

函数的定义格式如下：
```
func FUNC_NAME <arg_list> <return_list> {
	<statement>
}
```
> 函数定义中，左大括号必须与`func`在同一行

go语言，**不支持**函数的嵌套(nested)，重载(overload)和默认参数(default parameter)

go语言中，函数是**第一类值**。

## 作用域
在go中，定义在函数外的变量是全局的；定义在函数体内的变量是局部的。
