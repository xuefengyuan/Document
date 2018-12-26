[TOC]

### GoLang面试题-选择题，附答案

#### 1-10

##### 1.【初级】下面属于关键字的是（）

```go
A. func
B. def
C. struct
D. class
```

答案：AC

##### 2.【初级】定义一个包内全局字符串变量，下面语法正确的是（）

```go
A. var str string
B. str := ""
C. str = ""
D. var str = ""
```

答案：AD

##### 3.【初级】通过指针变量 p 访问其成员变量 name，下面语法正确的是（）

```go
A. p.name
B. (*p).name
C. (&p).name
D. p->name
```

答案：AB

##### 4.【初级】关于接口和类的说法，下面说法正确的是（）

> <font color=blue>A. 一个类只需要实现了接口要求的所有函数，我们就说这个类实现了该接口</font>
> <font color=blue>B. 实现类的时候，只需要关心自己应该提供哪些方法，不用再纠结接口需要拆得多细才合理</font>
> <font color=red>C. 类实现接口时，需要导入接口所在的包</font>
> <font color=blue>D. 接口由使用方按自身需求来定义，使用方无需关心是否有其他模块定义过类似的接口</font>

答案：ABD

##### 5.【初级】关于字符串连接，下面语法正确的是（）

```go
A. str := ‘abc’ + ‘123’
B. str := "abc" + "123"
C. str ：= '123' + "abc"
D. fmt.Sprintf("abc%d", 123)
```

答案：BD

##### 6.【初级】关于协程，下面说法正确是（）

> <font color=blue>A. 协程和线程都可以实现程序的并发执行 </font>
> <font color=red>B. 线程比协程更轻量级</font>
> <font color=red>C. 协程不存在死锁问题</font>
> <font color=blue>D. 通过channel来进行协程间的通信</font>

答案：AD

##### 7.【中级】关于init函数，下面说法正确的是（）

> <font color=blue>A. 一个包中，可以包含多个init函数</font>
> <font color=blue>B. 程序编译时，先执行导入包的init函数，再执行本包内的init函数</font>
> <font color=red>C. main包中，不能有init函数</font>
> <font color=red>D. init函数可以被其他函数调用</font>

答案：AB

##### 8.【初级】关于循环语句，下面说法正确的有（）

> <font color=red>A. 循环语句既支持for关键字，也支持while和do-while</font>
> <font color=red>B. 关键字for的基本使用方法与C/C++中没有任何差异</font>
> <font color=blue>C. for循环支持continue和break来控制循环，但是它提供了一个更高级的break，可以选择中断哪一个循环</font>
> <font color=blue>D. for循环不支持以逗号为间隔的多个赋值语句，必须使用平行赋值的方式来初始化多个变量 </font>

答案：CD

##### 9.【中级】对于函数定义：

```go
func add(args ...int) int {
    sum := 0
    for _, arg := range args {
        sum += arg
    }
    return sum
}
```

下面对add函数调用正确的是（）

> <font color=blue>A. add(1, 2)</font>
> <font color=blue>B. add(1, 3, 7)</font>
> <font color=red>C. add([]int{1, 2})</font>
> <font color=blue>D. add([]int{1, 3, 7}...)</font>

答案：ABD

##### 10.【初级】关于类型转化，下面语法正确的是（）

A:

```go
type MyInt int
var i int = 1
var jMyInt = i
```

B:

```go
type MyIntint
var i int= 1
var jMyInt = (MyInt)i
```

<font color=blue>C:</font>

```go
type MyIntint
var i int= 1
var jMyInt = MyInt(i)
```

D:

```go
type MyIntint
var i int= 1
var jMyInt = i.(MyInt)
```

答案：C

#### 11-20

##### 11.【初级】关于局部变量的初始化，下面正确的使用方式是（）

```go
A. var i int = 10
B. var i = 10
C. i := 10
D. i = 10
```

答案：ABC

##### 12.【初级】关于const常量定义，下面正确的使用方式是（）

```go
A:
const Pi float64 = 3.14159265358979323846
const zero= 0.0
B:
const (
    size int64= 1024
    eof = -1
)
C:
const (
    ERR_ELEM_EXISTerror = errors.New("element already exists")
    ERR_ELEM_NT_EXISTerror = errors.New("element not exists")
)
D:
const u, vfloat32 = 0, 3
const a,b, c = 3, 4, "foo"
```

答案：ABD

##### 13.【初级】关于布尔变量b的赋值，<font color=red>下面错误的用法是</font>（）

```go
A. b = true
B. b = 1
C. b = bool(1)
D. b = (1 == 2)
```

答案：BC

##### 14.【中级】下面的程序的运行结果是（）

```go
func main() {
    if (true) {
        defer fmt.Printf("1")
    }else{
        defer fmt.Printf("2")
    }
    fmt.Printf("3")
}
```

> A. 321
> B. 32
> <font color=blue>C. 31</font>
> D. 13

答案：C

##### 15.【初级】关于switch语句，下面说法正确的有（）

> <font color=red>A. 条件表达式必须为常量或者整数</font>
> <font color=blue>B. 单个case中，可以出现多个结果选项</font>
> <font color=red>C. 需要用break来明确退出一个case</font>
> <font color=blue>D. 只有在case中明确添加fallthrough关键字，才会继续执行紧跟的下一个case</font>

答案：BD

##### 16.【中级】 golang中没有隐藏的this指针，这句话的含义是（）

> <font color=blue>A. 方法施加的对象显式传递，没有被隐藏起来</font>
> <font color=red>B. golang沿袭了传统面向对象编程中的诸多概念，比如继承、虚函数和构造函数</font>
> <font color=blue>C. golang的面向对象表达更直观，对于面向过程只是换了一种语法形式来表达</font>
> <font color=blue>D. 方法施加的对象不需要非得是指针，也不用非得叫this</font>

答案：ACD

##### 17.【中级】 golang中的引用类型包括（）

> <font color=blue>A. 数组切片</font>
> <font color=blue>B. map</font>
> <font color=blue>C. channel</font>
> <font color=blue>D. interface</font>

答案：ABCD

##### 18.【中级】 golang中的指针运算包括（）

> <font color=red>A. 可以对指针进行自增或自减运算 </font>
> <font color=blue>B. 可以通过“&”取指针的地址</font>
> <font color=blue>C. 可以通过“*”取指针指向的数据</font>
> <font color=red>D. 可以对指针进行下标运算</font>

答案：BC

##### 19.【初级】关于main函数（可执行程序的执行起点），下面说法正确的是（）

> <font color=blue>A. main函数不能带参数</font>
> <font color=blue>B. main函数不能定义返回值</font>
> <font color=blue>C. main函数所在的包必须为main包</font>
> <font color=blue>D. main函数中可以使用flag包来获取和解析命令行参数</font>

答案：ABCD

##### 20.【中级】下面赋值正确的是（）

```go
A. var x = nil
B. var x interface{} = nil
C. var x string = nil
D. var x error = nil
```

答案：BD

#### 21-30

##### 21.【中级】从切片中删除一个元素，下面的算法实现正确的是（）

A:
```go
func (s *Slice) Remove(value interface{}) error {
    for i, v := range *s {
         if isEqual(value, v) {
              if i == len(*s)-1 {
                *s = (*s)[:i]
                } else {
                 *s = append((*s)[:i], (*s)[i+2:]...)
                }
            return nil
        }
    }
    return ERR_ELEM_NT_EXIST
}
```
B:
```go
func (s*Slice)Remove(value interface{}) error {
    for i, v:= range *s {
        if isEqual(value, v) {
           *s =append((*s)[:i],(*s)[i + 1:])
           return nil
        }
    }
    return ERR_ELEM_NT_EXIST
}
```
C:
```go
func (s*Slice)Remove(value interface{}) error {
    for i, v:= range *s {
        if isEqual(value, v) {
           delete(*s, v)
           return nil
        }
    }
    return ERR_ELEM_NT_EXIST
}
```
<font color=blue>D:</font>

```go
func (s*Slice)Remove(value interface{}) error {
    for i, v:= range *s {
        if isEqual(value, v) {
            *s =append((*s)[:i],(*s)[i + 1:]...)
            return nil
        }
    }
    return ERR_ELEM_NT_EXIST
}
```

答案：D

##### 22.【初级】对于局部变量整型切片x的赋值，下面定义正确的是（）

```go
A:
x := []int{
 1, 2, 3,
 4, 5, 6,
}
B:
x :=[]int{
        1, 2, 3,
        4, 5, 6
    }
C:
x :=[]int{
        1, 2, 3,
        4, 5, 6}
D:
x :=[]int{1, 2, 3, 4, 5, 6,}
```

答案：ACD

##### 23.【初级】关于变量的自增和自减操作，下面语句正确的是（）

```go
A:
i := 1
i++
B:
i := 1
j = i++
C:
i := 1
++i
D:
i := 1
i--
```

答案：AD

##### 24.【中级】关于函数声明，<font color=red>下面语法错误的是</font>（）

```go
A. func f(a, b int) (value int, err error)
B. func f(a int, b int) (value int, err error)
C. func f(a, b int) (value int, error)
D. func f(a int, b int) (int, int, error)
```

答案：C

##### 25.【中级】如果Add函数的调用代码为：

```go
func main() {
    var a Integer = 1
    var b Integer = 2
    var i interface{} = &a
    sum := i.(*Integer).Add(b)
    fmt.Println(sum)
}
```

则Add函数定义正确的是（）

<font color=blue>A:</font>

```go
type Integer int

func (a Integer) Add(b Integer) Integer {
     return a + b
}
```

<font color=red>B:</font>

```go
type Integer int

func (a Integer) Add(b *Integer) Integer {
     return a + *b
}
```

<font color=blue>C:</font>

```go
type Integer int

func (a *Integer) Add(b Integer) Integer {
     return *a + b
}
```

<font color=red>D:</font>

```go
type Integer int

func (a*Integer) Add(b *Integer) Integer {
     return *a + *b
}
```

答案：AC

##### 26.【中级】如果Add函数的调用代码为

则Add函数定义正确的是（）

<font color=blue>A:</font>

```go
type Integer int

func (a Integer)Add(b Integer) Integer {
    return a + b
}
```

B:

```go
type Integer int

func a Integer) Add(b *Integer) Integer {
    return a + *b
}
```

C:

```go
type Integer int

func (a *Integer) Add(b Integer) Integer {
    return *a + b
}
```

D:

```go
type Integer int

func (a*Integer) Add(b *Integer) Integer {
    return *a + *b
}
```

答案：A

##### 27.【中级】关于GetPodAction定义，下面赋值正确的是（）

```go
type Fragment interface {
    Exec(transInfo *TransInfo) error
}

type GetPodAction struct {
}

func (g GetPodAction) Exec(transInfo *TransInfo) error {

    return nil
}
```

```go
A. var fragment Fragment = new(GetPodAction)
B. var fragment Fragment = GetPodAction
C. var fragment Fragment = &GetPodAction{}
D. var fragment Fragment = GetPodAction{}
```

答案：ACD

##### 28.【中级】关于GoMock，下面说法正确的是（）

> <font color=blue>A. GoMock可以对interface打桩 </font>
> <font color=red>B. GoMock可以对类的成员函数打桩</font>
> <font color=red>C. GoMock可以对函数打桩</font>
> <font color=blue>D. GoMock打桩后的依赖注入可以通过GoStub完成</font>

答案：AD

##### 29：【中级】关于接口，下面说法正确的是（）

> A. 只要两个接口拥有相同的方法列表（次序不同不要紧），那么它们就是等价的，可以相互赋值
> B. 如果接口A的方法列表是接口B的方法列表的子集，那么接口B可以赋值给接口A
> C. 接口查询是否成功，要在运行期才能够确定
> <font color=red>D. 接口赋值是否可行，要在运行期才能够确定</font>

答案：ABC

##### 30.【初级】关于channel，下面语法正确的是（）

```go
A. var ch chan int
B. ch := make(chan int)
C. <- ch
D. ch <-
```

答案：ABC

#### 31-40

##### 31.【初级】关于同步锁，下面说法正确的是（）

> A. 当一个goroutine获得了Mutex后，其他goroutine就只能乖乖的等待，除非该goroutine释放这个Mutex
> B. RWMutex在读锁占用的情况下，会阻止写，但不阻止读
> C. RWMutex在写锁占用情况下，会阻止任何其他goroutine（无论读和写）进来，整个锁相当于由该goroutine独占
> <font color=red>D. Lock()操作需要保证有Unlock()或RUnlock()调用与之对应</font>

答案：ABC

##### 32.【中级】 golang中大多数数据类型都可以转化为有效的JSON文本，下面几种类型除外（）

> <font color=red>A. 指针</font>
> B. channel
> C. complex
> D. 函数

答案：BCD

##### 33.【中级】关于go vendor，下面说法正确的是（）

> A. 基本思路是将引用的外部包的源代码放在当前工程的vendor目录下面
> B. 编译go代码会优先从vendor目录先寻找依赖包
> <font color=red>C. 可以指定引用某个特定版本的外部包</font>
> D. 有了vendor目录后，打包当前的工程代码到其他机器的$GOPATH/src下都可以通过编译

答案：ABD

##### 34.【初级】 flag是bool型变量，下面if表达式符合编码规范的是（）

```go
A. if flag == 1
B. if flag
C. if flag == false
D. if !flag
```

答案：BD

##### 35.【初级】 value是整型变量，下面if表达式符合编码规范的是（）

```go
A. if value == 0
B. if value
C. if value != 0
D. if !value
```

答案：AC  

##### 36.【中级】关于函数返回值的错误设计，下面说法正确的是（）

> <font color=blue>A. 如果失败原因只有一个，则返回bool</font>
> <font color=blue>B. 如果失败原因超过一个，则返回error</font>
> <font color=blue>C. 如果没有失败原因，则不返回bool或error</font>
> <font color=blue>D. 如果重试几次可以避免失败，则不要立即返回bool或error</font>

答案：ABCD  

##### 37.【中级】关于异常设计，下面说法正确的是（）

> A. 在程序开发阶段，坚持速错，让程序异常崩溃
> B. 在程序部署后，应恢复异常避免程序终止
> <font color=red>C. 一切皆错误，不用进行异常设计</font>
> D. 对于不应该出现的分支，使用异常处理

答案：ABD  

##### 38.【中级】关于slice或map操作，下面正确的是（）

A:

```go
var s []int
s =append(s,1)
```

<font color=red>B:</font>

```go
var m map[string]int
m["one"]= 1
```

C:

```go
var s[]int
s =make([]int, 0)
s =append(s,1)
```

D:

```go
var m map[string]int
m = make(map[string]int)
m["one"]= 1
```

答案：ACD

##### 39.【中级】关于channel的特性，下面说法正确的是（）

> <font color=blue>A. 给一个 nil channel 发送数据，造成永远阻塞</font>
> <font color=blue>B. 从一个 nil channel 接收数据，造成永远阻塞</font>
> <font color=blue>C. 给一个已经关闭的 channel 发送数据，引起 panic</font>
> <font color=blue>D. 从一个已经关闭的 channel 接收数据，如果缓冲区中为空，则返回一个零值</font>

答案：ABCD

#### 40-49

##### 40.【中级】关于无缓冲和有冲突的channel，下面说法正确的是（）

> A. 无缓冲的channel是默认的缓冲为1的channel
> B. 无缓冲的channel和有缓冲的channel都是同步的
> C. 无缓冲的channel和有缓冲的channel都是非同步的
> <font color=blue>D. 无缓冲的channel是同步的，而有缓冲的channel是非同步的</font>

答案：D

##### 41.【中级】关于异常的触发，下面说法正确的是（）

> <font color=blue>A. 空指针解析</font>
> <font color=blue>B. 下标越界</font>
> <font color=blue>C. 除数为0</font>
> <font color=blue>D. 调用panic函数</font>

答案：ABCD  

##### 42.【中级】关于cap函数的适用类型，下面说法正确的是（）

```go
A. array
B. slice
C. map
D. channel
```

答案：ABD  

##### 43.【中级】关于beego框架，下面说法正确的是（）

> A. beego是一个golang实现的轻量级HTTP框架
> B. beego可以通过注释路由、正则路由等多种方式完成url路由注入
> C. 可以使用bee new工具生成空工程，然后使用bee run命令自动热编译
> <font color=red>D. beego框架只提供了对url路由的处理，而对于MVC架构中的数据库部分未提供框架支持</font>

答案：ABC

##### 44.【中级】关于goconvey，下面说法正确的是（）

> A. goconvey是一个支持golang的单元测试框架
> B. goconvey能够自动监控文件修改并启动测试，并可以将测试结果实时输出到web界面
> C. goconvey提供了丰富的断言简化测试用例的编写
> <font color=red>D. goconvey无法与go test集成</font>

答案：ABC

##### 45.【中级】关于go vet，下面说法正确的是（）

> A. go vet是golang自带工具go tool vet的封装
> <font color=red>B. 当执行go vet database时，可以对database所在目录下的所有子文件夹进行递归检测</font>
> C. go vet可以使用绝对路径、相对路径或相对GOPATH的路径指定待检测的包
> D. go vet可以检测出死代码

答案：ACD

##### 46.【中级】关于map，下面说法正确的是（）

> <font color=blue>A. map反序列化时json.unmarshal的入参必须为map的地址</font>
> B. 在函数调用中传递map，则子函数中对map元素的增加不会导致父函数中map的修改
> C. 在函数调用中传递map，则子函数中对map元素的修改不会导致父函数中map的修改
> D. 不能使用内置函数delete删除map的元素

答案：A

##### 47.【中级】关于GoStub，下面说法正确的是（）

> A. GoStub可以对全局变量打桩
> B. GoStub可以对函数打桩
> <font color=red>C. GoStub可以对类的成员方法打桩</font>
> D. GoStub可以打动态桩，比如对一个函数打桩后，多次调用该函数会有不同的行为

答案：ABD  

##### 48.【初级】关于select机制，下面说法正确的是（）

> A. select机制用来处理异步IO问题
> B. select机制最大的一条限制就是每个case语句里必须是一个IO操作
> C. golang在语言级别支持select关键字
> <font color=red>D. select关键字的用法与switch语句非常类似，后面要带判断条件</font>

答案：ABC

##### 49.【初级】关于内存泄露，下面说法正确的是（）

> <font color=blue>A. golang有自动垃圾回收，不存在内存泄露</font>
> <font color=red>B. golang中检测内存泄露主要依靠的是pprof包</font>
> <font color=blue>C. 内存泄露可以在编译阶段发现</font>
> <font color=red>D. 应定期使用浏览器来查看系统的实时内存信息，及时发现内存泄露问题</font>

答案：BD

