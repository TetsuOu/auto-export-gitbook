# 使用方法 

## 申请Personal access token

登录github，点击 `头像 -> Settings -> Developer settings -> Personal access tokens -> Generate new token`。范围选择`repo`，点击生成`token`。

![image-20201123203638793](https://gitee.com/wangzhebufangqi/PictureBed/raw/master/image-20201123203638793.png)

> Make sure to copy your new personal access token now. You won’t be able to see it again!

请保存好这个值。

## 将token保存至仓库中的Secrets

进入仓库，点击`Settings -> Secrets -> New repository secret`。将上一步得到的值保存为`TOKEN`，点击`Add secret`。以便Github Actions能利用这个值，使得其有权限向你的仓库push。(同一个token可以保存在多个仓库)

![image-20201123204745882](https://gitee.com/wangzhebufangqi/PictureBed/raw/master/image-20201123204745882.png)

## 本地文件向仓库的main分支进行新的push

### 确认已有文件`.github\workflows\auto-generate-gitbook.yml`

❗请按提示修改下述文件中的邮箱

此文件为Github Actions执行的脚本，请确认其所在的目录为`.github\workflows`。

**若无其他需求，可只修改邮箱。**

```yml
name: auto-generate-gitbook
on:                                 #在main分支上进行push时触发  
  push:
    branches:
    - main

jobs:
  main-to-gh-pages:
    runs-on: ubuntu-latest
        
    steps:                          
    - name: checkout main
      uses: actions/checkout@v2
      with:
        ref: main
            
    - name: install nodejs
      uses: actions/setup-node@v1
      
    - name: configue gitbook
      run: |
        npm install -g gitbook-cli          
        gitbook install
        npm install -g gitbook-summary
                
    - name: generate _book folder
      run: |
        book sm
        gitbook build
        cp SUMMARY.md _book
                
    - name: push _book to branch gh-pages 
      env:
        TOKEN: ${{ secrets.TOKEN }}
        REF: github.com/${{github.repository}}
        MYEMAIL: 1823636309@qq.com                  # ！！记得修改为自己邮箱
        MYNAME: ${{github.repository_owner}}          
      run: |
        cd _book
        git config --global user.email "${MYEMAIL}"
        git config --global user.name "${MYNAME}"
        git init
        git remote add origin https://${REF}
        git add . 
        git commit -m "Updated By Github Actions With Build ${{github.run_number}} of ${{github.workflow}} For Github Pages"
        git branch -M main
        git push --force --quiet "https://${TOKEN}@${REF}" main:gh-pages
```

### 确认文件`book.json`

此文件为生成的gitbook的配置信息。

以下信息无需修改。

可参考[.\Part II](https://wangzhebufangqi.github.io/auto-export-gitbook/PART%20II/)以及[.\Part III\UpdateLog](https://wangzhebufangqi.github.io/auto-export-gitbook/PART%20III/UpdateLog.html)

```json
{
	"title": "Summary",
    "links": {
        "sidebar": {
            "Home": "https://wangzhebufangqi.github.io"
        }
    },
	"plugins" : [
		"expandable-chapters",
		"copy-code-button",
		"page-footer-ex",
		"anchor-navigation-ex",
		"expandable-chapters-small",
		"prism", 
		"-highlight",
		"-lunr", 
		"-search", 
		"search-pro",
		"splitter"
	],
	"pluginsConfig": {	
		"page-footer-ex": {
            "copyright": "使用[知识共享 署名-相同方式共享 4.0协议](https://creativecommons.org/licenses/by-sa/4.0/)发布",
            "markdown": true,
            "update_label": "<i>updated</i>",
            "update_format": "YYYY-MM-DD HH:mm:ss"
		},	
		"prism": {
			"css": ["prismjs/themes/prism-solarizedlight.css"],
			"lang": {"flow": "typescript"}
		}
	},
	"ignores" : ["_book", "node_modules"]
}
```

### 确认目录结构等符合规范

请参考[.\Part III\Attention](https://wangzhebufangqi.github.io/auto-export-gitbook/PART%20III/Attention.html)

### 进行push

第一次提交时，请确认默认分支为`main`。否则需要修改.yml文件。

```bash
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/wangzhebufangqi/auto-export-gitbook.git
git push -u origin main
```

以后的提交保证在main分支上更新即可

```bash
git add .
git commit -m "update"
git push
```

# 结果

请确认按上述流程操作而无错漏之处。

假设输入为：

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

push后等待两分钟左右，即可在网址`<username>.github.io/<repository>`查看生成的gitbook。

这里的示例是https://wangzhebufangqi.github.io/auto-export-gitbook/

![image-20201123213004208](https://gitee.com/wangzhebufangqi/PictureBed/raw/master/image-20201123213004208.png)

# 更多信息

