# Plugins I

## [Expandable-chapters-small](https://github.com/chrisjake/gitbook-plugin-expandable-chapters-small)

折叠目录

```json
{    
    "plugins": ["expandable-chapters-small"] 
}
```

## [github-buttons](https://github.com/azu/gitbook-plugin-github-buttons)

提供非官方的github按钮（star, fork, sponsor, and follow ）

```json
{
  "plugins": [
    "github-buttons"
  ],
  "pluginsConfig": {
    "github-buttons": {
      "buttons": [{
        "user": "azu",
        "repo": "JavaScript-Plugin-Architecture",
        "type": "star",
        "size": "large"
      }, {
        "user": "azu",
        "type": "follow",
        "width": "230",
        "count": false
      }]
    }
  }
}
```

| Option  |                         Description                          |        备注        |
| :-----: | :----------------------------------------------------------: | :----------------: |
| `user`  |    GitHub username that owns the repo/Username to sponsor    |    必须，用户名    |
| `repo`  |   GitHub repository to pull the forks and watchers counts    |    必须，仓库名    |
| `type`  | Type of button to show: `watch`, `fork`, `sponsor`, or `follow` | 必须，4种类型之一  |
| `count` | Show the optional watchers or forks count: *none* by default or `true` | 可选，是否显示计数 |
| `size`  | Optional flag for using a larger button: *none* by default or `large` |   可选，按钮大小   |

## [editlink](https://github.com/zhaoda/gitbook-plugin-editlink)

页面顶部编辑本页

```json
{
  "plugins": ["editlink"],
  "pluginsConfig": {
    "editlink": {
      "base": "https://github.com/zhaoda/webpack-handbook/edit/master/content",
      "label": "Edit This Page",
      "multilingual": false
    }
  }
}
```

## [copy-code-button](https://github.com/WebEngage/gitbook-plugin-copy-code-button)

复制代码按钮

```json
{
    "plugins": ["copy-code-button"]
}
```

## [page-footer-ex](https://github.com/zq99299/gitbook-plugin-page-footer-ex)

定制页脚

```json
{
    "plugins": [
        "page-footer-ex"
    ],
    "pluginsConfig": {
        "page-footer-ex": {
            "copyright": "[mrcode](https://github.com/zq99299)",
            "markdown": true,
            "update_label": "<i>updated</i>",
            "update_format": "YYYY-MM-DD HH:mm:ss"
        }
    }
}
```

## [anchor-navigation-ex](https://github.com/zq99299/gitbook-plugin-anchor-navigation-ex)

锚点导航-ex

```json
{
  "plugins": [
       "anchor-navigation-ex"
  ]
}
```

## [Expandable-chapters-small](https://github.com/chrisjake/gitbook-plugin-expandable-chapters-small)

折叠目录

```json
{    
    "plugins": ["expandable-chapters-small"] 
}
```

## [prism](https://github.com/gaearon/gitbook-plugin-prism)

基于Prism的代码高亮

```json
{
  "plugins": ["prism", "-highlight"]
}
```

## [search-pro](https://www.npmjs.com/package/gitbook-plugin-search-pro)

中文搜索

```json
{
    "plugins": [
      "-lunr", "-search", "search-pro"
    ]
}
```

## [donate](https://github.com/willin/gitbook-plugin-donate)

捐赠打赏

```json
{
    "plugins": ["donate"],
    "pluginsConfig": {
        "donate": {
          "wechat": "例：/images/qr.png",
          "alipay": "http://blog.willin.wang/static/images/qr.png",
          "title": "默认空",
          "button": "默认值：Donate",
          "alipayText": "默认值：支付宝捐赠",
          "wechatText": "默认值：微信捐赠"
        }
    }
}
```

## [splitter](https://github.com/yoshidax/gitbook-plugin-splitter)

左侧拖拽栏

```json
{
    "plugins": ["splitter"]
}
```

## [gitbook-plugin-advanced-emoji](https://github.com/codeclou/gitbook-plugin-advanced-emoji)

支持显示markdown文件中的emoji

`:artificial_satellite:`  =>   :artificial_satellite:

```json
{
    "plugins" : ["advanced-emoji"]
}
```

## [gitbook-plugin-katex-ng](https://github.com/vowstar/gitbook-plugin-katex-ng)

支持显示latex公式

`$\int_{-\infty}^\infty g(x) dx$` => $\int_{-\infty}^\infty g(x) dx$

```
$$
\int_{-\infty}^\infty g(x) dx
$$
```
=>
$$
\int_{-\infty}^\infty g(x) dx
$$

```json
{
  "plugins": ["katex-ng"]
}
```

and so on