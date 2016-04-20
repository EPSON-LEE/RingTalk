## 前端技能挑战

#### 修改 this 指向

题目描述

封装函数 f，使 f 的 this 指向指定的对象  

输入例子:  
>bindThis(function(a, b){return this.test + a + b}, {test: 1})(2, 3)  

输出例子:  
>6

代码:
```js

        方法一:
        function bindThis(func, oTarget) {
            return function(){
                return func.apply(oTarget, arguments);
            };
        }
        方法二:
        function bindThis(f, oTarget) {
        return  f.bind(oTarget);
        }
```

---

#### 获取 url 中的参数

题目描述  
获取 url 中的参数  
1. 指定参数名称，返回该参数的值 或者 空字符串  
2. 不指定参数名称，返回全部的参数对象 或者 {}  
3. 如果存在多个同名参数，则返回数组

输入例子:
>getUrlParam('http://www.nowcoder.com?key=1&key=2&key=3&test=4#hehe', 'key')

输出例子:
>['1', '2', '3']

代码:

```js

    function getUrlParam(sUrl, sKey) {
     // 捕获组两枚,一枚负责Key 一枚负责获取Value
        var reg = new RegExp('([0-9a-zA-Z%]+)=([0-9a-zA-Z%]+)&*', 'ig');
        // 结果集保存
        var result = {};
        var temp;
        var key, value;
      
        while(temp = reg.exec(sUrl)) {
            key = temp[1];
            value = temp[2];
      
            if (result[key] && !(result[key] instanceof Array)) {
                result[key] = [result[key], value];     // 如果发现了第二个同名参数,则从字符串变为数组
            } else if (result[key] instanceof Array) {
                result[key].push(value);    // 已经是数组,又找到了,就push进去
            } else {
                result[key] = value;    // 第一次,还是普通保存
            }
        }
      
        if (sKey) {
            return result[sKey] ? result[sKey] : '';    // 为了避免undefined的情况
        } else {
            return result;  // 返回全部的对象参数
        }   
    }
```

---

#### dom 节点查找

题目描述  
查找两个节点的最近的一个共同父节点，可以包括节点自身 

输入描述:
>oNode1 和 oNode2 在同一文档中，且不会为相同的节点

代码:

```js

    function commonParentNode(oNode1, oNode2){
        if (oNode1.contains(oNode2))
            {
                return oNode1;
            }
        else if (oNode2.contains(oNode1))
            {
                return oNode2;
            }
        else{
            return arguments.callee(oNode1.parentNode,oNode2);
        }
    }
```

---
#### 根据包名，在指定空间中创建对象

题目描述  
根据包名，在指定空间中创建对象

输入描述:
>namespace({a: {test: 1, b: 2}}, 'a.b.c.d')

输出描述:
>{a: {test: 1, b: {c: {d: {}}}}}

代码:

```js

    function namespace(oNamespace, sPackage) {
        var pack = sPackage.split('.');
        for(var i=0;i<pack.length;i++){
            if(!oNamespace[pack[i]]){
                oNamespace[pack[i]] ={};
            }
            oNamespace = oNamespace[pack[i]];
        }
    }
```
#### 数组去重

题目描述  
为 Array 对象添加一个去除重复项的方法 

输入例子:
>[false, true, undefined, null, NaN, 0, 1, {}, {}, 'a', 'a', NaN].uniq()

输出例子:
>[false, true, undefined, null, NaN, 0, 1, {}, {}, 'a']

代码:

```js

    Array.prototype.uniq = function () {
       var arr = [];
            var flag = true;
            for(var i=0;i<this.length;i++){
                if(arr.indexOf(this[i])==-1){       //数组中没找到
                    if(this[i]!==this[i]){
                        if(flag){
                            arr.push(this[i]);
                            flag = false;
                        }
                    }else {
                        arr.push(this[i]);
                    }
                }
            }
        return arr;
    }
```

---

#### 斐波那契数列

题目描述  
用 JavaScript 实现斐波那契数列函数,返回第n个斐波那契数。 f(1) = 1, f(2) = 1 等

代码:
```js

    function fibonacci(n){
        if(n==1||n==2)
            return 1;
        return fibonacci(n-1)+fibonacci(n-2);
    }
```

---

#### 时间格式化输出

题目描述  
按所给的时间格式输出指定的时间  
格式说明  
对于 2014.09.05 13:14:20  
yyyy: 年份，2014  
yy: 年份，14  
MM: 月份，补满两位，09  
M: 月份, 9  
dd: 日期，补满两位，05  
d: 日期, 5  
HH: 24制小时，补满两位，13  
H: 24制小时，13  
hh: 12制小时，补满两位，01  
h: 12制小时，1  
mm: 分钟，补满两位，14  
m: 分钟，14  
ss: 秒，补满两位，20  
s: 秒，20  
w: 星期，为 ['日', '一', '二', '三', '四', '五', '六'] 中的某一个，本 demo 结果为 五  

输入例子:
>formatDate(new Date(1409894060000), 'yyyy-MM-dd HH:mm:ss 星期w')

输出例子:
>2014-09-05 13:14:20 星期五

代码:
```js

    function formatDate(oDate, sFormation) {
        var obj ={
            yyyy:oDate.getFullYear(),
            yy:(''+oDate.getFullYear()).slice(-2),
            MM:('0'+(oDate.getMonth()+1)).slice(-2),
            M:oDate.getMonth()+1,
            dd:('0'+(oDate.getDate())).slice(-2),
            d:oDate.getDate(),
            HH:('0'+(oDate.getHours())).slice(-2),
            H:oDate.getHours(),
            hh:('0'+(oDate.getHours()%12)).slice(-2),
            h:(oDate.getHours()%12),
            mm:('0'+oDate.getMinutes()).slice(-2),
            m:oDate.getMinutes(),
            ss:('0'+oDate.getSeconds()).slice(-2),
            s:oDate.getSeconds(),
            w:['日','一','二','三','四','五','六'][oDate.getDay()]
        };
        return sFormation.replace(/([a-z]+)/ig,function($1){
            return obj[$1];
        });
    }
```

---

#### 获取字符串的长度

题目描述  
如果第二个参数 bUnicode255For1 === true，则所有字符长度为 1  
否则如果字符 Unicode 编码 > 255 则长度为 2  

输入例子:
>strLength('hello world, 牛客', false)

输出例子:
>17

代码:
```js

    function strLength(s, bUnicode255For1) {
        var sLength=0;
        if(bUnicode255For1===true){
            return s.length;
        }else{
            for(var i=0;i<s.length;i++){
                if(s.charCodeAt(i)>255){
                    sLength+=2;
                }else{
                    sLength+=1;
                }
            }
        }
        return sLength;
    }
```

---

#### 邮箱字符串判断

题目描述  
判断输入是否是正确的邮箱格式

输入描述:
>邮箱字符串

输出描述:
>true表示格式正确

代码:
```js

    function isAvailableEmail(sEmail) {
        var pattern = /^\w+(\.)?(\w+)?@\w+\.(com|org)(\.cn)?$/ig;
        return pattern.test(sEmail);
         
    }
```

---

#### 颜色字符串转换

题目描述  
将 rgb 颜色字符串转换为十六进制的形式，如 rgb(255, 255, 255) 转为`#ffffff`  
1. rgb 中每个 , 后面的空格数量不固定  
2. 十六进制表达式使用六位小写字母  
3. 如果输入不符合 rgb 格式，返回原始输入

输入例子:
>rgb2hex('rgb(255, 255, 255)')

输出例子:
>`#ffffff`

代码:
```js

    function rgb2hex(sRGB) {
       return sRGB.replace(/^rgb\((\d+)\s*\,\s*(\d+)\s*\,\s*(\d+)\)$/g, function(a, r, g, b){
           return '#' + hex(r) + hex(g) + hex(b);
       });
    }
    function hex(n){
        return n < 16 ? '0' + (+n).toString(16) : (+n).toString(16);
    }
```

---

#### 将字符串转换为驼峰格式

题目描述  
css 中经常有类似 background-image 这种通过 - 连接的字符，通过 javascript 设置样式的时候需要将这种样式转换成 backgroundImage 驼峰格式，请完成此转换功能  
1. 以 - 为分隔符，将第二个起的非空单词首字母转为大写  
2. -webkit-border-image 转换后的结果为 webkitBorderImage

输入例子:
>cssStyle2DomStyle('font-size')

输出例子:
>fontSize

代码:
```js

    function cssStyle2DomStyle(sName) {
        var style = sName.match(/(\w+)\-/)[1];
        sName.replace(/\-(\w+)/g,function(a,k,p){
            if(p>1){
                style = style + k[0].toUpperCase() + k.substring(1);
            }
        })
        return style;
    }
```

---

#### 字符串字符统计

题目描述  
统计字符串中每个字符的出现频率，返回一个 Object，key 为统计字符，value 为出现频率  
1. 不限制 key 的顺序  
2. 输入的字符串参数不会为空  
3. 忽略空白字符

输入例子:
>count('hello world')

输出例子:
>{h: 1, e: 1, l: 3, o: 2, w: 1, r: 1, d: 1}

代码:
```js

    function count(str) {
        var items=str.replace(/\s+/,'');
        var item=items.split('');
        var result={};
        item.forEach(function(n,i){
            if(!result[n]){
                result[n]=1;
            }else{
                result[n]+=1;
            }
        });
        return result;
    }
```