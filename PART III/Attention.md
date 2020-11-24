# 规范

## 文件规范

### 每一个文件夹下是否有一个`README.md`文件

首先，并不是每一个文件夹下都需要一个README.md文件。但是**项目根目录下必须存在README.md文件**！（项目根目录下的SUMMARY.md文件不需要，因为我会帮你自动生成）。

其他子目录下是否含README.md文件的区别在于：

如果子目录Part I下含README.md文件，那么在生成的gitbook的目录中，点击PART I，页面将会跳转到对应的README.md上写的内容，同时，如果此目录是折叠起来的并且不是蓝色的话将会展开。

如果子目录Part I下不含README.md文件，那么在生成的gitbook的目录中，点击PART I，页面并不会发生跳转，因为它无法跳转到相应的内容，但是此时如果此目录是折叠起来的将会展开，如果此目录是展开的将会折叠起来。

如果还不清楚，尝试一下！

输入：

```
auto-export-gitbook
│  book.json
│  README.md
│
├─.github
│  └─workflows
│          auto-generate-gitbook.yml
│
├─PART I
│  │  README.md
│  │
│  ├─SubPart I
│  │      Markdown.md
│  │      PicGo.md
│  │      README.md
│  │      Typora.md
│  │
│  └─SubPart II
│          Git.md
│          Github.md
│          README.md
│
├─PART II
│      Plugins I.md
│      Plugins II.md
│      README.md
│
└─PART III
        Attention.md
        README.md
        UpdateLog.md
```

对应自动生成的SUMMARY.md：（生成的SUMMARY.md文件顺便也推送到了gh-pages分支）

```markdown
# Summary

- [PART I](PART I/README.md)
  - [Sub Part I](PART I/SubPart I/README.md)
    * [Markdown](PART I/SubPart I/Markdown.md)
    * [Pic Go](PART I/SubPart I/PicGo.md)
    * [Typora](PART I/SubPart I/Typora.md)
  - [Sub Part II](PART I/SubPart II/README.md)
    * [Git](PART I/SubPart II/Git.md)
    * [Github](PART I/SubPart II/Github.md)
- [PART II](PART II/README.md)
  * [Plugins I](PART II/Plugins I.md)
  * [Plugins II](PART II/Plugins II.md)
- [PART III](PART III/README.md)
  * [Attention](PART III/Attention.md)
  * [Update Log](PART III/UpdateLog.md)
```

## 命名规范