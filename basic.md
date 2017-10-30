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
| uintptr 				| 4或8 		 |		  |			|
| array 				| 			 | 		  | 值类型  |
| struct 				| 			 | 		  | 值类型  |
| string 				| 			 | "" 	  | 	    |
| slice 				| 			 | nil	  | 引用类型|
| map 					| 			 | nil	  | 引用类型 |
| channel 				| 			 | nil	  | 引用类型 |
| interface 			|			 | nil	  | 接口     |
| function 				| 			 | nil	  | 函数     |


## 变量和常量


