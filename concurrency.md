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
var ch_a = make(char int, 5) // 传递int类型数据，有5个缓存
```
