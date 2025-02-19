###HTML页面原生的声明周期事件
- **DOMContentLoaded** —— 浏览器已完全加载 HTML，并构建了 DOM 树，但像\<img>和样式表之类的外部资源可能尚未加载完成。可以查找DOM节点，并初始化接口。
  
- **load** —— 浏览器不仅加载完成了 HTML，还加载完成了所有外部资源：图片，样式等。
-  **beforeunload** —— 用户正在离开：我们可以检查用户是否保存了更改，并询问他是否真的要离开。
-  **unload** —— 用户几乎已经离开了，但是我们仍然可以启动一些操作，例如发送统计数据。
***例***

        document.addEventListener("DOMContentLoaded",()=>{

        })


####window.onload
- 当整个页面，包括样式、图片和其它资源被完全加载完成时，会触发window对象上的load事件。

        window.onload = function(){
            alert('page loaded');
        }
####window.onunload
- 当访问者离开页面时，window 对象上的 unload 事件就会被触发。我们可以在那里做一些不涉及延迟的操作，例如关闭相关的弹出窗口。
####window.onbeforeunload
- 如果访问者触发了离开页面的导航（navigation）或试图关闭窗口，beforeunload 处理程序将要求进行更多确认.

####readyState
`document.readyState` 属性可以为我们提供当前加载状态的信息。
它有3个可能值：
- `loading` 文档正在被加载。
- `interactive` 文档被全部读取。
- `complete` 文档被全部读取，并且所有资源（例如图片等）都已加载完成。

我们可以检查 document.readyState 并设置一个处理程序，或在代码准备就绪时立即执行它。

    if(document.readyState == 'loading){
        document.addEventListener('DOMContentLoaded', ()=>{

        });
    }else{

    }
还有一个 readystatechange 事件，会在状态发生改变时触发。

    document.addEventListener('readystatechange',()=>{
        console.log(document.readyState);
    })