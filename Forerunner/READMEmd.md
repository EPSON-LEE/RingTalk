## 先行者计划
每天完成一份JS作业，坚持30天，看看什么效果...

4-18
---
用JS写一个可以鼠标拖动的DIV,这个也很简单的,思路就是获取鼠标XY坐标,将之赋予DIV要有鼠标按下和松开的事件.

    <!DOCTYPE html>
    <html>
    <head lang="en">
        <meta charset="UTF-8">
        <title></title>
        <style>
            div{
                position: absolute;
                width: 100px;
                height: 100px;
                background-color:red;
                left: 0;
                top: 0;
            }
        </style>
    </head>
    <body>
    <div id="box">
    </div>
    <script>
       function addHandler(ele,type,handler){
            if(ele.addEventListener){
                ele.addEventListener(type,handler,false);
            }else if(ele.attachEvent){
                ele.attachEvent("on"+type,handler);
            }else{
                ele["on"+type]=handler;
            }
        }
       var pX=0,pY=0;
       var width=50;
       var isMoving=false;
       var box=document.getElementById('box');
       addHandler(document,'mousedown',function(e){
           isMoving=true;
       })
       addHandler(document,'mousemove',function(e){
           if(isMoving){
               e=e||window.event;
               pX=e.clientX;
               pY=e.clientY;
               box.style.left=pX-width+"px";
               box.style.top=pY-width+"px";
           }

       })
       addHandler(document,'mouseup',function(){
           isMoving=false;
       })
    </script>
    </body>
    </html>

