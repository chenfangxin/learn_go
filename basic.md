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
| array 				| 			 | 		  | 数组，值类型,长度固定  |
| struct 				| 			 | 		  | 结构体，值类型  |
| string 				| 			 | "" 	  | 字符串是不可变的 |
| slice 				| 			 | nil	  | 引用类型|
| map 					| 			 | nil	  | 引用类型 |
| channel 				| 			 | nil	  | 引用类型 |
| function 				| 			 | nil	  | 函数     |
| interface 			|			 | nil	  | 接口     |

> 所谓`引用类型`是指`slice`, `map`,`channel`这三种预定义类型。创建这些类型的数据，除了要分配内存外，还需要一系列复杂的初始化工作。使用make()函数来创建。

## 变量和常量

变量(varable)的**值**是可变的，其本质是一段存储数据的内存。常量(constant)的值是不可变的，其值必须是编译期可确定的数值，字符串或bool类型。

#### 变量的声明

在go语言中，变量的声明(declare)和定义(define)是放在一起的，也就是说变量总会被初始化。在go中，有三种形式声明变量：
```
var a int = 12 # 声明变量a的类型为int，并初始化为12
var b int      # 声明变量b的类型为int，并初始化为0
c := 12        # 声明变量c，并通过初始值推导其类型。这种形式只能在函数体中使用

var ary1 [5]int # 定义一个5个int元素的array
ary1[0] = 1     # 给array的元素赋值

var ary2 [5]int{1,2,3,4,5} # 给array提供初始值 
ary2 := [...]int{1,2,3,4,5} # 自动推导数组大小，`...`不可省略，否则成了slice

var slc1 []int # 定义一个int类型的slice
slc2 := []int{1,2,3,4,5} # 定义并初始化一个slice
slc3 := make([]int, 5)	# 使用make函数，创建一个slice，长度和容量都设为5

var map1 map[string]int # 声明一个map，key类型为string, value类型为int
map1 = make(map[string]int) # 创建map
map1["key1"] = 1 # 向map添加元素

var map2 = map[string]int {} # 声明并初始化一个map
map2["key2"] = 2
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

+ 算术运算: `*`, `/`, `%`, `+`, `++`, `-`, `--`
+ 关系运算: `==`, `!=`, `>`, `>=`, `<`, `<=`
+ 逻辑运算: `&&`, `||`, `!`
+ 位运算: `<<`, `>>`, `&`, `|`, `^`, `&^`
+ 赋值运算: `=`, `:=`, `+=`, `-=`, `*=`, `/=`, `%=`, `<<=`, `>>=`, `&=`, `|=`, `^=`
+ 其他运算符: `&`(一元，取地址), `*`(一元，指针变量) ,`<-`(数据流向)

> 语句(statement)和表达式(expression)的区别：语句表示一个操作，不能用于赋值场景。表达式除了表示一系列动作外，还有其代表的值，可以用于赋值。
> 在go语言中，++ 和 -- 是**语句**

> go语言**不支持**运算符的重载

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
| range 		| 迭代器，用于slice, array, string, map, channel |
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
| close   | 用于关闭channel	|
| delete  | 用于删除map中的元素	|
| len     | 用于返回string, slice和array的长度 		|
| cap 	  | 用于返回array,slice,channel的容量		|
| new	  | 用于各种类型的内存分配		|
| make 	  | 用于内建类型(map, slice, channel)的内存分配		|
| append  | 用于追加slice		|
| copy    | 用于复制slice		|
| panic/recover   | 用于异常处理		|
| print/println   | 底层的打印函数		|
| complex/real/imag | 用于处理复数		|

## 控制结构

#### `if...else`
`if...else`结构中，大括号是必须的,且要与if在同一行, 
```
if <condition> { // <condition>不用小括号
	<statement>
} else {
	<statement>
}

```

#### `for`循环
go语言中`for`循环中的大括号是必须的，且要与`for`在同一行。`for`循环有3种形式：
```
for <init>; <condition>; <post> {
}

for <condition> {
}

for { // 死循环
}
```

#### `switch...case`
`switch...case`语句中，大括号也是必须的，且要与`switch`在同一行。`<condition>`也不是必须的。
```
switch <condition> {
	case <expr1> : <statement1>
	case <expr2> : <statement2>
	...
	default:
			<statement>
}
```
go语言的`switch`语句中，每个`case`语句都是独立的，并不需要`break`跳出执行。`case`语句中有`fallthrougth`关键字，会继续执行下一个`case`。

`switch`后的`<condition>`**不是**必须的，每个`case`相当于一个`if`语句。


## 函数


