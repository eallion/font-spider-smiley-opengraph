## Font Spider 压缩字体文件

- https://github.com/eallion/font-spider-smiley-opengraph

```bash
mkdir font-spider && cd font-spider
# 安装 Font Spider
npm install font-spider -g

# 生成 import.html 模板内容
vim import.html

# 从 Summary.json 文件中提取 Title 放入到 index.html 中
cat summary.json | jq -r '.summaries[] | "<h1>\(.title)</h1>"' | sed -e '/<body>/r /dev/stdin' import.html > index.html

# 生成 Title 用到的字体
font-spider index.html --no-backup --debug
```

`SmileySans.ttf` 字体文件放到当前目录，把生成后的字体复制到本项目 `Public` 中。  
`import.html` 内容：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        @font-face {
            font-family: 'SmileySans';
            src: url('SmileySans.ttf') format('truetype');
            font-weight: normal;
            font-style: normal;
        }
        h1,
        p {
            font-family: 'SmileySans',sans-serif;
        }
    </style>
</head>
<body>
</body>
</html>
```
