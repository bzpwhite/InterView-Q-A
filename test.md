## 算法题

### 1
牛牛去犇犇老师家补课，出门的时候面向北方，但是现在他迷路了。虽然他手里有一张地图，但是他需要知道自己面向哪个方向，请你帮帮他。
```bash
var n = readline();//获取转方向的次数
var str = readline();//获取转的方向
var arr = str.split("");
var L = 0;
var R = 0;
var positionR = ['N', 'E', 'S', 'W']
var positionL = ['N', 'W', 'S', 'E']

for (var i = 0; i < n; i++) {
    if (arr[i] == 'L') {
        L++
    } else[
        R++
    ]
}
if (R > L) {
    console.log(positionR[(R - L) % 4])
} else {
    console.log(position[(L - R) % 4])
}
```

### 2

小易有一些彩色的砖块。每种颜色由一个大写字母表示。各个颜色砖块看起来都完全一样。现在有一个给定的字符串s,s中每个字符代表小易的某个砖块的颜色。小易想把他所有的砖块排成一行。如果最多存在一对不同颜色的相邻砖块,那么这行砖块就很漂亮的。请你帮助小易计算有多少种方式将他所有砖块排成漂亮的一行。(如果两种方式所对应的砖块颜色序列是相同的,那么认为这两种方式是一样的。)
例如: s = "ABAB",那么小易有六种排列的结果:
"AABB","ABAB","ABBA","BAAB","BABA","BBAA"
其中只有"AABB"和"BBAA"满足最多只有一对不同颜色的相邻砖块。

```bash
var input = readline();
var arr = input.split('');
var num = []

for (var i=0; i<arr.length; i++) {
    if(!isInArray(num, arr[i])){
    num.push(arr[i])
    }
}
function isInArray(arr,value){
    for(var i = 0; i < arr.length; i++){
        if(value === arr[i]){
            return true;
        }
    }
    return false;
}
switch (num.length) {
    case 1:
        console.log(1)
        break;
    case 2:
        console.log(2);
        break;
    default:
        console.log(0);
        break;
}
```

### 3
如果一个01串任意两个相邻位置的字符都是不一样的,我们就叫这个01串为交错01串。例如: "1","10101","0101010"都是交错01串。
小易现在有一个01串s,小易想找出一个最长的连续子串,并且这个子串是一个交错01串。小易需要你帮帮忙求出最长的这样的子串的长度是多少。 
```bash
var input = readline();
var arr = input.split('');
var length = 1;
var max = [1];

for(var i=0; i<arr.length-1; i++) {
    if(arr[i]==arr[i+1]){
        length = 1;
    } else {
        length++
    }
    if(length!=1) {
        max.push(length);
    }
}

console.log(Math.max.apply(Math,max))
```

### 4

在英文中,我们会把一些长的名字或者短语进行缩写。例如"looks good to me"缩写为"lgtm",短语中的每个单词的首字母组成缩写。现在给出一个字符串s,字符串s中包括一个或者多个单词,单词之间以空格分割,请输出这个字符串的缩写。

```bash
var input = 'looks good to me';
var arr = input.split(" ");
var sim = '';

for (var i = 0; i < arr.length; i++) {
    sim = sim + arr[i].split("")[0];
}

console.log(sim)
```

### 5

给定5个正整数, 它们的最小的众倍数是指的能够被其中至少三个数整除的最小正整数。 给定5个不同的正整数, 请计算输出它们的最小众倍数。

```bash
var input = "1 2 3 4 5";
var arr = input.split(" ");
var arrMin = [];

var a = Number(arr[0]);
var b = Number(arr[1]);
var c = Number(arr[2]);
var d = Number(arr[3]);
var e = Number(arr[4]);

arrMin.push(getSpecialNum(c, d, e).LCM)
arrMin.push(getSpecialNum(b, d, e).LCM)
arrMin.push(getSpecialNum(b, c, e).LCM)
arrMin.push(getSpecialNum(b, c, d).LCM)
arrMin.push(getSpecialNum(a, d, e).LCM)
arrMin.push(getSpecialNum(a, c, e).LCM)
arrMin.push(getSpecialNum(a, c, d).LCM)
arrMin.push(getSpecialNum(a, b, d).LCM)
arrMin.push(getSpecialNum(a, b, e).LCM)
arrMin.push(getSpecialNum(a, b, c).LCM)

console.log(Math.min.apply(Math, arrMin))

function getSpecialNum(num1, num2, num3) {
    var max = num1;
    var min = num1;
    var specilanum = new Object();
    if (num1 < 1 || num2 < 1 || num3 < 1) {
        specilanum.GCM = -1;
        specilanum.LCM = -1;
        return specilanum;
    }
    if (num2 > num1) max = num2;
    if (max < num3) max = num3;
    if (num2 < num1) min = num2;
    if (num3 < min) min = num3;
    for (var i = min; i > 0; i--) {
        if (num1 % i == 0 && num2 % i == 0 && num3 % i == 0) {
            specilanum.GCM = i;
            break;
        }
    }
    for (var i = max; i <= num1 * num2 * num3; i++) {
        if (i % num1 == 0 && i % num2 == 0 && i % num3 == 0) {
            specilanum.LCM = i;
            break;
        }
    }
    return specilanum;
}
```

### 6

一个由小写字母组成的字符串可以看成一些同一字母的最大碎片组成的。例如,"aaabbaaac"是由下面碎片组成的:'aaa','bb','c'。牛牛现在给定一个字符串,请你帮助计算这个字符串的所有碎片的平均长度是多少。

```bash
var input = readline();
var arr = input.split("");
var num = 1;
var lenArr = [];
var average = 0;
var sum = 0;

for (var i = 0; i < arr.length - 1; i++) {
    if (arr[i] == arr[i + 1]) {
        num++
    } else {
        lenArr.push(num)
        num = 1;
    }
}
lenArr.push(num)
for (var j = 0; j < lenArr.length; j++) {
    sum = sum + lenArr[j];
}

console.log((sum / lenArr.length).toFixed(2))
```
### 7

算1-400有多少个1，如1-23有13个1；

```bash
var input = '1 400';
var arr = input.split(' ');
var numOne = 0;

for (var i=Number(arr[0]); i<=Number(arr[1]); i++) {
    var numStr = String(i)
    var numArr = numStr.split("")
    for(var j=0;j<numArr.length;j++) {
        if(numArr[j]=='1') {
            numOne++
        }
    }
}

console.log(numOne)
```

### 8.归并排序

```bash

function merge(left, right) {
    var result = [];

    while (left.length && right.length) {
        if (left[0] < right[0])
            result.push(left.shift());
        else
            result.push(right.shift());
    }
    return result.concat(left, right);
}

function mergeSort(myArray){

    if (myArray.length < 2) {
        return myArray;
    }

    var middle = Math.floor(myArray.length / 2),
        left    = myArray.slice(0, middle),
        right   = myArray.slice(middle),
        params = merge(mergeSort(left), mergeSort(right));
    # 在返回的数组头部，添加两个元素，第一个是0，第二个是返回的数组长度
    params.unshift(0, myArray.length);
    # splice用来替换数组元素，它接受多个参数，
    # 第一个是开始替换的位置，第二个是需要替换的个数，后面就是所有新加入的元素。
    # 因为splice不接受数组作为参数，所以采用apply的写法。
    # 这一句的意思就是原来的myArray数组替换成排序后的myArray
    myArray.splice.apply(myArray, params);
    # 返回排序后的数组
    return myArray;
}

console.log(mergeSort([1, 3, 4, 2, 5, 0, 8, 10, 4]));
```

### 9.快排

```bash
var quickSort = function (arr) {
    //元素个数小于1
    if (arr.length <= 1) {
        return arr;
    }

    var pivotIndex = Math.floor(arr.length / 2);
    var pivot = arr.splice(pivotIndex, 1)[0];

    var left = [];
    var right = [];

    for (var i = 0; i < arr.length; i++) {
        if (arr[i] < pivot) {
            left.push(arr[i]);
        } else {
            right.push(arr[i]);
        }
    }

    console.log('left', left, 'right', right, 'pivot', pivot);

    return quickSort(left).concat([pivot], quickSort(right));
}

test = [85, 24, 63, 45, 17, 31, 96, 50]
console.log(quickSortFilter(test))

function quickSortFilter(a) {
    return a.length <= 1 ? a : quickSortFilter(a.slice(1).filter(item => item <= a[0])).concat(a[0], quickSortFilter(a.slice(1).filter(item => item > a[0])));
}
```

## 百度-字典序

```bash
var input = 'abots';
var array = input.split('');

for (var i = array.length - 1; i > 0; i--) {
    if (array[i] > array[i - 1]) {
        #如果前一项小于本项
        array.splice(i - 1, 1)
        #剔除前一项，确保前面的永远大于后面的
        console.log('arr', array)
    }
}
console.log(array.join(""))
```

## 字符覆盖

小度有一个小写字母组成的字符串s.字符串s已经被写在墙上了.
小度还有很多卡片,每个卡片上有一个小写字母,组成一个字符串t。小度可以选择字符串t中任意一个字符,然后覆盖在字符串s的一个字符之上。小度想知道在选取一些卡片覆盖s的一些字符之后,可以得到的字典序最大的字符串是什么。

```bash
# self
var input1 = 'ittmcsvmoa';
var input2 = 'jktvvblefw';

var arr1 = input1.split("");
var arr2 = input2.split("");

var sortArr = quickSortFilter(arr2);

function quickSortFilter(a) {
    return a.length <= 1 ? a : quickSortFilter(a.slice(1).filter(item => item > a[0])).concat(a[0], quickSortFilter(a.slice(1).filter(item => item <= a[0])));
}

for(var i=0; i<sortArr.length; i++) {
    for(var j=0; j<arr1.length; j++) {
        if(sortArr[i]>arr1[j]) {
            arr1[j]=sortArr[i];
            break;
        }
    }
}

console.log(arr1.join(""));

# nowcoder
var str = 'ittmcsvmoa';
var ss = 'jktvvblefw'; 

var res = dicOrder(str, ss);

console.log(res);

function dicOrder(str, ss) {  
    var arr = ss.split('').sort().reverse();  
    var newStr = '';  
    for (let i = 0, j = 0; i < str.length; i++) {
        if (arr[j] > str[i]) {
            newStr += arr[j];
            j++;
        } else {
            newStr += str[i];
        }  
    }  
    return newStr;
}

```

## promise实现

```bash
(function(window,undefined){

    # resolve 和 reject 最终都会调用该函数
    var final = function(status,value){
        var promise = this, fn, st;
        if(promise._status !== 'PENDING') return;
        # 所以的执行都是异步调用，保证then是先执行的
        setTimeout(function(){
            promise._status = status;
            st = promise._status === 'FULFILLED'
            queue = promise[st ? '_resolves' : '_rejects'];
            while(fn = queue.shift()) {
                value = fn.call(promise, value) || value;
            }
            promise[st ? '_value' : '_reason'] = value;
            promise['_resolves'] = promise['_rejects'] = undefined;
        });
    }
    # 参数是一个函数，内部提供两个函数作为该函数的参数,分别是resolve 和 reject
    var Promise = function(resolver){
        if (!(typeof resolver === 'function' ))
            throw new TypeError('You must pass a resolver function as the first argument to the promise constructor');
        # 如果不是promise实例，就new一个
        if(!(this instanceof Promise)) return new Promise(resolver);
        var promise = this;
        promise._value;
        promise._reason;
        promise._status = 'PENDING';
        # 存储状态
        promise._resolves = [];
        promise._rejects = [];
        #
        var resolve = function(value) {
            # 由於apply參數是數組
            final.apply(promise,['FULFILLED'].concat([value]));
        }
        var reject = function(reason){
            final.apply(promise,['REJECTED'].concat([reason]));
        }
        resolver(resolve,reject);
    }
    Promise.prototype.then = function(onFulfilled,onRejected){
        var promise = this;
        // 每次返回一个promise，保证是可thenable的
        return new Promise(function(resolve,reject){
            function handle(value) {
                # 這一步很關鍵，只有這樣才可以將值傳遞給下一個resolve
                var ret = typeof onFulfilled === 'function' && onFulfilled(value) || value;
                # 判断是不是promise 对象
                if (ret && typeof ret ['then'] == 'function') {
                    ret.then(function(value) {
                        resolve(value);
                    }, function(reason) {
                        reject(reason);
                    });
                } else {
                    resolve(ret);
                }
            }
            function errback(reason){
                reason = typeof onRejected === 'function' && onRejected(reason) || reason;
                reject(reason);
            }
            if(promise._status === 'PENDING'){
                promise._resolves.push(handle);
                promise._rejects.push(errback);
            }else if(promise._status === FULFILLED){ // 状态改变后的then操作，立刻执行
                callback(promise._value);
            }else if(promise._status === REJECTED){
                errback(promise._reason);
            }
        });
    }
    Promise.prototype.catch = function(onRejected){
        return this.then(undefined, onRejected)
    }
    Promise.prototype.delay = function(ms,value){
        return this.then(function(ori){
            return Promise.delay(ms,value || ori);
        })
    }
    Promise.delay = function(ms,value){
        return new Promise(function(resolve,reject){
            setTimeout(function(){
                resolve(value);
                console.log('1');
            },ms);
        })
    }
    Promise.resolve = function(arg){
        return new Promise(function(resolve,reject){
            resolve(arg)
        })
    }
    Promise.reject = function(arg){
        return Promise(function(resolve,reject){
            reject(arg)
        })
    }
    Promise.all = function(promises){
        if (!Array.isArray(promises)) {
            throw new TypeError('You must pass an array to all.');
        }
        return Promise(function(resolve,reject){
            var i = 0,
                result = [],
                len = promises.length,
                count = len
            # 这里与race中的函数相比，多了一层嵌套，要传入index
            function resolver(index) {
              return function(value) {
                resolveAll(index, value);
              };
            }
            function rejecter(reason){
                reject(reason);
            }
            function resolveAll(index,value){
                result[index] = value;
                if( --count == 0){
                    resolve(result)
                }
            }
            for (; i < len; i++) {
                promises[i].then(resolver(i),rejecter);
            }
        });
    }
    Promise.race = function(promises){
        if (!Array.isArray(promises)) {
            throw new TypeError('You must pass an array to race.');
        }
        return Promise(function(resolve,reject){
            var i = 0,
                len = promises.length;
            function resolver(value) {
                resolve(value);
            }
            function rejecter(reason){
                reject(reason);
            }
            for (; i < len; i++) {
                promises[i].then(resolver,rejecter);
            }
        });
    }
    window.Promise = Promise;
    })(window);
```

## 判断一个单词是否是回文？

```bash

var input = 'mamam';

var arr = Array.from(input);

console.log(arr);

var changeArr = arr.reverse().join('');

console.log(changeArr);

if (changeArr == input) {
    console.log(true);
} else {
    console.log(false);
}

```

## 去掉一组整型数组重复的值

```bash
var input = [1, 13, 24, 11, 11, 14, 1, 2];

let unique = function (arr) {
    let hashTable = {};
    let data = [];
    for (let i = 0, l = arr.length; i < l; i++) {
        if (!hashTable[arr[i]]) {
            hashTable[arr[i]] = true;
            data.push(arr[i]);
        }
    }
    return data
}

console.log(unique(input))
```

## 删除数组元素

```bash
var arr=[1,2,3,4,5,'谦龙','雏田'];
arr.splice(5,1);
console.log(arr,arr[5],arr.length);
```

## 为了不断优化推荐效果，今日头条每天要存储和处理海量数据。假设有这样一种场景：我们对用户按照它们的注册时间先后来标号，对于一类文章，每个用户都有不同的喜好值，我们会想知道某一段时间内注册的用户（标号相连的一批用户）中，有多少用户对这类文章喜好值为k。因为一些特殊的原因，不会出现一个查询的用户区间完全覆盖另一个查询的用户区间(不存在L1<=L2<=R2<=R1)。

```bash
var input1 = '5';
var input2 = '12335';
var input3 = '3';
var input4 = '121';
var input5 = '245';
var input6 = '353';

var num = 0;
var arr = [];
var result = [];

arr.push(Array.from(input4));
arr.push(Array.from(input5));
arr.push(Array.from(input6));

var arr4 = Array.from(input2);

for(var j=0; j<Number(input3); j++) {
    var i = arr[j][0]-1;
    var l = arr[j][1]-1;
    while(i<=l) {
        if(arr4[i]==arr[j][2]) {
            num++;
        }
        i++
    }
    result.push(num);
    num = 0;
}

for(var k=0;k<result.length;k++) {
    console.log(result[k]);
}
```

## 请填充代码，使mySort()能使传入的参数按照从小到大的顺序显示出来。

```bash
function mySort() {
    //使用数组作为参数存储容器
    var tags = new Array();
    for(var i=0; i<arguments.length; i++) {
        tags.push(arguments[i]);
    }
    
    tags.sort(function(a,b) {
        return b-a
    })

    //返回已经排序的数组
    return tags;
}

//传入参数个数不确定
var result = mySort(50,11,16,32,24,99,57,100);

//显示结果
console.info(result);
```

## 数组原型去重

```bash
Array.prototype.setMap = function() {
    var arr = [];
    for(var i=0;i<this.length; i++) {
        if (arr.indexOf(this[i]) == -1) {
            arr.push(this[i])
        }
    }
    return arr;
}

var test = [1,2,3,3,4,1,6]
console.log(test.setMap())
```

## 牛牛有一些排成一行的正方形。每个正方形已经被染成红色或者绿色。牛牛现在可以选择任意一个正方形然后用这两种颜色的任意一种进行染色,这个正方形的颜色将会被覆盖。牛牛的目标是在完成染色之后,每个红色R都比每个绿色G距离最左侧近。牛牛想知道他最少需要涂染几个正方形。

如样例所示: s = RGRGR
我们涂染之后变成RRRGG满足要求了,涂染的个数为2,没有比这个更好的涂染方案。 

```bash
var input = 'RRRGGGRGGGRGGRRRGGRRRGR';
var arr = input.split("");
var rnum = [];
var gnum = [];
var num = 0;

for (var i = 0; i < arr.length; i++) {
    if (arr[i] == 'R') {
        rnum.push(i);
    } else {
        gnum.push(i);
    }
}

for(var j=0;j<gnum.length;j++) {
    if(rnum[rnum.length-1] > gnum[j]) {
        num++
    }
}

if(num > (rnum.length-1)) {
    console.log(rnum.length)
} else {
    console.log(num)
}
```

## 牛牛手中有三根木棍,长度分别是a,b,c。牛牛可以把任一一根木棍长度削短,牛牛的目标是让这三根木棍构成一个三角形,并且牛牛还希望这个三角形的周长越大越好。 

```bash
var input = '1 2 3';
var arrS = input.split(' ');
var arr = [];
arrS.forEach(ele => {
    arr.push(Number(ele)) 
})

function triagle (a, b, c) {
    console.log(a,b,c)
    if (a+b>c && a+c>b && b+c>a && Math.abs(a-b)<c && Math.abs(a-c)<b && Math.abs(b-c)<a) {
        console.log(true);
        return true;
    } else {
        console.log(false);
        return false;
    }
}

while(!triagle(arr[0], arr[1], arr[2])) {
    var max = Math.max.apply(Math,arr);
    var index = arr.indexOf(max);
    arr[index] = max-1;
}

console.log(arr[0]+arr[1]+arr[2])
```

## 如果一个整数只能被1和自己整除,就称这个数是素数。如果一个数正着反着都是一样,就称为这个数是回文数。例如:6, 66, 606, 6666如果一个数字既是素数也是回文数,就称这个数是回文素数牛牛现在给定一个区间[L, R],希望你能求出在这个区间内有多少个回文素数。

```bash
var input = '5 1000';
var arr = input.split(" ")
var num = 0;

for (var i = Number(arr[0]); i <= Number(arr[1]); i++) {
    var str = String(i)
    var strX = String(i).split('').reverse().join('')
    if (str == strX && zhishu(i) && i!=1) {
        num++
    }
}

function zhishu(n) {
    var zhishu = true;
    for (var i = 2; i <= n / 2; i++) {
        if (n % i === 0) {
            zhishu = false;
        }
    }
    return zhishu;
}

console.log(num)
```

## 牛牛有一个长度为n的整数序列,牛牛想对这个序列进行重排为一个非严格升序序列。牛牛比较懒惰,他想移动尽量少的数就完成重排,请你帮他计算一下他最少需要移动多少个序列中的元素。(当一个元素不在它原来所在的位置,这个元素就是被移动了的) 

```bash
var input1 = '3';
var input2 = '3 2 1';
var num = 0;

var arr = input2.split(' ');
var newArr = input2.split(' ').sort((a,b) => {
    return a-b;
})

for (var i=0; i<arr.length; i++) {
    if (arr[i] == newArr[i]) {
        num++
    }
}

console.log(arr.length-num);
```

## dom深度广度遍历

```bash
<body>
    <div class="root">
        <div class="container">
            <section class="sidebar">
                <ul class="menu"></ul>
            </section>
            <section class="main">
                <article class="post"></article>
                <p class="copyright"></p>
            </section>
        </div>
    </div>
    <script>
        const traverse = (ndRoot) => {
            #深度遍历
            printInfo(ndRoot);
            if (ndRoot.children.length) {
                console.log(ndRoot.children)
                Array.from(ndRoot.children).forEach(function(el) {
                    traverse(el)
                })
            }
            #广度遍历
            #const queue = [ndRoot];
            # while (queue.length) {
            #     const node = queue.shift();
            #     printInfo(node);

            #     if (!node.children.length) {
            #         continue;
            #     }
            #     Array.from(node.children).forEach(x => queue.push(x));
            # }
        };

        const printInfo = (node) => {
            console.log(node.tagName, `.${node.className}`);
        };

        // kickoff
        traverse(document.querySelector('.root'));
    </script>
</body>
```

## ES7异步

```bash
const sleep = (timeountMS) => new Promise((resolve) => {
    setTimeout(resolve, timeountMS);
});

(async () => {  // 声明即执行的 async 函数表达式
    for (var i = 0; i < 5; i++) {
        await sleep(1000);
        console.log(new Date, i);
    }

    await sleep(1000);
    console.log(new Date, i);
})();
```

## 牛牛的老师给出了一个区间的定义:对于x ≤ y,[x, y]表示x到y之间(包括x和y)的所有连续整数集合。例如[3,3] = {3}, [4,7] = {4,5,6,7}.牛牛现在有一个长度为n的递增序列,牛牛想知道需要多少个区间并起来等于这个序列。

```bash
var input = '5';
var input2 = '1 3 5 6 7';

var arr = input2.split(' ');
var count = 0;

for (var i=0; i<arr.length; i++) {
    if (Number(arr[i+1]) - Number(arr[i]) > 1) {
        count++
    }
}

console.log(count+1);
```

## 牛牛举办了一场数字游戏,有n个玩家参加这个游戏,游戏开始每个玩家选定一个数,然后将这个数写在纸上(十进制数,无前缀零),然后接下来对于每一个数字将其数位按照非递减顺序排列,得到新的数,新数的前缀零将被忽略。得到最大数字的玩家赢得这个游戏。 

```bash
var input = '3';
var input2 = '9638 8210 331';

var arr = input2.split(' ');
var arr2 = [];
var newArr = [];

arr.forEach((el) => {
    arr2.push(Array.from(el));
})

for (var i = 0; i < arr2.length; i++) {
    arr2[i].sort((a, b) => {
        return a - b;
    })
    newArr.push(Number(arr2[i].join('')));
}

console.log(Math.max.apply(Math, newArr));
```

## 扑克牌游戏大家应该都比较熟悉了，一副牌由54张组成，含3~A，2各4张，小王1张，大王1张。牌面从小到大用如下字符和字符串表示（其中，小写joker表示小王，大写JOKER表示大王）:) 

3 4 5 6 7 8 9 10 J Q K A 2 joker JOKER 
输入两手牌，两手牌之间用“-”连接，每手牌的每张牌以空格分隔，“-”两边没有空格，如：4 4 4 4-joker JOKER
请比较两手牌大小，输出较大的牌，如果不存在比较关系则输出ERROR

基本规则：
（1）输入每手牌可能是个子，对子，顺子（连续5张），三个，炸弹（四个）和对王中的一种，不存在其他情况，由输入保证两手牌都是合法的，顺子已经从小到大排列；
（2）除了炸弹和对王可以和所有牌比较之外，其他类型的牌只能跟相同类型的存在比较关系（如，对子跟对子比较，三个跟三个比较），不考虑拆牌情况（如：将对子拆分成个子）
（3）大小规则跟大家平时了解的常见规则相同，个子，对子，三个比较牌面大小；顺子比较最小牌大小；炸弹大于前面所有的牌，炸弹之间比较牌面大小；对王是最大的牌；
（4）输入的两手牌不会出现相等的情况。

答案提示：
（1）除了炸弹和对王之外，其他必须同类型比较。
（2）输入已经保证合法性，不用检查输入是否是合法的牌。
（3）输入的顺子已经经过从小到大排序，因此不用再排序了.

```bash
var input = '4 4 4 4-joker JOKER';

var first = input.split('-')[0];
var second = input.split('-')[1];

var type = ['one', 'two', 'five', 'three', 'four', 'king'];
var sort = ['3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K', 'A', '2', 'j', 'J'];

var arr1 = first.split(' ');
var arr2 = second.split(' ');

var type1 = arrType(arr1);
var type2 = arrType(arr2);

if (type1 == type2) {
    var a = sort.indexOf(arr1[0])
    var b = sort.indexOf(arr2[0])
    if (a>b) {
        console.log(first);
    } else {
        console.log(second);
    }

} else if (type1=='four'||type2=='four'||type1=='king'||type2=='king') {
    if (type1=='king') {
        console.log(first);
    } else if (type2=='king') {
        console.log(second);
    } else if (type1=='four') {
        console.log(first);
    } else {
        console.log(second);
    }

} else {
    console.log('ERROR')
}

function arrType (arr) {
    switch (arr.length) {
        case 1:
            return type[0]; 
        case 2:
            if (arr[0] == 'joker') {
                return type[5];
            } else {
                return type[1];
            }
        case 3:
            return type[3];
        case 5:
            return type[2];
        case 4:
            return type[4];
        default:
            break;
    }
}
```

## 

```bash
while (line = readline()) {
    var line1 = line.split(" ");
    var n = Number(line1[0]);
    var m = Number(line1[1]);
    var score = [];
    var arr = readline().split(" ");
    arr.forEach((el) => {
        score.push(Number(el))
    })

    for (var i = 0; i < m; i++) {
        var line = readline().split(" ");
        var a = Number(line[1]);
        var b = Number(line[2]);
        if (line[0] == 'Q') {
            if (a > b) {
                var temp = a;
                a = b;
                b = temp;
            }
            var max = 0;
            for (var j = a - 1; j < b; j++) {
                if (max < score[j]) {
                    max = score[j];
                }
            }
            console.log(max);
        } else {
            score[a - 1] = b;
        }
    }
}
```

## 有这样一道智力题：“某商店规定：三个空汽水瓶可以换一瓶汽水。小张手上有十个空汽水瓶，她最多可以换多少瓶汽水喝？”答案是5瓶，方法如下：先用9个空瓶子换3瓶汽水，喝掉3瓶满的，喝完以后4个空瓶子，用3个再换一瓶，喝掉这瓶满的，这时候剩2个空瓶子。然后你让老板先借给你一瓶汽水，喝掉这瓶满的，喝完以后用3个空瓶子换一瓶满的还给老板。如果小张手上有n个空汽水瓶，最多可以换多少瓶汽水喝？ 

```bash
var input = '3';
var input2 = '10';
var input3 = '81';

var arr = [];
var count = 0;
arr.push(input);
arr.push(input2);
arr.push(input3);

for (var i = 0; i < arr.length; i++) {
    var num = Number(arr[i]);
    compete(count, num);
}

function compete(count, num) {
    var use = Math.floor(num / 3);
    count = count + use;
    var next = use + num % 3;
    if (next > 2) {
        compete(count, next)
    } else if (next == 2) {
        count = count + 1;
        console.log(count);
        count = 0;
    } else {
        console.log(count);
        count = 0;
    }
}
```

## 有一个数组a[N]顺序存放0~N-1，要求每隔两个数删掉一个数，到末尾时循环至开头继续进行，求最后一个被删掉的数的原始下标位置。以8个数(N=7)为例:｛0，1，2，3，4，5，6，7｝，0->1->2(删除)->3->4->5(删除)->6->7->0(删除),如此循环直到最后一个数被删除。

```bash
var input = '249';
var data = [];

for (var i = 0; i < Number(input); i++) {
    data.push(i);
}

function third (array) {
    for (var j = 2; j < array.length; j=j+3) {
        array[j] = 'a';
    }
    delet(array);
}

function delet (array) {
    var temp = [];
    for (var k=0;k<array.length; k++) {
        if (array[k] != 'a') {
            temp.push(array[k]);
        }
    }
    data = [];
    for (var p=0; p<temp.length; p++) {
        data.push(temp[p])
    }
    console.log(data)
}

while(data.length > 3) {
    third(data);
}

console.log(data[2])
```

##  有一个数组a[N]顺序存放0~N-1，要求每隔两个数删掉一个数，到末尾时循环至开头继续进行，求最后一个被删掉的数的原始下标位置。以8个数(N=7)为例:｛0，1，2，3，4，5，6，7｝，0->1->2(删除)->3->4->5(删除)->6->7->0(删除),如此循环直到最后一个数被删除。

```bash
var length = 8;
var arr = []

for (var i = 0; i < length; i++) {
    arr.push(i)
}

var index = 0

while (arr.length > 1) {
    index = (index + 2) % arr.length
    arr.splice(index, 1) //数组删除
    console.log(arr)
}

console.log(arr[0])
```

# LeetCode

##

```bash
console.log(groupAnagrams(["eat", "tea", "tan", "ate", "nat", "bat"]))

function groupAnagrams (strs) {
    var arr = [];
    var set = [];
    var output = [];

    for (var i = 0; i < strs.length; i++) {
        var sortArr = strs[i].split('')
        sortArr.sort((a,b) => {
            return a > b;
        })
        sortArr = sortArr.join('');
        arr.push(sortArr);
    }
    for (var j = 0; j < arr.length; j++) {
        if (set.indexOf(arr[j]) == -1) {
            set.push(arr[j]);
        }
    }

    for( var k = 0; k < arr.length; k++) {
        var index = set.indexOf(arr[k]);
        output[index] = [];
    }
    for( var k = 0; k < arr.length; k++) {
        var index = set.indexOf(arr[k]);
        output[index].push(strs[k]);
    }

    return output;
};
```

## 

```bash
var L = 1;
var R = 2;
var i = 0;
var X, Y, Xs, Ys;

var C = 2 * Math.PI * R;
while (L > R) {
    L = L - R;
    i++;
}

var degree = (L / C) * 360;

switch (Math.floor(degree / 90)) {
    case 0:
        X = R * Math.cos(degree * Math.PI / 180);
        Y = R * Math.sin(degree * Math.PI / 180);
        break;
    case 1:
        X = R * Math.cos((180 - degree) * Math.PI / 180) * -1;
        Y = R * Math.sin((180 - degree) * Math.PI / 180);
    case 2:
        X = R * Math.cos((degree - 180) * Math.PI / 180) * -1;
        Y = R * Math.sin((degree - 180) * Math.PI / 180) * -1;
    case 3:
        X = R * Math.cos((360 - degree) * Math.PI / 180);
        Y = R * Math.sin((360 - degree) * Math.PI / 180) * -1;
    default:
        break;
}

console.log('顺时针', X.toFixed(3), Y.toFixed(3));
console.log('逆时针', X.toFixed(3), Y.toFixed(3) * -1);
```

## js二维数组全排列

```bash
function serialArray(arr) {
	var lengthArr = [];
	var productArr = [];
	var result = [];
	var length = 1;
	for (var i = 0; i < arr.length; i++) {
		var len = arr[i].length;
		lengthArr.push(len);
		var product = i === 0 ? 1 : arr[i - 1].length * productArr[i - 1];
		productArr.push(product);
		length *= len;
	}
	for (var i = 0; i < length; i++) {
		var resultItem = '';
		for (var j = 0; j < arr.length; j++) {
			resultItem += arr[j][Math.floor(i / productArr[j]) % lengthArr[j]];
		}
		result.push(resultItem);
	}
	return result
}
```

## 冒泡排序

```bash
function maopao (nums) {
	for (var i=0; i<nums.length-2; i++) {
		for (var j = 0, s = nums.length-1-i; j<s ;j++) {
			if (nums[j] < nums[j+1]) {
				var temp = nums[j];
				nums[j] = nums[j+1];
				nums[j+1] = temp;
			}
		}
	}

	return nums;
}
```

## 选择排序

```bash
function maopao (nums) {
	var sort = [];
	for (var i=0; i<nums.length;) {
		var max = Math.max.apply(Math, nums);
		sort.push(max);
		nums.splice(nums.indexOf(max), 1);
	}

	return sort;
}
```

## linux tcpdump监听网卡eth0,对方主机IP为10.1.1.180,tcp端口为80的数据,相应命令为