```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <textarea name="" id="text" cols="30" rows="10"></textarea>
    <button  onclick="downloadFile('text')">下载文本</button>
    <button onclick="downloadFile('json')">下载JSON</button>
    <button onclick="downloadWord()">下载Word</button>
</body>
<script>
    function downloadFile(type){
        let value = document.querySelector('#text').value;
        if(type === 'text'){
            downloadByContent(value,'hello.text','text/plain');
        }else{
            downloadByContent(value,'hello.json','application/json');
        }
    }
    function downloadWord(){
        const template = '<html xmlns:o="urn:schemas-microsoft-com:office:office" '
            +'xmlns:x="urn:schemas-microsoft-com:office:word" '
            +'xmlns="http://www.w3.org/TR/REC-html40">'
            +'<head>'
            +'</head>'
            +'<body>{table}<\/body>'
            +'<\/html>';
        const context = template.replace('{table}', document.querySelector('#text').value);
        downloadByContent(context, 'hello.doc', 'application/msword');
    }
    function downloadByContent(content, filename, type) {
        // const aTag = document.createElementNS('http://www.w3.org/1999/xhtml', 'a');
        const aTag = document.createElement('a');
        aTag.download = filename;
        const blob = new Blob([content],{type});
        const blobUrl = URL.createObjectURL(blob);
        aTag.href = blobUrl;
        // 用 dispatchEvent 触发 a 的 click 事件
        // aTag.dispatchEvent(new MouseEvent('click'))        
        aTag.click();
        URL.revokeObjectURL(blob);
    }
</script>
</html>
```