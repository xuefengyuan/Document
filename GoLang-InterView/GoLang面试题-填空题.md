[TOC]

#### GoLang面试题-填空题，附答案

===================================================================

##### 1.【初级】声明一个整型变量i _______________

答案：<font color=blue>`var i int`</font>

##### 2.【初级】声明一个含有10个元素的整型数组a _______________

答案：<font color=blue>`var a [10]int`</font>

##### 3.【初级】声明一个整型数组切片s _______________

答案：<font color=blue>`var s []int`</font>

##### 4.【初级】声明一个整型指针变量p _______________

答案：<font color=blue>`var p *int`</font>

##### 5.【初级】声明一个key为字符串型value为整型的map变量m _______________

答案：<font color=blue>`var m map[string]int`</font>

##### 6.【初级】声明一个入参和返回值均为整型的函数变量f _______________

答案：<font color=blue>`var f func(a int)int`</font>

##### 7.【初级】声明一个只用于读取int数据的单向channel变量ch _______________

答案：<font color=blue>`var ch <-chan int`</font>

##### 8.【初级】假设源文件的命名为slice.go，则测试文件的命名为 _______________

答案：<font color=blue>`slice_test.go`</font>

##### 9.【初级】 go test要求测试函数的前缀必须命名为 _______________

答案：<font color=blue>`Test`</font>

##### 10.【中级】下面的程序的运行结果是 _______________
```go
for i := 0; i < 5; i++ {
	defer fmt.Printf("%d ", i)
}
```
答案：<font color= blue>`4 3 2 1 0`</font>

##### 11.【中级】下面的程序的运行结果是 _______________

```go
func main() {
    x := 1
    {
        x := 2
        fmt.Print(x)
    }
    fmt.Println(x)
}
```
答案：<font color=blue>`21`</font>

##### 12.【中级】下面的程序的运行结果是 _______________

```go
func main4() {
    strs := []string{"one", "two", "three"}
    for _, s := range strs {
        go func() {
            time.Sleep(1 * time.Second)
            fmt.Printf("%s ", s)
        }()
    }
    time.Sleep(3 * time.Second)
}
```

答案：<font color=blue>`three three three`</font>

##### 13.【中级】下面的程序的运行结果是 _______________

```go
func main() {
    x := []string{"a", "b", "c"}
    for v := range x {
        fmt.Print(v)
    }
}
```

答案：<font color=blue>`012`</font>

##### 14.【中级】下面的程序的运行结果是 _______________

```go
func main() {
    x := []string{"a", "b", "c"}
    for _,v := range x {
        fmt.Print(v)
    }
}
```

答案：<font color=blue>`abc`</font>

##### 15.【中级】下面的程序的运行结果是 _______________

```go
func main() {
    i := 1
    j := 2
    i, j = j, i
    fmt.Printf("%d%d\n", i, j)
}
```

答案：<font color=blue>`21`</font>

##### 16.【中级】下面的程序的运行结果是 _______________

```go
func incr(p *int) int {
    *p++
    return *p
}

func main7() {
    v := 1
    incr(&v)
    fmt.Println(v)
}
```

答案：<font color=blue>`2`</font>

##### 17.【中级】下面的程序的运行结果是 _______________

```go
type Slice []int

func NewSlice() Slice {
    return make(Slice, 0)
}

func (s *Slice) Add(elem int) *Slice {
    *s = append(*s, elem)
    fmt.Print(elem)
    return s
}

func main() {
    s := NewSlice()
    defer s.Add(1).Add(2)
    s.Add(3)
}
```

答案：<font color=blue>`132`</font>

