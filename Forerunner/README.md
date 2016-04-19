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

4-19
---

做一个右键弹出菜单，就是鼠标在网页上点击，弹出的不是window的属性什么的，而是一个右定义的菜单。
同时要把window的属性什么的菜单屏蔽掉。

HTML部分

    <h3>右键单击下面的区域，自定义右键菜单</h3>
    <div id="box"></div>
    <ul id="menu">
      <li>右键选项一</li>
      <li>右键选择二</li>
      <li>右键选项三</li>
      <li>右键选项四</li>
    </ul>

CSS部分

    html,body,div,ul,li{
          margin: 0;
          padding: 0;
    }
    h3{
          text-align: center;
    }
    div#box{
          width: 200px;
          height: 200px;
          border: 1px solid black;
          margin: 20px auto;
    }
    /*将ul标签隐藏起来*/
     #menu{
          border: 1px solid #ddd;
          display: inline-block;
          display: none;
          position: absolute;
    }
     #menu li{
          list-style-type: none;
          padding: 5px 10px;
          font: 14px "微软雅黑";
    }
     /*添加鼠标移动到li标签上的时候的效果*/
     #menu li:hover{
          background: #4545ff;
    }

JS部分

    var box = document.getElementById("box"),
        menu = document.getElementById("menu");
        
    function showMenu(event){
        // 阻止默认行为
        event.preventDefault();
        // 定位菜单位置
        menu.style.left = event.pageX + "px";
        menu.style.top = event.pageY + "px";
        // 设置菜单可见
        menu.style.display = 'inline-block';
    }
    function hideMenu(){
            menu.style.display = "none";
    }

    // 事件处理
    box.addEventListener("contextmenu", showMenu, false);
    document.addEventListener("click", hideMenu, false);