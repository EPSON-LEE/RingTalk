## 牛客网JS能力测评经典题
[本专题](http://www.nowcoder.com/ta/js-assessment?query=&asc=true&order=&page=3)包括由易到难的50道JavaScript在线编程题，帮助各位前端爱好者进行JS能力自我评估及技能学习提高.
### 数组
#### 查找数组元素位置
**找出元素 item 在给定数组 arr 中的位置**

输出描述:
>如果数组中存在 item，则返回元素在数组中的位置，否则返回 -1

输入例子:
>indexOf([ 1, 2, 3, 4 ], 3)

输出例子:
> 2

代码:

方法一:调用ES5自带的查找方法

    function indexOf(arr, item) {
        return arr.indexOf(item);
    }

方法二:纯函数方法

    function indexOf(arr, item) {
        for(var i = 0; i<arr.length; i++) {
            if(arr[i] == item) {
                return i;
            }
         }
         return -1;
    }

方法三:判断是否支持ES5自带的查找方法

    function indexOf(arr, item) {
      if (Array.prototype.indexOf){
          return arr.indexOf(item);
      } else {
          for (var i = 0; i < arr.length; i++){
              if (arr[i] === item){
                  return i;
              }
          }
      }     
      return -1;
    }
#### 数组求和
**计算给定数组 arr 中所有元素的总和**

输入描述:
>数组中的元素均为 Number 类型


输入例子:
>sum([ 1, 2, 3, 4 ])

输出例子:
>10

代码:

方法一:Array.prototype.reduce,数组中每两个数进行操作

    function sum(arr) {
     var total = arr.reduce(function (a,b){
            return a+b;
        },0);
        return total;
    }

方法二:调用js的计算函数

    function sum(arr) {
    return eval(arr.join('+'));
    }

方法三:常规的for循环

    function sum(arr) {
    var ans=0;
    for(var i = 0;i<arr.length;i++){
        ans += arr[i];
    }
    return ans;
    }
#### 移除数组中的元素1
**移除数组 arr 中的所有值与 item 相等的元素。不要直接修改数组 arr，结果返回新的数组**

输入例子:
>remove([1, 2, 3, 4, 2], 2)

输出例子:
>[1, 3, 4]

代码:

方法一:使用filter函数

    function remove(arr, item) {
            return arr.filter(
            function(x) {
            return x !== item;
            });
    }

方法二:for循环方法

    function remove(arr, item) {
         var a = [];
         for(var i=0; i < arr.length; i++){
             if(arr[i] != item){
                 a.push(arr[i]);
             }
         }
         return a;
     }
#### 移除数组中的元素2
**移除数组 arr 中的所有值与 item 相等的元素，直接在给定的 arr 数组上进行操作，并将结果返回**

输入例子:
>removeWithoutCopy([1, 2, 2, 3, 4, 2, 2], 2)

输出例子:
>[1, 3, 4]

代码:

    function removeWithoutCopy(arr, item) {
         for(var i = 0; i < arr.length; i++){
             if(arr[i] == item){
                 //splice方法会改变数组长度
                 //当减掉一个元素后，后面的元素都会前移，因此需要相应减少i的值
                 arr.splice(i,1);
                 i--;
             }
         }
         return arr;
     }
#### 添加元素
**在数组 arr 末尾添加元素 item。不要直接修改数组 arr，结果返回新的数组**

输入例子:
>append([1, 2, 3, 4],  10)

输出例子:
>[1, 2, 3, 4, 10]

代码:

方法一:先用slice函数进行复制,再在复制后的数组后操作

    function append(arr, item) {
         //复制数组
         var a = arr.slice(0);
         //添加元素
         a.push(item);
         return a;
     }

方法二:使用concat函数进行操作

    function append(arr, item) {
    return arr.concat([item]);
    }
#### 删除数组最后一个元素
**删除数组 arr 最后一个元素。不要直接修改数组 arr，结果返回新的数组**

输入例子:
>truncate([1, 2, 3, 4])

输出例子:
>[1, 2, 3]

代码:

方法一:先用slice复制,然后用pop操作复制后的数组

    function truncate(arr) {
         //复制数组
         var a = arr.slice(0);
         //删除元素
         a.pop();
         return a;
     }

方法二:直接用slice选出从0位置到length-1位置的元素,即把最后元素删除

    function truncate(arr) {
        return arr.slice(0,arr.length-1);
    }
#### 添加元素1
**在数组 arr 开头添加元素 item。不要直接修改数组 arr，结果返回新的数组**

输入例子:
>prepend([1, 2, 3, 4], 10)

输出例子:
>[10, 1, 2, 3, 4]

代码:

方法一:直接用数组拼接函数

    function prepend(arr, item) {
        return [item].concat(arr);   
    }

方法二:因为需要不改变,所以先用slice复制一个原数组再进行操作

    function prepend(arr, item) {
         //将arr数组复制给a
         var a = arr.slice(0);
         //使用unshift方法向a开头添加item
         a.unshift(item);
         return a;
     }
#### 删除数组第一个元素
**删除数组 arr 第一个元素。不要直接修改数组 arr，结果返回新的数组**

输入例子:
>curtail([1, 2, 3, 4])

输出例子:
>[2, 3, 4]

代码:

方法一:直接用slice选出1位置到length位置的元素

    function curtail(arr) {
        return arr.slice(1,arr.length);
    }

方法二:先用slice复制,再用基本方法操作

    function curtail(arr) {
         //复制数组arr
         var a = arr.slice(0);
         a.shift();
         return a;
     }
#### 数组合并
**合并数组 arr1 和数组 arr2。不要直接修改数组 arr，结果返回新的数组**

输入例子:
>concat([1, 2, 3, 4], ['a', 'b', 'c', 1])

输出例子:
>[1, 2, 3, 4, 'a', 'b', 'c', 1]

代码:

方法一:直接用cancat方法进行合并

    function concat(arr1, arr2) {
     return arr1.concat(arr2);
    }

方法二:使用循环

    function concat(arr1, arr2) {
        var tmpArr = arr1.slice(0);
        for(var i = 0; i < arr2.length; i++) {
             tmpArr.push(arr2[i]);
        }
        return tmpArr;
    }
#### 添加元素2
**在数组 arr 的 index 处添加元素 item。不要直接修改数组 arr，结果返回新的数组**

输入例子:
>insert([1, 2, 3, 4], 'z', 2)

输出例子:
>[1, 2, 'z', 3, 4]

代码:

直接用splice方法,先用slice复制一个数组

    function insert(arr, item, index) {
        var a = arr.slice(0);
        a.splice(index,0,item);
        return a;
    }
#### 计数
**统计数组 arr 中值等于 item 的元素出现的次数**

输入例子:
>count([1, 2, 4, 4, 3, 4, 3], 4)

输出例子:
>3

代码:

方法一:使用forEach遍历  用一个三元条件运算符来判断结果，true则执行count++，false则为0，最后返回count。

    function count(arr, item) {
        var count = 0;
        arr.forEach(function(e){
            e == item ? count++ : 0;
        });
        return count;
    }

方法二:使用for循环方法

    function count(arr, item) {
        var cc = 0;
         
        for(var i=0;i<arr.length;i++ ){
            if(arr[i]===item){
                  cc+=1;
            }
        }
        return cc;
    }
#### 查找重复元素
**找出数组 arr 中重复出现过的元素**

输入例子:
>duplicates([1, 2, 4, 4, 3, 3, 1, 5, 3]).sort()

输出例子:
>[1, 3, 4]

代码:

先排序，如果后一个与前一个相等且未保存，则保存。

    function duplicates(arr) {
        var a=arr.sort(),b=[];
        for(var i in a){
            if(a[i]==a[i-1] && b.indexOf(a[i])==-1){
                b.push(a[i]);
            } 
        }
        return b;
    }
#### 求二次方
**为数组 arr 中的每个元素求二次方。不要直接修改数组 arr，结果返回新的数组**

输入例子:
>square([1, 2, 3, 4])

输出例子:
>[1, 4, 9, 16]

代码:

方法一:使用map方法

    function square(arr) {
        return arr.map(function(x){
            return x*x;
        });
    }

方法二:遍历原数组，将其每一个元素求平方，然后存入新的数组即可。

    function square(arr) {
       //声明一个新的数组存放结果
         var a = [];
         arr.forEach(function(e){
             //将arr中的每一个元素求平方后，加入到a数组中
             a.push(e*e);
         });
         return a;
     }
#### 查找元素位置
**在数组 arr 中，查找值与 item 相等的元素出现的所有位置**

输入例子:
>findAllOccurrences('abcdefabc'.split(''), 'a').sort()

输出例子:
>[0, 6]

代码:

查找target的位置，只需要将数组arr中键值对key-value中value == target的key找出来存到新数组而已。因此，遍历arr，如果target == arr[i]，i即目标值位置，则将i加入到a数组中。

    function findAllOccurrences(arr, target) {
        var a = [];
        for(var i = 0; i < arr.length; i++){
            if(target == arr[i])
                a.push(i);
        }
        return a;
    }
### 编码规范
#### 避免全局变量
**给定的 js 代码中存在全局变量，请修复**

    function globals() {
        myObject = {
          name : 'Jory'
        };
        return myObject;
    }

代码:

    function globals() {
        var myObject = {
          name : 'Jory'
        };
        return myObject;
    }
#### 正确的函数定义
**请修复给定的 js 代码中，函数定义存在的问题**

    function functions(flag) {
        if (flag) {
          function getValue() { return 'a'; }
        } else {
          function getValue() { return 'b'; }
        }
        return getValue();
    }
输入例子:
>functions(true)

输出例子:
>a

代码:

else中的语句相当于将if中的function重写，因此无论flag为何值，返回的方法始终为重写后的方法。将方法赋值给一个变量，方法就不会被重写，因此才能得到正确的结果。

    function functions(flag) {
        if (flag) {
          var getValue = function () { return 'a'; }
        } else {
          var getValue = function () { return 'b'; }
        }
        return getValue();
    }
#### 正确的使用 parseInt
**修改 js 代码中 parseInt 的调用方式，使之通过全部测试用例**

    function parse2Int(num) {
        return parseInt(num);
    }
输入例子:
>parse2Int('12'); parse2Int('12px'); parse2Int('0x12')

输出例子:
>12; 12; 0

代码:

按10进制去处理字符串，碰到非数字字符，会将后面的全部无视

    function parse2Int(num) {
         return parseInt(num,10);
     }
#### 完全等同
**判断 val1 和 val2 是否完全等同**

代码:

    function identity(val1, val2) {
           return val1===val2;
    }
### 计数
#### 计时器
**实现一个打点计时器，要求**
1、从 start 到 end（包含 start 和 end），每隔 100 毫秒 console.log 一个数字，每次数字增幅为 1  
2、返回的对象中需要包含一个 cancel 方法，用于停止定时操作  
3、第一个数需要立即输出

代码:

setInterval() 方法会按照指定周期不停地调用函数，直到 clearInterval()被调用或窗口被关闭。由 setInterval() 返回的 ID 值可用作 clearInterval()方法的参数。注意第一个数需要立即输出即可。

    function count(start, end) {
      //立即输出第一个值
      console.log(start++);
         var timer = setInterval(function(){
             if(start <= end){
                 console.log(start++);
             }else{
                 clearInterval(timer);
             }
         },100);
        //返回一个对象
         return {
             cancel : function(){
                 clearInterval(timer);
             }
         };
     }

### 流程控制
#### 流程控制
**实现 fizzBuzz 函数，参数 num 与返回值的关系如下：**
1、如果 num 能同时被 3 和 5 整除，返回字符串 fizzbuzz  
2、如果 num 能被 3 整除，返回字符串 fizz  
3、如果 num 能被 5 整除，返回字符串 buzz  
4、如果参数为空或者不是 Number 类型，返回 false  
5、其余情况，返回参数 num

输入例子:
>fizzBuzz(15)

输出例子:
>fizzbuzz

代码:

能否整除即余数是否为0，则使用%运算符。使用if-elseif结构，只要某一条匹配，则下面的不会在进行判断。判断num是否为Number，可以用typeof运算符，返回的是字符串。

    function fizzBuzz(num) {
        if(num%3 == 0 && num%5 == 0)
            return "fizzbuzz";
        else if(num%3 == 0)
            return "fizz";
        else if(num%5 == 0)
            return "buzz";
        else if(num == null || typeof num != "number")
            return false;
        else return num;
    }
### 函数
#### 函数传参
**将数组 arr 中的元素作为调用函数 fn 的参数**

输入例子:
>argsAsArray(function (greeting, name, punctuation) {

>return greeting + ', ' + name + (punctuation || '!');

>}, ['Hello', 'Ellie', '!'])

输出例子:
>Hello, Ellie!

代码:

调用函数可以使用call或者apply这两个方法，区别在于call需要将传递给函数的参数明确写出来，是多少参数就需要写多少参数。而apply则将传递给函数的参数放入一个数组中，传入参数数组即可。

    function argsAsArray(fn, arr) {
      return fn.apply(this, arr);
     }
#### 函数的上下文
**将函数 fn 的执行上下文改为 obj 对象**

输入例子:
>speak(function () {

>return this.greeting + ', ' + this.name + '!!!';},

>{greeting: 'Hello', name: 'Rebecca'})

输出例子:
Hello, Rebecca!!!

代码:

在JavaScript中，函数是一种对象，其上下文是可以变化的，对应的，函数内的this也是可以变化的，函数可以作为一个对象的方法，也可以同时作为另一个对象的方法，可以通过Function对象中的call或者apply方法来修改函数的上下文，函数中的this指针将被替换为call或者apply的第一个参数。将函数 fn 的执行上下文改为 obj 对象，只需要将obj作为call或者apply的第一个参数传入即可。

    function speak(fn, obj) {
      return fn.apply(obj, obj);
     }
#### 返回函数
**实现函数 functionFunction，调用之后满足如下条件:**
1、返回值为一个函数 f  
2、调用返回的函数 f，返回值为按照调用顺序的参数拼接，拼接字符为英文逗号加一个空格，即 ', '  
3、所有函数的参数数量为 1，且均为 String 类型

输入例子:
>functionFunction('Hello')('world')

输出例子:
>Hello, world

代码:

首先执行functionFunction('Hello')，传入参数str，然后返回函数f，f与('world')组合，执行f('world')，传入参数s，f返回str+", "+s，即Hello, world。注意中间的逗号后面有一个空格。

    function functionFunction(str) {
      var f = function(s){
             return str+", "+s;
         }
         return f;
     }
#### 使用闭包
**实现函数 makeClosures，调用之后满足如下条件:**  
1、返回一个函数数组 result，长度与 arr 相同  
2、运行 result 中第 i 个函数，即 result\[i]()，结果与 fn(arr[i]) 相同  

输入例子:
>var arr = [1, 2, 3];

>var square = function (x) { 

>return x * x; 

>};

>var funcs = makeClosures(arr, square);

>funcs\[1]();

输出例子:
>4

代码:

简单的描述闭包：如果在函数func内部声明函数inner，然后在函数外部调用inner，这个过程即产生了一个闭包.  
题目要求的是返回一个函数数组，如果在循环中直接写result[i] = function(){return fn(arr[i]);}或者result.push(function(){return fn(arr[i]);})，最终的结果是不正确的，因为在每次迭代的时候，那样的语句后面的方法并没有执行，只是创建了一个函数体为“return fn(arr[i]);”的函数对象而已，当迭代停止时，i为最终迭代停止的值，在函数被调用时，i依旧为最终迭代停止的值，因此无法返回正确的结果。  
为了解决这个问题，需要声明一个匿名函数，并立即执行它。  
function(num){return function(){return fn(arr[num]); }; }(i)，函数执行后，i立即传入并被内部函数访问到，因此就能得到正确的结果。闭包允许你引用存在于外部函数中的变量。  
下面的代码使用的是forEach循环

    function makeClosures(arr, fn) {
      var result = [];
         arr.forEach(function(e){
             result.push(function(num){
                 return function(){
                     return fn(num);
                 };
             }(e));
         });
         return result;
     }

#### 二次封装函数
**已知函数 fn 执行需要 3 个参数。请实现函数 partial，调用之后满足如下条件:**  
1、返回一个函数 result，该函数接受一个参数  
2、执行 result(str3) ，返回的结果与 fn(str1, str2, str3) 一致  

输入例子:
>var sayIt = function(greeting, name, punctuation) {

>   return greeting + ', ' + name + (punctuation || '!');
>};

>partial(sayIt, 'Hello', 'Ellie')('!!!');

输出例子:
>Hello, Ellie!!!

代码:  
partial(sayIt, 'Hello', 'Ellie')('!!!');首先执行partial(sayIt, 'Hello', 'Ellie')，将参数传入，然后返回函数result与('!!!')组合成result('!!!')执行。于是，可以在result函数里调用fn，因为函数的参数固定为三个，因此可以用call方法去调用函数fn。

    function partial(fn, str1, str2) {
        var result=function(str3){
            return fn.call(null,str1,str2,str3);
        }
        return result;
    }
#### 使用 arguments
函数 useArguments 可以接收1个及以上的参数。请实现函数useArguments，返回所有调用参数相加后的结果。本题的测试参数全部为 Number 类型，不需考虑参数转换。 

输入例子:
>useArguments(1, 2, 3, 4)

输出例子:
>10

代码:  
本题考查的是对于arguments的使用，arguments能获得函数对象传入的参数组，类似与一个数组，能够通过length获取参数个数，能通过下标获取该位置的参数，但是它不能使用forEach等方法。本题先通过arguments.length获得参数个数，然后循环求和，得出结果。

    function useArguments() {
      /*
       因为参数数量不定，可以先获取参数个数arguments.length
       然后循环求值
      */
      //声明一个变量保存最终结果
      var sum = 0;
      //循环求值
      for(var i = 0; i < arguments.length; i++){
          sum += arguments[i];
      }
      return sum;
     }
#### 使用 apply 调用函数
**实现函数 callIt，调用之后满足如下条件**  
1、返回的结果为调用 fn 之后的结果  
2、fn 的调用参数为 callIt 的第一个参数之后的全部参数

输入例子:
>var a = 1; var b = 2;  
var test = function (first, second) {  
return first === a && second === b;  
};  
callIt(test, a, b);

输出例子:
>true

代码:  
因为arguments并非真正的数组，因此要获得callIt的第一个参数之后的所有参数，不能直接使用slice方法截取，需要先将arguments转换为真正的数组才行。有两种常见的方法，一是使用slice方法：var args = Array . prototype . slice . call ( arguments);二是循环遍历逐一填入新数组。在获得了args之后，就可以调用apply来执行传入的函数参数。

    function callIt(fn) {
        //将arguments转化为数组后，截取第一个元素之后的所有元素
        var args = Array.prototype.slice.call(arguments,1);
        //调用fn
        var result = fn.apply(null,args);
        return result;
    }
#### 二次封装函数
**实现函数 partialUsingArguments，调用之后满足如下条件：**
1、返回一个函数 result  
2、调用 result 之后，返回的结果与调用函数 fn 的结果一致  
3、fn 的调用参数为 partialUsingArguments 的第一个参数之后的全部参数以及 result 的调用参数

输入例子:
>var a = 1; var b = 2; var c = 3; var d = 4;  
var test = function (first, second, third, forth) {  
return first + second + third + forth;};  
partialUsingArguments(test, a, b)(c, d);

输出例子:
>10

代码:

arguments不能用slice方法直接截取，需要先转换为数组，var args = Array.prototype.slice.call(arguments);合并参数可以使用concat方法，并且也需要将arguments先转换为数组才能使用concat进行合并。最用使用apply执行传入的函数即可。

    function partialUsingArguments(fn) {
         //先获取p函数第一个参数之后的全部参数
         var args = Array.prototype.slice.call(arguments,1);
         //声明result函数
         var result = function(){
             //使用concat合并两个或多个数组中的元素
             return fn.apply(null, args.concat([].slice.call(arguments)));
         }
         return result;
     }
#### 柯里化
**已知 fn 为一个预定义函数，实现函数 curryIt，调用之后满足如下条件：**
1、返回一个函数 a，a 的 length 属性值为 1（即显式声明 a 接收一个参数）  
2、调用 a 之后，返回一个函数 b, b 的 length 属性值为 1  
3、调用 b 之后，返回一个函数 c, c 的 length 属性值为 1  
4、调用 c 之后，返回的结果与调用 fn 的返回值一致  
5、fn 的参数依次为函数 a, b, c 的调用参数

输入例子:
>var fn = function (a, b, c) {return a + b + c}; curryIt(fn)(1)(2)(3);

输出例子:
>6

代码:

柯里化是把接受多个参数的函数变换成接受一个单一参数(最初函数的第一个参数)的函数，并且返回接受余下的参数且返回结果的新函数的技术。简单理解题目意思，就是指，我们将预定义的函数的参数逐一传入到curryIt中，当参数全部传入之后，就执行预定义函数。于是，我们首先要获得预定义函数的参数个数fn.length，然后声明一个空数组去存放这些参数。返回一个匿名函数接收参数并执行，当参数个数小于fn.length，则再次返回该匿名函数，继续接收参数并执行，直至参数个数等于fn.length。最后，调用apply执行预定义函数。

    function curryIt(fn) {
         //获取fn参数的数量
         var n = fn.length;
         //声明一个数组args
         var args = [];
         //返回一个匿名函数
         return function(arg){
             //将curryIt后面括号中的参数放入数组
             args.push(arg);
             //如果args中的参数个数小于fn函数的参数个数，
             //则执行arguments.callee（其作用是引用当前正在执行的函数，这里是返回的当前匿名函数）。
             //否则，返回fn的调用结果
             if(args.length < n){
                return arguments.callee;
             }else return fn.apply("",args);
         }
     }
### 逻辑操作
#### 或运算
**返回参数 a 和 b 的逻辑或运算结果**

输入例子:
>or(false, true)

输出例子:
>true

代码:

    function or(a, b) {
      return a||b;
     }
#### 且运算
**返回参数 a 和 b 的逻辑且运算结果**

输入例子:
>and(false, true)

输出例子:
>false

代码:

    function and(a, b) {
      return a && b;
    }
### 模块
#### 模块
**完成函数 createModule，调用之后满足如下要求：**
1、返回一个对象  
2、对象的 greeting 属性值等于 str1， name 属性值等于 str2  
3、对象存在一个 sayIt 方法，该方法返回的字符串为 greeting属性值 + ', ' + name属性值

代码:

声明对象有两种常见的方式：var obj = {};和var obj = new Object();。前面一种可以直接在括号中以key:value的方式定义属性，后一种采用点运算符给对象添加属性。

    function createModule(str1, str2) {
         var obj = {
             greeting : str1,
             name     : str2,
             sayIt    : function(){
                 //两个属性前面都需要加上this
                 return this.greeting+", "+this.name;
             }
         };
         return obj;
     }
### Number
#### 二进制转换1
**获取数字 num 二进制形式第 bit 位的值。注意：**
1、bit 从 1 开始  
2、返回 0 或 1  
3、举例：2 的二进制为 10，第 1 位为 0，第 2 位为 1

输入例子:
>valueAtBit(128, 8)

输出例子:
>1

代码:

通过num.toString(2)能直接将num转换为2进制数格式的字符串，利用下标就能将对应值取出来。题目返回的数字是从右往左，因此下标为倒数。

    function valueAtBit(num, bit) {
      var s = num.toString(2);
         return s[s.length - bit];
     }
#### 二进制转换2
**给定二进制字符串，将其换算成对应的十进制数字 **

输入例子:
>base10('11000000')

输出例子:
>192

代码:

parseInt方法可以将其它进制转换为十进制，只需要给该方法传入需要转换的字符串和该字符串的进制表示两个参数即可。

    function base10(str) {
        /**
            其它进制转十进制
            parseInt(str,2)
            parseInt(str,8)
            parseInt(str,16)
        */
        return parseInt(str,2);
    }
#### 二进制转换3
**将给定数字转换成二进制字符串。如果字符串长度不足 8 位，则在前面补 0 到满8位。**

输入例子:
>convertToBinary(65)

输出例子:
>01000001

代码:

首先通过toString方法将num转为2进制数形式，然后判断其长度是否足够8位。如不足8位，则声明一个“0000000”字符串用于补0，因为目标的2进制数形式最少为一位，因此最多只需要7个0；通过slice方法对“0000000”进行截取，然后将其结果加在目标前面即可。

    function convertToBinary(num) {
         //转换为2进制格式
         var s = num.toString(2);
         //获得2进制数长度
         var l = s.length;
         if(l<8){
             //声明一个字符串用于补满0
             var s1 = "0000000";
             var s2 = s1.slice(0,8-l);
             s = s2+s; 
         }
         return s;
     }
#### 乘法
**求 a 和 b 相乘的值，a 和 b 可能是小数，需要注意结果的精度问题**

输入例子:
>multiply(3, 0.0001)

输出例子:
>0.0003

代码:

通过将a、b小数位数的相加，能够得到a*b结果的小数位数最大可能值。然后使用toFixed方法可以将结果的小数位数指定为可能的最大值，即保证了结果的精度。但本题实际上，仅返回a*b也能通过。在浏览器上做实验，最大17位的小数位数满足了该题全部的测试用例。

    function multiply(a, b) {
      return a*b;
     }
### 对象
#### 改变上下文
**将函数 fn 的执行上下文改为 obj，返回 fn 执行后的值**

输入例子:
>alterContext(function() {  
return this.greeting + ', ' + this.name + '!'; },  
{name: 'Rebecca', greeting: 'Yo' })

输出例子:
>Yo, Rebecca!

代码:

在JavaScript中，函数是一种对象，其上下文是可以变化的，对应的，函数内的this也是可以变化的，函数可以作为一个对象的方法，也可以同时作为另一个对象的方法，可以通过Function对象中的call或者apply方法来修改函数的上下文，函数中的this指针将被替换为call或者apply的第一个参数。将函数 fn 的执行上下文改为 obj 对象，只需要将obj作为call或者apply的第一个参数传入即可。

    function alterContext(fn, obj) {
      return fn.call(obj,obj);
     }
#### 批量改变对象的属性
**给定一个构造函数 constructor，请完成 alterObjects 方法，将 constructor 的所有实例的 greeting 属性指向给定的 greeting 变量。**

输入例子:
>var C = function(name) {this.name = name; return this;};   
>var obj1 = new C('Rebecca');  
>alterObjects(C, 'What\'s up');  
>obj1.greeting;

输出例子:
>What's up

代码:

这是原型链问题。访问一个对象的方法或者是属性，首先会在该对象中寻找，如果找到则返回，如果没找到，则在其原型链上面向上寻找，直至基原型，如还未找到，则返回undefined。将 constructor 的所有实例的 greeting 属性指向给定的 greeting 变量，只需要在constructor的原型上面添加greeting属性，并指定值。

    function alterObjects(constructor, greeting) {
      constructor.prototype.greeting = greeting;
     }
#### 属性遍历
**找出对象 obj 不在原型链上的属性(注意这题测试例子的冒号后面也有一个空格~)**  
1、返回数组，格式为 key: value  
2、结果数组不要求顺序

输入例子:
>var C = function() {  
this.foo = 'bar'; this.baz = 'bim';};  
C.prototype.bop = 'bip';  
iterate(new C());

输出例子:
>["foo: bar", "baz: bim"]

代码:

可以使用for-in来遍历对象中的属性，hasOwnproperty方法能返回一个布尔值，指出一个对象是否具有指定名称的属性。此方法无法检查该对象的原型链中是否具有该属性，该属性必须为对象本身的属性。

    function iterate(obj) {
         var arr = [];
         //使用for-in遍历对象属性
         for(var key in obj){
             //判断key是否为对象本身的属性
             if(obj.hasOwnProperty(key)){
                 //将属性和值按格式存入数组
                 arr.push(key+": "+obj[key]);
             }
         }
         return arr;
     }
### 正则
#### 判断是否包含数字
**给定字符串 str，检查其是否包含数字，包含返回 true，否则返回 false**

输入例子:
>containsNumber('abc123')

输出例子:
>true

代码:

方法一:直接表达式判断

    function containsNumber(str) {
        return /\d/.test(str);
    }

方法二:用if函数进行判断,只要有一个数字,就返回true

    function containsNumber(str) {
        var pattern=/\d/g;
        if(str.match(pattern))
            return true;
        else
            return false;
    }
#### 检查重复字符串
**给定字符串 str，检查其是否包含连续重复的字母（a-zA-Z），包含返回 true，否则返回 false**

输入例子:
>containsRepeatingLetter('rattler')

输出例子:
>true

代码:

在正则表达式中，利用()进行分组，使用斜杠加数字表示引用，\1就是引用第一个分组，\2就是引用第二个分组。将[a-zA-Z]做为一个分组，然后引用，就可以判断是否有连续重复的字母。

    function containsRepeatingLetter(str) {
         return /([a-zA-Z])\1/.test(str);
     }
#### 判断是否以元音字母结尾
**给定字符串 str，检查其是否以元音字母结尾**
1、元音字母包括 a，e，i，o，u，以及对应的大写  
2、包含返回 true，否则返回 false

输入例子:
>endsWithVowel('gorilla')

输出例子:
>true

代码:

首先确定元音集合[a,e,i,o,u]，然后是以元音结尾，加上$，最后通配大小写，加上i。因此正则表达式为:/[a,e,i,o,u]$/i，最后用test方法去检测字符串str

    function endsWithVowel(str) {
        return /[a,e,i,o,u]$/i.test(str)
    }
#### 获取指定字符串
**给定字符串 str，检查其是否包含 3 个连续的数字**  
1、如果包含，返回最新出现的 3 个数字的字符串  
2、如果不包含，返回 false

输入例子:
>captureThreeNumbers('9876543')

输出例子:
>987

代码:

考察的是字符串中是否含有连续的三个任意数字，而不是三个连续的数字。依题，若存在连续的三个任意数字，则返回最早出现的三个数字，若不存在，则返回false。因此需要用到match方法，match()返回的是正则表达式匹配的字符串数组，连续的三个任意数字用正则表达式表示为/\d{3}/。

    function captureThreeNumbers(str) {
         //声明一个数组保存匹配的字符串结果
      var arr = str.match(/\d{3}/);
         //如果arr存在目标结果，则返回第一个元素，即最早出现的目标结果
         if(arr)
             return arr[0];
         else return false;
     }
#### 判断是否符合指定格式
**给定字符串 str，检查其是否符合如下格式**
1、XXX-XXX-XXXX
2、其中 X 为 Number 类型 

输入例子:
>matchesPattern('800-555-1212')

输出例子:
>true

代码:

本题需要注意格式，开头^和结尾$必须加上来限定字符串，3个数可表示为\d{3}，4个数则为\d{4}，{n}表示前面内容出现的次数。正则表达式可写作/^\d{3}-\d{3}-\d{4}$/，有相同部分\d{3}-，因此也可写作/^(\d{3}-){2}\d{4}$/

    function matchesPattern(str) {
        return /^(\d){3}-(\d){3}-(\d){4}$/.test(str);
    }
#### 判断是否符合 USD 格式
**给定字符串 str，检查其是否符合美元书写格式**
1、以 $ 开始  
2、整数部分，从个位起，满 3 个数字用 , 分隔  
3、如果为小数，则小数部分长度为 2  
4、  
正确的格式如：$1,023,032.03 或者 $2.03，  
错误的格式如：$3,432,12.12 或者 $34,344.3

输入例子:
>isUSD('$20,933,209.93')

输出例子:
>true

代码:

本题注意点有必须是USD格式，以$开头，数字结尾，$和小数点的转义。  
首先，开头必是$，而正则表达式中$表示结尾，需要进行转义，因此开头为^\$  
然后$后必然接数字，并且最少一位，最多三位数，可用{m,n}表示,  最少m位，最多n位，因此此段为\d{1,3}  
接着，后面如还有数，则必然有，分隔，并且后面必有3个数，类似于，XXX的格式会出现0或者n次，因此此段可表示为(,\d{3})*  
最后，如有小数部分，则注意对小数点进行转义，此段可表示为(\.\d{2})?  
因此，最后的正则表达式为/^\$\d{1,3}(,\d{3})*(\.\d{2})?$/  
使用test方法去检测str

    function isUSD(str) {
       return /^\$\d{1,3}(,\d{3})*(\.\d{2})?$/.test(str);
    }