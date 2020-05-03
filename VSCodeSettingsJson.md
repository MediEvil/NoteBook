---
note:
    createdAt: 2020-05-03T07:31:45.397Z
    modifiedAt: 2020-05-03T07:35:28.133Z
    tags: []
    id: ""
---
## visual studio settings.json 配置帮助

### editor自身设置

1. 字体大小

```json
"editor.fontSize"
```

2. 80个字符的换行提示线设置

```json
"editor.rulers": [80]
```
editor.rulers是个数组，意味着可以设定多条竖线，可以在80个字符和120个字符的位置都进行提示
```json
"editor.rulers": [80, 120]
```
如果只想针对某些语言设置rulers，可以这么写
```json
"[latex]":{
  "editor.rulers": [80]
}
```

### latex workshop设置

1. pdf阅读器设置
```json
"latex-workshop.view.pdf.viewer": "tab"
```
tab 为vsCode自带浏览器
browser 为网页浏览器
externel 为其他pdf浏览器，需要额外设置（这块暂无）
