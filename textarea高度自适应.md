```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .box{
            width: 200px;
            font-size: 18px;
        }
        .text{
            min-height: 54px;
            height: 54px;
            display: block;
            resize: vertical;
            padding: 5px 15px;
            line-height: 1.5;
            box-sizing: border-box;
            width: 100%;
            font-size: inherit;
            color: #606266;
            background-color: #fff;
            background-image: none;
            border: 1px solid #dcdfe6;
            border-radius: 4px;
            transition: border-color .2s cubic-bezier(.645,.045,.355,1);
        }
    </style>
</head>
<body>
    <div class="box">
        <textarea id="myTextarea" class="text"></textarea>
    </div>
    <script>
        let text = document.getElementById('myTextarea');
        text.addEventListener('input',function(e){
            const scrollHeight = text.scrollHeight
            const style = getComputedStyle(text)
            const borderTop = parseInt(style.borderTopWidth)
            const borderBottom = parseInt(style.borderBottomWidth)
            const height = scrollHeight + borderTop + borderBottom;
            text.style.height = height + 'px';
        })
    </script>
</body>
</html>
```