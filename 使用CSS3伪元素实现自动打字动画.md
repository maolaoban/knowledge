```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .tagline,.tagline-skill{
            height:80px;
            width: 200px;
        }
        .tagline{
            font-family: "Fira Mono",monospace;
            overflow: hidden;
            background-color: #2a2a28;
            color: #fff;
            padding-left: 10px;
            text-transform: uppercase;
        }
        .tagline-skill{
            position: relative;
            font-size: 1.5em;
            padding-top: .75em;
            line-height: 80px;
        }
        .tagline-skill_inner{
            display: inline-block;
            position: relative;
        } 
        .tagline-skill_inner:after{
            content: "";
            position: absolute;
            top:25px;
            right: 0;
            bottom: 25px;
            left: 0;
            border-left: 1px solid #fff;
            background-color: #2a2a28;
            -webkit-animation: animatetoright 1s steps(10) infinite alternate;
            animation: animatetoright 1s steps(10) infinite alternate;
        }
        @-webkit-keyframes animatetoright {
            0% {
                left: 0;
                margin-right: auto;
            }
            100% {
                left: 100%;
                margin-left: .6em;
                margin-right: -.6em;
            }
        }

        @keyframes animatetoright {
            0% {
                left: 0;
                margin-right: auto;
            }
            100% {
                left: 100%;
                margin-left: .6em;
                margin-right: -.6em;
            }
        }
    </style>
</head>
<body>
    <div>
        <h1>自动打字</h1>
        <p class="tagline">
            <span class="tagline-skill">
                <span class="tagline-skill_inner">
                    Hello World!
                </span>
            </span>
        </p>
    </div>
</body>
</html>
```