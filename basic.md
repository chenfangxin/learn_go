# 语言基础

`GO`是**编译型**，**静态类型**语言。

## 值类型

| 类型 					| 长度(字节) | 缺省值 | 说明    |
|-----------------------|------------|--------|---------|
| bool  				| 1   		 | false  |			|
| int, uint  			| 4或8 		 | 0	  |			|
| int8, uint8(byte) 	| 1 		 | 0      |			|
| int16, uint16  		| 2 		 | 0      |			|
| int32(rune), uint32 	| 4 		 | 0      |			|
| int64, uint64  		| 8 		 | 0      |			|
| float32				| 4 		 | 0.0    |			|
| float64  				| 8 		 | 0.0    |			|
| complex64				| 8 		 |        |			|
| complex128			| 16 		 |	 	  |			|
| uintptr 				| 4或8 		 | 		  | 足以存放指针的uint	|
| array 				| 			 | 		  | 数组，值类型  |
| struct 				| 			 | 		  | 结构体，值类型  |
| string 				| 			 | "" 	  | 字符串是不可变的 |
| slice 				| 			 | nil	  | 引用类型|
| map 					| 			 | nil	  | 引用类型 |
| channel 				| 			 | nil	  | 引用类型 |
| function 				| 			 | nil	  | 函数     |
| interface 			|			 | nil	  | 接口     |

> 所谓`引用类型`是指`slice`, `map`,`channel`这三种与定义类型。创建这些类型的数据，除了要分配内存外，还需要一系列复杂的初始化工作。

## 变量和常量

变量(varable)的**值**是可变的，其本质是一段存储数据的内存。常量(constant)的值是不可变的，其值必须是编译期可确定的数值，字符串或bool类型。

#### 变量的声明

在go语言中，变量的声明(declare)和定义(define)是放在一起的，也就是说变量总会被初始化。在go中，有三种形式声明变量：
```
var a int = 12	# 声明变量a的类型为int，并初始化为12
var a int		# 声明变量a的类型为int，并初始化为0
a := 12			# 声明变量a，并通过初始值推导其类型。这种形式只能在函数体中使用
```

#### 变量的赋值

在go语言中，使用`=`运算符给变量赋值。需要注意的是，go中没有隐含的类型转换！
```
var a int
var b uint

a = 15
b = a 		# 这句会报错！
b = uint(a) # 需要明确的类型转换
```

go语言支持平行赋值：
```
var x, y int
x, y = 12, 16
_, b := 1, 2	# 任何给特殊的变量_赋值，都会被丢弃
```

#### 常量的定义

在go中，使用关键字`const`定义常量。
```
const a, b = 12, 13  # 多常量初始化
const c = "hello"	 # 类型推导
```

## 运算符

go语言支持如下运算符：
| 运算符 | 说明 |
|--------|------|
| `*`	 | 乘法 |
| `/`	 | 除法 |
| `%`	 | 取余 | 
| `<<`	 | 左移 | 
| `>>`	 | 右移 |
| `&`	 | (二元)位与，(一元)取地址 |
| `|`	 | 位或 |
| `^`	 | (二元)位异或, (一元)位取反 |
| `&^`	 | 位清除 |
| `+`	 | 加法 |
| `++`	 | 自增 |
| `-`	 | 减法 |
| `--`	 | 自减 |
| `=`	 | 赋值 |
| `:=`	 | 带类型推导的赋值 |
| `==`,`!=`	 | 等于/不等于 |
| `>`	 | 大于 |
| `<`	 | 小于 |
| `&&`	 | 逻辑与 |
| `||`	 | 逻辑或 |
| `!`	 | 逻辑非 |
| `<-`	 | 数据流向 |

> 语句(statement)和表达式(expression)的区别：语句表示一个操作，不能用于赋值场景。表达式除了表示一系列动作外，还有其代表的值，可以用于赋值。
> 在go语言中，++ 和 -- 是**语句**

## 关键字

| 关键字 | 说明 |
|---------------|------|
| break 		| 跳出当前或指定的循环体 	|
| case 			| 用于switch/select场景 	|
| chan 			| 							|
| const 		| 常量定义 					|
| continue 		| 忽略当前循环体的余下代码 	|
| default 		| 用于switch/select场景 	|
| defer 		|							|
| else 			|							|
| fallthrough 	|							|
| for 			| 循环 						|
| func 			| 定义函数 					|
| go 			|							|
| goto 			|							|
| if 			|							|
| import 		|							|
| interface 	|							|
| map 			|							|
| package 		|							|
| range 		|							|
| return 		|							|
| select 		|							|
| struct 		|							|
| switch 		|							|
| type 			|							|
| var 			| 定义变量					|

## 内建函数

内建函数是预定义的，无需引入任何包就可以使用的函数。

| 函数名  | 说明 |
|---------|------|
| close   |		|
| delete  |		|
| len     |		|
| cap 	  |		|
| new	  |		|
| make 	  |		|
| append  |		|
| copy    |		|
| panic   |		|
| recover |		|
| print   |		|
| println |		|
| complex |		|
| real    |		|
| imag    |		|

## 控制结构


## 函数

