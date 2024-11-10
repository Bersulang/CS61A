**这是一个关于Markdown语法的test文档，使用Markdown语法编写**

# 标题：

# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
#中间不带空格那这就是个标签而不是标题

# 段落：

段落的前后要有空行，所谓的空行是指没有文字内容。若想在段内强制换行的方式是使用两个以上空格加上回车（引用中换行省略回车）。

例如：这仅仅  
只是一个测试（上一部分结尾一定要有两个以上的空格）

# 文本

*hello*——斜体文本（换成下划线_也可以）

**hello**——粗体文本

***hello***——粗斜体文本

分割线：他会放大上一行字体
---
***
* * *

~~删除线~~

<u>下划线</u>

脚注：对文章补充说明

例如：这是一个带有脚注的句子(中间需要空一行)[^r]。

[^r]: 这是脚注内容

# 列表：

无序列表（三种符号皆可）：
* 第一项
- 第二项
+ 第三项

有序列表：
1. 第一项
2. 第二项
3. 第三项

嵌套列表（前面加两个或者四个空格）：
- 第一项
  - 元素1
  - 元素2
2. 第二项
   - 元素1
   - 元素2

结果发现无序列表嵌套需要两个空格，有序列表为四个

# 区块：

> 这是一个区块引用
>> 它还可以嵌套
>>> 甚至多层嵌套

区块中使用列表：
> 1. 第一项
> 2. 第二项
> - 第一项
> - 第二项

列表中使用区块：
1. 第一项 缩进（0-3）
> 这是个测试
2. 第二项 缩进（4）
    > 显示效果取决于缩进

# 代码块：

`print`函数，这只是用于单个代码块，`等等`

    def hello_word():
        print("hello world")
    这是一个代码块，只需要在内容前面加上四个空格（一个制表符tab）
否则就会是新的一行

```python
def hello_world():
    print("hello world")

也可以用三个反引号来标注代码块，区别于缩进这种方式会有高亮提醒
```


# Markdown超链接：

[这是我的博客](https://www.lazypigzyh.top/)

或者直接一点：  
<https://www.lazypigzyh.top/>

**高级链接:**

这个链接用 1 作为网址变量 [Google][1]  
这个链接用 runoob 作为网址变量 [Runoob][runoob]  
然后在文档的结尾为变量赋值（网址）

[1]: http://www.google.com/
  [runoob]: http://www.runoob.com/

# 图片：
中括号里的内容当图片未正常加载时显示的内容
![这是一个图片测试 ](https://raw.githubusercontent.com/Bersulang/Photos/refs/heads/main/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20240924123211.jpg?token=GHSAT0AAAAAACX6CM3OPKIWRW6XCC5XCIRMZZOELCQ '可选的图片标题')

这个链接用 1 作为网址变量 [RUNOOB][1].
然后在文档的结尾为变量赋值（网址）

[1]: https://raw.githubusercontent.com/Bersulang/Photos/refs/heads/main/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20240924123211.jpg?token=GHSAT0AAAAAACX6CM3OPKIWRW6XCC5XCIRMZZOELCQ

Markdown 还没有办法指定图片的高度与宽度，如果需要的话，可以使用普通的 <img> 标签。

例如：<img src="https://raw.githubusercontent.com/Bersulang/Photos/refs/heads/main/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20240924123211.jpg?token=GHSAT0AAAAAACX6CM3OPKIWRW6XCC5XCIRMZZOELCQ" width="50%">

# Markdown表格

Markdown 制作表格使用 | 来分隔不同的单元格，使用 - 来分隔表头和其他行。

| 表头1 | 表头2 |
| ---- | ---- |
| 内容1 | 内容2 |
| 内容3 | 内容4 |

| 左对齐 | 右对齐 | 居中对齐 |
| ----: | :---- | :----: |
| 单元格 | 单元格 | 单元格 |
| 单元格 | 单元格 | 单元格 |
