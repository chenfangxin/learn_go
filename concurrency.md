# 并发

go语言使用`groutine`和`channel`实现CSP(Communicating Sequential Processes)模型。`groutine`是执行序列；`channel`是`groutine`之间的通讯和同步机制。

#### 使用groutine

可以把`groutine`视为另一种形式的**函数调用**，是并行执行的函数。示例如下：

```
func test_g(){
	fmt.Println("Hello Groutine")
}

func main(){
	go test_g()  // 使用go语句，将函数加入全觉得groutine执行序列中，等待被调度
	time.Sleep(time.Second) // 主执行序列在此等待
}
```

#### 使用channel

`channel`是`groutine`之间传递数据的结构。创建`channel`时，要指定需要传递的数据类型，和是否有缓存。如下：

```
var i = 10
var ch_a = make(char int, 5) // 传递int类型数据，有5个缓存

ch_a <- i  // 将i的值传入channel
```

`channel`要注意的特性：
+ 未赋值的channel称为nil channel，close一个nil channel会导致panic；读写nil channel会导致永久阻塞
+ 多次close同一个channel，会导致panic。一般由发送者close
+ 当close一个channel时，所有因为读取该channel而阻塞的groutine都将立即向后执行 
+ 向已经close的channel写数据，会导致panic；从已经close的channel读数据，会得到channel对应类型的零值

由于读取close了的channel会返回零值，将导致程序无法判断读取的数据是否正常，此时需要用channel返回的第二个返回值，来判断channel是否关闭，如下：

```
if b, ok := <- ch_a; !ok { // channel已经关闭
	fmt.Println("channel closed")
}
```

#### 使用select

go语言中，使用`select-case`结构在多个`channel`上监听IO事件，当某个case上产生了IO事件，就执行其对对应的代码块，示例如下：
```
c1 := make(chan int)
c2 := make(chan int)

go func() {
	c1<-1
}()

select{
	case a := <-c1 :
		fmt.Println("read from c1, a=", a)
	case a := <-c2 :
		fmt.Println("read from c2, a=", a)
}
```

