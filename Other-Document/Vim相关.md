## vim（vi）编辑器：		

shell -- bash		vi —— vim

### 一、三种工作模式：

> 命令模式： 默认进入vim的工作模式。该种模式下，用户所有输入均被当成命令。
> 编辑模式： 编写模式。写代码、文本内容。。。
> 末行模式： 在 命令模式下， 按“:”进入末行模式。该种模式下，用户所有输入均被当成  末行命令。

​	

### 二、光标移动（命令模式）；

> h：左
> j：下
> k：上
> L：右

### 三、转换编辑模式：

> i：向光标所在位置的 “前面”插入数据！
> a：向光标所在位置的 “后面”插入数据！
> o：向光标所在位置的 “下一行”插入数据！
> s：以删除光标位置一个字符为代价，修改工作模式 —— 文本编辑模式。
> O：向光标所在位置的 “上一行”插入数据！
> I：向光标所在位置的 “行首”插入数据！
> A：向光标所在位置的 “行尾”插入数据！
> S：以删除光标位置一整行为代价，修改工作模式 —— 文本编辑模式。

### 四、复制、粘贴：

> yy：复制光标所在行。
Nyy：复制光标所在往后的N行（包含本行）。
p：粘贴至光标所在位置，下一行。
P（大写）：粘贴至光标所在位置，上一行。
yw：将光标放置于单词的首字符上， 复制一个单词。

### 五、区域复制：

<font color=red>将光标放置于待复制区域的首字符上， 按“v”（左下角出现 “可视”提示）使用 h，j，k，l 选择复制区域。</font>

> 剪切、粘贴：hhh
> dd：剪切光标所在行。
> Ndd：剪切光标所在往后的N行（包含本行）。
> p：粘贴至光标所在位置，下一行。
> P（大写）：粘贴至光标所在位置，上一行。
> dw：将光标放置于单词的首字符上， 剪切一个单词。

### 六、区域剪切：

<font color=blue>将光标放置于待剪切区域的首字符上， 按“v”（左下角出现 “可视”提示）使用 h，j，k，l 选择剪切区域。</font>

d0：从光标所在位置，删除到 行首。
d$（D）: 从光标所在位置，删除到 行尾。	

**删除：**
同剪切。
​	

### 七、字符操作：

> x：删除光标选中字符
> r：光标选中字符， 按“r”， 按目标字符。 可以将 原字符，替换为 目标字符。

### 八、跳转到指定行：

命令模式：

> gg：第一行
> G：最后一行
> gg=G  自动排版。
> NG：跳转到 第 N 行
> vim hello.go  + 56 —— 打开文件同时，跳转到 56 行

末行模式：

> ：N 回车。 —— 跳转到 第 N 行	

### 九：查找：

> 1. 想象一个单词查找。 输入“/”（显示在末行的位置）， 再输入要查找的单词。
> 2. 查找一个已经看到的单词。将光标放在该单词任意一个字符，“*”向后找， “#”向前找。 “n”代表下一个。

撤销：“u”

反撤销：ctrl - r

### 十、替换：—— 末行模式。

1. 单行替换： 	:s/旧单词/新单词。 	
   - 一行有多个“旧单词”， 使用 “g”。否则只替换一行的首个。
2. 通篇替换：	:%s/旧单词/新单词。	
   - 一行有多个“旧单词”， 使用 “g”。否则只替换一行的首个。
3. 指定区域替换：	:n，ms/旧单词/新单词。
   - 替换从n行开始，到m行结束，出现的“旧单词”， 一行有多个“旧单词”， 使用 “g”。否则只替换一行的首个。

十一、vim的配置：

- 用户配置： 用户宿主目录下，创建 .vimrc (隐藏文件)，写入 配置项。

- 系统配置：sudo vi  /etc/vim/vimrc （非隐藏文件）。写入 配置项。

> 当前目录下有提供vimrc文件，直接放置到相应目录下就可以了