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
#### 正确的函数定义
#### 正确的使用 parseInt
#### 完全等同
### 计数
#### 计时器
### 流程控制
#### 流程控制
### 函数
#### 函数传参
#### 函数的上下文
#### 返回函数
#### 使用闭包
#### 二次封装函数
#### 使用 arguments
#### 使用 apply 调用函数
#### 二次封装函数
#### 柯里化
### 逻辑操作
#### 或运算
#### 且运算
### 模块
#### 模块
### Number
#### 二进制转换1
#### 二进制转换2
#### 二进制转换3
#### 乘法
### 对象
#### 改变上下文
#### 批量改变对象的属性
#### 属性遍历
### 正则
#### 判断是否包含数字
#### 检查重复字符串
#### 判断是否以元音字母结尾
#### 获取指定字符串
#### 判断是否符合指定格式
#### 判断是否符合 USD 格式