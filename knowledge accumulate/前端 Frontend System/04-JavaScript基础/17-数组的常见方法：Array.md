---

　　title: 17-数组的常见方法
publish: true

---

## 数组的方法清单

### 数组的类型相关

|方法|描述| 备注 |
| :--------------------------------- | :----------------------------------------- | :----- |
|Array.isArray()|判断是否为数组|  |
|toString()| 将数组转换为字符串                       |<br />|
|Array.from(arrayLike)| 将**伪数组**转化为**真数组** |  |
|Array.of(value1, value2, value3)| 创建数组：将**一系列值**转换成数组 |      |

　　注意，获取数组的长度是用 `length` 属性，不是方法。关于 `length` 属性，详见上一篇文章。["获取数组的长度"](siyuan://blocks/20210805093548-xyn5d6v)

### 数组元素的添加和删除

| 方法      | 描述                                                                       | 备注           |
| :-------- | :------------------------------------------------------------------------- | :------------- |
| push()    | 向数组的**最后面**插入一个或多个元素，返回结果为新数组的**长度**           | 会改变原数组   |
| pop()     | 删除数组中的**最后一个**元素，返回结果为**被删除的元素**                   | 会改变原数组   |
| unshift() | 在数组**最前面**插入一个或多个元素，返回结果为新数组的**长度**             | 会改变原数组   |
| shift()   |删除数组中的**第一个**元素，返回结果为**被删除的元素**|  |
| slice()   |从数组中**提取**指定的一个或多个元素，返回结果为**新的数组**| 不会改变原数组 |
| splice()  |从数组中**删除**指定的一个或多个元素，返回结果为**被删除元素组成的新数组**| 会改变原数组   | 
| fill()    |填充数组：用固定的值填充数组，返回结果为**新的数组**| 不会改变原数组 |

### 数组的合并和拆分

| 方法     | 描述                                                 | 备注             |
| :------- | :--------------------------------------------------- | :--------------- |
| concat() | 合并数组：连接两个或多个数组，返回结果为**新的数组** | 不会改变原数组   |
| join()   | 将数组转换为字符串，返回结果为**转换后的字符串**     | 不会改变原数组   |
| split()  | 将字符串按照指定的分隔符，组装为数组                 | 不会改变原字符串 |

　　注意，`split()`是字符串的方法，不是数组的方法。

### 数组排序

| 方法      | 描述                                                    | 备注         |
| :-------- | :------------------------------------------------------ | :----------- |
| reverse() | 反转数组，返回结果为**反转后的数组**                    | 会改变原数组 |
| sort()    | 对数组的元素,默认按照**Unicode 编码**，从小到大进行排序 | 会改变原数组 |

### 查找数组的元素

| 方法                  | 描述                                                                           | 备注                                                     |
| :---------------------- | :------------------------------------------------------------------------------- | :--------------------------------------------------------- |
| indexOf(value)        | 从前往后索引，检索一个数组中是否含有指定的元素的第一个索引                     | 如果不存在，则返回-1<br />                                   |
| lastIndexOf(value)    | 从后往前索引，检索一个数组中是否含有指定的元素的第一个索引                     | 如果不存在，则返回-1                                     |
| includes(item)        | 数组中是否包含指定的内容                                                       | 如果包含则返回 true，否则返回 false                      |
| find(function())      | 找出**第一个**满足「指定条件返回 true」的元素                            |                                                          |
| findIndex(function()) | 找出**第一个**满足「指定条件返回 true」的元素的 index                    |                                                          |
|splice()| 确保数组中的每个元素都满足「指定条件返回 true」，则停止遍历，此方法才返回 true | 全真才为真。要求每一项都返回 true，最终的结果才返回 true | 
| some()                | 数组中只要有一个元素满足「指定条件返回 true」，则停止遍历，此方法就返回 true   | 一真即真。只要有一项返回 true，最终的结果就返回 true     |

### 遍历数组

| 方法      | 描述                                                                         | 备注                                                                           |
| :---------- | :----------------------------------------------------------------------------- | :------------------------------------------------------------------------------- |
| for 循环  | 这个大家都懂                                                                 |                                                                                |
| forEach() | 和 for 循环类似，但需要兼容 IE8 以上                                         | forEach() 没有返回值。也就是说，它的返回值是 undefined                         |
| map()     |对原数组中的每一项进行加工，将组成新的数组| 不会改变原数组  ["JS map()方法[Array]"](siyuan://blocks/20210913113937-q0yrg2z)    |
| filter()  | 过滤数组：返回结果是 true 的项，将组成新的数组，返回结果为**新的数组** | 不会改变原数组  ["JS filter()方法[Array]"](siyuan://blocks/20210917112417-dijvirb) |
| reduce    | 接收一个函数作为累加器，返回值是回调函数累计处理的结果                       |                                                                                |

## isArray()：判断是否为数组

　　语法：

```javascript
布尔值 = Array.isArray(被检测的数组);
```

　　以前，我们会通过 `A instanceof B`来判断 A 是否属于 B 类型。但是在数组里，这种 instanceof 方法已经用的不多了，因为有 isArray()方法。

## toString()：数组转换为字符串

```javascript
字符串 = 数组.toString();
```

　　解释：把数组转换成字符串，每一项用`,`分割。

　　备注：大多数的数据类型都可以使用`.toString()`方法，将其转换为字符串。

### 知识点补充：将数组转换为字符串，有哪些方式

　　方式 1：

```js
字符串 = 数组.toString();
```

　　方式 2：

```js
字符串 = String(数组);
```

　　方式 3：

```js
字符串 = 数组.join(','); // 将数组转为字符串，每一项用 英文逗号 分隔
```

## Array.from()：将伪数组转换为真数组

　　**语法**：

```javascript
array = Array.from(arrayLike);
```

　　**作用**：将**伪数组**或可遍历对象转换为**真数组**。

　　代码举例：

```js
const name = 'qianguyihao';
console.log(Array.from(name)); // 打印结果是数组：["q","i","a","n","g","u","y","i","h","a","o"]
```

### 伪数组与真数组的区别

　　**伪数组**：包含 length 属性的对象或可迭代的对象。

　　另外，伪数组的原型链中没有 Array.prototype，而真数组的原型链中有 Array.prototype。因此伪数组没有数组的一般方法，比如 pop()、join() 等方法。

### 伪数组举例

```html
<body>
    <button>按钮1</button>
    <button>按钮2</button>
    <button>按钮3</button>

    <script>
        let btnArray = document.getElementsByTagName('button');
        console.log(btnArray);
        console.log(btnArray[0]);
    </script>
</body>
```

　　上面的布局中，有三个 button 标签，我们通过`getElementsByTagName`获取到的`btnArray`实际上是**伪数组**，并不是真实的数组：

　　![](http://img.smyhvae.com/20180402_1116.png)

　　既然`btnArray`是伪数组，它就不能使用数组的一般方法，否则会报错：

　　![](http://img.smyhvae.com/20180402_1121.png)

　　解决办法：采用`Array.from`方法将`btnArray`这个伪数组转换为真数组即可：

```javascript
Array.from(btnArray);
```

　　然后就可以使用数组的一般方法了：

　　![](http://img.smyhvae.com/20180402_1125.png)

## Array.of()：创建数组

　　**语法**：

```javascript
Array.of(value1, value2, value3);
```

　　**作用**：根据参数里的内容，创建数组。

　　**举例**：

```javascript
const arr = Array.of(1, 'abc', true);
console.log(arr); // 打印结果是数组：[1, "abc", true]
```

　　补充：`new Array()`和 `Array.of()`的区别在于：当参数只有一个时，前者表示数组的长度，后者表示数组中的内容。

　　

## 数组元素的添加和删除

### push()

　　`push()`：向数组的**最后面**插入一个或多个元素，返回结果为新数组的**长度**。会改变原数组，因为原数组变成了新数组。

　　语法：

```javascript
新数组的长度 = 数组.push(元素);
```

　　代码举例：

```javascript
var arr = ['王一', '王二', '王三'];

var result1 = arr.push('王四'); // 末尾插入一个元素
var result2 = arr.push('王五', '王六'); // 末尾插入多个元素

console.log(result1); // 打印结果：4
console.log(result2); // 打印结果：6
console.log(JSON.stringify(arr)); // 打印结果：["王一","王二","王三","王四","王五","王六"]
```

### pop()

　　`pop()`：删除数组中的**最后一个**元素，返回结果为**被删除的元素**。

　　语法：

```javascript
被删除的元素 = 数组.pop();
```

　　代码举例：

```javascript
var arr = ['王一', '王二', '王三'];

var result1 = arr.pop();

console.log(result1); // 打印结果：王三
console.log(JSON.stringify(arr)); // 打印结果：["王一","王二"]
```

### unshift()

　　`unshift()`：在数组**最前面**插入一个或多个元素，返回结果为新数组的**长度**。会改变原数组，因为原数组变成了新数组。插入元素后，其他元素的索引会依次调整。

　　语法：

```javascript
新数组的长度 = 数组.unshift(元素);
```

　　代码举例：

```javascript
var arr = ['王一', '王二', '王三'];

var result1 = arr.unshift('王四'); // 最前面插入一个元素
var result2 = arr.unshift('王五', '王六'); // 最前面插入多个元素

console.log(result1); // 打印结果：4
console.log(result2); // 打印结果：6
console.log(JSON.stringify(arr)); // 打印结果：["王五","王六","王四","王一","王二","王三"]
```

### shift()

　　`shift()`：删除数组中的**第一个**元素，返回结果为**被删除的元素**。

　　语法：

```javascript
被删除的元素 = 数组.shift();
```

　　代码举例：

```javascript
var arr = ['王一', '王二', '王三'];

var result1 = arr.shift();

console.log(result1); // 打印结果：王一
console.log(JSON.stringify(arr)); // 打印结果：["王二","王三"]
```

### slice()

　　`slice()`：从数组中**提取**指定的一个或者多个元素，返回结果为**新的数组**（不会改变原来的数组）。

　　备注：该方法不会改变原数组，而是将截取到的元素封装到一个新数组中返回。

　　**语法**：

```javascript
新数组 = 原数组.slice(开始位置的索引, 结束位置的索引); //注意：包含开始索引，不包含结束索引
```

　　举例：

```javascript
const arr = ['a', 'b', 'c', 'd', 'e', 'f'];

const result1 = arr.slice(); // 不加参数时，则获取所有的元素。相当于数组的整体赋值
const result2 = arr.slice(2); // 从第二个值开始提取，直到末尾
const result3 = arr.slice(-2); // 提取最后两个元素
const result4 = arr.slice(2, 4); // 提取从第二个到第四个之间的元素（不包括第四个元素）
const result5 = arr.slice(4, 2); // 空

console.log('arr:' + JSON.stringify(arr));
console.log('result1:' + JSON.stringify(result1));
console.log('result2:' + JSON.stringify(result2));
console.log('result3:' + JSON.stringify(result3));
console.log('result4:' + JSON.stringify(result4));
console.log('result5:' + JSON.stringify(result5));
```

　　打印结果：

```javascript
arr: ['a', 'b', 'c', 'd', 'e', 'f'];
result1: ['a', 'b', 'c', 'd', 'e', 'f'];
result2: ['c', 'd', 'e', 'f'];
result3: ['e', 'f'];
result4: ['c', 'd'];
result5: [];
```

　　**补充**：

　　很多前端开发人员会用 slice()将伪数组，转化为真数组。写法如下：

```javascript
// 方式1
array = Array.prototype.slice.call(arrayLike);

// 方式2
array = [].slice.call(arrayLike);
```

　　ES6 看不下去这种蹩脚的转化方法，于是出了一个新的 API：（专门用来将伪数组转化成真数组）

```javascript
array = Array.from(arrayLike);
```

　　关于这个 API 的详细介绍，上面的内容已经讲了，请往前翻。

### splice()

　　`splice()`：从数组中**删除**指定的一个或多个元素，返回结果为**被删除元素组成的新数组**（会改变原来的数组）。

　　备注：该方法会改变原数组，会将指定元素从原数组中删除；被删除的元素会封装到一个新的数组中返回。

　　语法：

```javascript

新数组 = 原数组.splice(起始索引index, 需要删除的个数);

新数组 = 原数组.splice(起始索引index, 需要删除的个数, 新的元素1, 新的元素2...);
```

　　上方语法中，第三个及之后的参数，表示：删除元素之后，向原数组中添加新的元素，这些元素将会自动插入到起始位置索引的前面。也可以理解成：删除了哪些元素，就在那些元素的所在位置补充新的内容。

　　`slice()`方法和`splice()`方法很容易搞混，请一定要注意区分。

　　举例 1：

```javascript
var arr1 = ['a', 'b', 'c', 'd', 'e', 'f'];
var result1 = arr1.splice(1); //从第index为1的位置开始，删除元素

console.log('arr1：' + JSON.stringify(arr1));
console.log('result1：' + JSON.stringify(result1));
```

　　打印结果：

```
    arr1：["a"]
    result1：["b","c","d","e","f"]
```

　　举例 2：

```javascript
var arr2 = ['a', 'b', 'c', 'd', 'e', 'f'];
var result2 = arr2.splice(-2); //删除最后两个元素

console.log('arr2：' + JSON.stringify(arr2));
console.log('result2：' + JSON.stringify(result2));
```

　　打印结果：

```
    arr2：["a","b","c","d"]
    result2：["e","f"]
```

　　举例 3：

```javascript
var arr3 = ['a', 'b', 'c', 'd', 'e', 'f'];
var result3 = arr3.splice(1, 3); //从第index为1的位置开始删除元素,一共删除三个元素

console.log('arr3：' + JSON.stringify(arr3));
console.log('result3：' + JSON.stringify(result3));
```

　　打印结果：

```
    arr3：["a","e","f"]
    result3：["b","c","d"]
```

　　举例 4：（我们来看看**第三个参数**的用法）

```javascript
var arr4 = ['a', 'b', 'c', 'd', 'e', 'f'];

//从第index为1的位置开始删除元素,一共删除三个元素。并且在 index=1 的前面追加两个元素
var result4 = arr4.splice(1, 3, '千古壹号', 'vae');

console.log('arr4：' + JSON.stringify(arr4));
console.log('result4：' + JSON.stringify(result4));
```

　　打印结果：

```javascript
arr4：["a","千古壹号","vae","e","f"]
result4：["b","c","d"]
```

### fill()

　　`fill()`：用一个固定值填充数组，返回结果为**新的数组**。不会改变原数组。

　　语法：

```js
// 用一个固定值填充数组。数组里的每个元素都会被这个固定值填充
新数组 = 数组.fill(固定值);

// 从 startIndex 开始的数组元素，用固定值填充
新数组 = 数组.fill(固定值, startIndex);

// 从 startIndex 到 endIndex 之间的元素（包左不包右），用固定值填充
新数组 = 数组.fill(固定值, startIndex, endIndex);
```

　　举例：

```js
// 创建一个长度为4的空数组，然后用 'f' 来填充这个空数组
console.log(Array(4).fill('f')); // ['f', 'f', 'f,' 'f']

// 将现有数组的每一个元素都进行填充
console.log(['a', 'b', 'c', 'd'].fill('f')); // ['f', 'f', 'f,' 'f']

// 指定位置进行填充
console.log(['a', 'b', 'c', 'd'].fill('f', 1, 3)); // ["a", "f", "f", "d"]
```

## 数组的合并和拆分

### concat()

　　`concat()`：连接两个或多个数组，返回结果为**新的数组**。不会改变原数组。`concat()`方法的作用是**数组合并**。

　　语法：

```javascript
    新数组 = 数组1.concat(数组2, 数组3 ...);
```

　　举例：

```javascript
const arr1 = [1, 2, 3];
const arr2 = ['a', 'b', 'c'];
const arr3 = ['千古壹号', 'vae'];

const result1 = arr1.concat(arr2);

const result2 = arr2.concat(arr1, arr3);

console.log('arr1 =' + JSON.stringify(arr1));
console.log('arr2 =' + JSON.stringify(arr2));
console.log('arr3 =' + JSON.stringify(arr3));

console.log('result1 =' + JSON.stringify(result1));
console.log('result2 =' + JSON.stringify(result2));
```

　　打印结果：

```javascript
arr1 = [1, 2, 3];
arr2 = ['a', 'b', 'c'];
arr3 = ['千古壹号', 'vae'];

result1 = [1, 2, 3, 'a', 'b', 'c'];
result2 = ['a', 'b', 'c', 1, 2, 3, '千古壹号', 'vae'];
```

　　从打印结果中可以看到，原数组并没有被修改。

　　**数组合并的另一种方式**：

　　我们可以使用`...`这种展开语法，将两个数组进行合并。举例如下：

```js
const arr1 = [1, 2, 3];

const result = ['a', 'b', 'c', ...arr1];
console.log(JSON.stringify(result)); // 打印结果：["a","b","c",1,2,3]
```

### join()

　　`join()`：将数组转换为字符串，返回结果为**转换后的字符串**（不会改变原来的数组）。

　　补充：`join()`方法可以指定一个**字符串**作为参数，这个字符串将会成为数组中元素的**连接符**；如果不指定连接符，则默认使用 `,` 作为连接符，此时和 `toString()的效果是一致的`。

　　语法：

```javascript
新的字符串 = 原数组.join(参数); // 参数选填
```

　　代码举例：

```javascript
var arr = ['a', 'b', 'c'];

var result1 = arr.join(); // 这里没有指定连接符，所以默认使用 , 作为连接符

var result2 = arr.join('-'); // 使用指定的字符串作为连接符

console.log(typeof arr); // 打印结果：object
console.log(typeof result1); // 打印结果：string

console.log('arr =' + JSON.stringify(arr));
console.log('result1 =' + JSON.stringify(result1));
console.log('result2 =' + JSON.stringify(result2));
```

　　上方代码中，最后三行的打印结果是：

```bash
arr =["a","b","c"]
result1 =a,b,c
result2 =a-b-c
```

### split()

> 注意，`split()`是字符串的方法，不是数组的方法。
>

　　语法：

```javascript
新的数组 = str.split(分隔符);
```

　　解释：通过指定的分隔符，将一个字符串拆分成一个**数组**。不会改变原字符串。

　　备注：`split()` 这个方法在实际开发中用得非常多。一般来说，从接口拿到的 json 数据中，经常会收到类似于 `"q, i, a, n"` 这样的字符串，前端需要将这个字符串拆分成 `['q', 'i', 'a', 'n']` 数组，这个时候 `split()` 方法就派上用场了。

　　["split()：字符串转换为数组 【重要】"](siyuan://blocks/20210805093548-fc89n55)

## reverse()

　　`reverse()`：反转数组，返回结果为**反转后的数组**（会改变原来的数组）。

　　语法：

```js
反转后的数组 = 数组.reverse();
```

　　举例：

```javascript
var arr = ['a', 'b', 'c', 'd', 'e', 'f'];

var result = arr.reverse(); // 将数组 arr 进行反转

console.log('arr =' + JSON.stringify(arr));
console.log('result =' + JSON.stringify(result));
```

　　打印结果：

```
arr =["f","e","d","c","b","a"]
result =["f","e","d","c","b","a"]
```

　　从打印结果可以看出，原来的数组已经被改变了。

## sort()方法

> sort()方法需要好好理解。
>

　　`sort()`：对数组的元素进行从小到大来排序（会改变原来的数组）。

### sort()方法：无参时

　　如果在使用 sort() 方法时不带参，则默认按照**Unicode 编码**，从小到大进行排序。

　　**举例 1**：（当数组中的元素为字符串时）

```javascript
let arr1 = ['e', 'b', 'd', 'a', 'f', 'c'];

let result = arr1.sort(); // 将数组 arr1 进行排序

console.log('arr1 =' + JSON.stringify(arr1));
console.log('result =' + JSON.stringify(result));
```

　　打印结果：

```
    arr1 =["a","b","c","d","e","f"]
    result =["a","b","c","d","e","f"]
```

　　从上方的打印结果中，我们可以看到，sort 方法会改变原数组，而且方法的返回值也是同样的结果。

　　**举例 2**：（当数组中的元素为数字时）

```javascript
let arr2 = [5, 2, 11, 3, 4, 1];

let result = arr2.sort(); // 将数组 arr2 进行排序

console.log('arr2 =' + JSON.stringify(arr2));
console.log('result =' + JSON.stringify(result));
```

　　打印结果：

```
arr2 =[1,11,2,3,4,5]
result =[1,11,2,3,4,5]
```

　　上方的打印结果中，你会发现，使用 sort() 排序后，数字`11`竟然在数字`2`的前面。这是为啥呢？因为上面讲到了，`sort()`方法是按照**Unicode 编码**进行排序的。

　　那如果我想让 arr2 里的数字，完全按照从小到大排序，怎么操作呢？继续往下看。

### sort()方法：带参时，自定义排序规则

　　如果在 sort()方法中带参，我们就可以**自定义**排序规则。具体做法如下：

　　我们可以在 sort()添加一个回调函数，来指定排序规则。回调函数中需要定义两个形参，浏览器将会分别使用数组中的元素作为实参去调用回调函数。

　　浏览器根据回调函数的返回值来决定元素的排序：（**重要**）

- 如果返回一个**大于 0** 的值，则元素会**交换位置**
- 如果返回一个**小于 0** 的值，则元素**位置不变**
- 如果返回一个**等于 0** 的值，则认为两个元素相等，则**不交换位置**

　　如果只是看上面的文字，可能不太好理解，我们来看看下面的例子，你肯定就能明白。

### 举例：将数组中的数字按照从小到大排序

　　**写法 1**：

```javascript
var arr = [5, 2, 11, 3, 4, 1];

// 自定义排序规则
var result = arr.sort(function (a, b) {
    if (a > b) {
        // 如果 a 大于 b，则交换 a 和 b 的位置
        return 1;
    } else if (a < b) {
        // 如果 a 小于 b，则位置不变
        return -1;
    } else {
        // 如果 a 等于 b，则位置不变
        return 0;
    }
});

console.log('arr =' + JSON.stringify(arr));
console.log('result =' + JSON.stringify(result));
```

　　打印结果：

```javascript
arr = [1, 2, 3, 4, 5, 11];
result = [1, 2, 3, 4, 5, 11];
```

　　上方代码的写法太啰嗦了，其实也可以简化为如下写法：

　　**写法 2**：（冒泡排序）

```javascript
let arr = [5, 2, 11, 3, 4, 1];

// 自定义排序规则
let result = arr.sort(function (a, b) {
    return a - b; // 升序排列
    // return b - a; // 降序排列
});

console.log('arr =' + JSON.stringify(arr));
console.log('result =' + JSON.stringify(result));
```

　　打印结果不变。

　　上方代码还可以写成 ES6 的形式，也就是将 function 改为箭头函数，其写法如下。

　　**写法 3**：（箭头函数）

```js
let arr = [5, 2, 11, 3, 4, 1];

// 自定义排序规则
let result = arr.sort((a, b) => {
    return a - b; // 升序排列
});

console.log('arr =' + JSON.stringify(arr));
console.log('result =' + JSON.stringify(result));
```

　　上方代码，因为函数体内只有一句话，所以可以去掉 return 语句，继续简化为如下写法。

　　**写法 4**：**（推荐）**  #排序数组中的数字（冒泡排序）#

```js
let arr = [5, 2, 11, 3, 4, 1];

// 自定义排序规则：升序排列
let result = arr.sort((a, b) => a - b);
// 自定义排序规则：降序排列
//let result2 = arr.sort((a, b) => b - a);

console.log('arr =' + JSON.stringify(arr));
console.log('result =' + JSON.stringify(result));
```

　　上面的各种写法中，写法 4 是我们在实战开发中用得最多的。

　　为了确保代码的简洁优雅，接下来的代码中，凡是涉及到函数，我们将尽量采用 ES6 中的箭头函数来写。

### sort 方法举例：将数组从小到大排序

　　将数组从小到大排序，这个例子很常见。但在实际开发中，总会有一些花样。

　　下面这段代码，在实际开发中，经常用到，一定要掌握。完整代码如下：

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Document</title>
    </head>
    <body>
        <script>
            let dataList = [
                {
                    title: '品牌鞋子，高品质低价入手',
                    publishTime: 200,
                },
                {
                    title: '不是很贵，但是很暖',
                    publishTime: 100,
                },
                {
                    title: '无法拒绝的美食，跟我一起吃吃',
                    publishTime: 300,
                },
            ];

            console.log('qianguyihao 排序前的数组：' + JSON.stringify(dataList));

            // 将dataList 数组，按照 publishTime 字段，从小到大排序。（会改变原数组）
            dataList.sort((a, b) => parseInt(a.publishTime) - parseInt(b.publishTime));

            console.log('qianguyihao 排序后的数组：' + JSON.stringify(dataList));
        </script>
    </body>
</html>
```

　　打印结果：

```
qianguyihao 排序前的数组：[
    {"title":"品牌鞋子，高品质低价入手","publishTime":200},
    {"title":"不是很贵，但是很暖","publishTime":100},
    {"title":"无法拒绝的美食，跟我一起吃吃","publishTime":300}
]

qianguyihao 排序后的数组：[
    {"title":"不是很贵，但是很暖","publishTime":100},
    {"title":"品牌鞋子，高品质低价入手","publishTime":200},
    {"title":"无法拒绝的美食，跟我一起吃吃","publishTime":300}
]
```

　　上方代码中，有人可能会问： publishTime 字段已经是 int 类型了，为啥在排序前还要做一次 parseInt() 转换？这是因为，这种数据，一般是后台接口返回给前端的，数据可能是 int 类型、也可能是字符串类型，所以还是统一先做一次 parseInt() 比较保险。这是一种良好的工作习惯。

## indexOf() 和 lastIndexOf()：获取数据的索引

　　**语法 1**：

```javascript
索引值 = 数组.indexOf(想要查询的元素);

索引值 = 数组.lastIndexOf(想要查询的元素);
```

　　备注：`indexOf()` 是从前向后查找元素的位置。同理，`lastIndexOf()`是从后向前寻找。

　　**解释**：可以检索一个数组中是否含有指定的元素。如果数组中含有该元素，则会返回其**第一次出现**的索引；如果没有找到指定的内容，则返回 -1。

　　这个方法的作用：

- **如果获取的索引值为 0，说明数组是以查询的元素为开头的**。
- 如果获取的索引值为-1，说明这个数组中没有指定的元素。

　　**注意**：`indexOf()`在检索时，是严格类型约束，类似于`===`。

　　**举例 1**：

```javascript
var arr = ['a', 'b', 'c', 'd', 'e', 'd', 'c'];

console.log(arr.indexOf('c')); //从前往后，找第一个"c"在哪个位置
console.log(arr.lastIndexOf('d')); //从后往前，找第一个"d"在哪个位置
```

　　打印结果：

```
2
5
```

　　**举例 2**：

```js
let arr = ['1', '2', '3', '4', '5'];
console.log(arr.indexOf(2));
```

　　打印结果：

```
-1
```

　　**语法 2**：

　　这个方法还可以指定第二个参数，用来指定查找的**起始位置**。语法如下：

```javascript
索引值 = 数组.indexOf(想要查询的元素, [起始位置]);
```

　　举例 3：（两个参数时，需要特别注意）

```javascript
let arr = ['q', 'i', 'a', 'n', 'g', 'u', 'y', 'i', 'h', 'a', 'o'];
result = str.indexOf('a', 3); // 从第三个位置开始查找 'a'这个元素 【重要】

console.log(result); // 打印结果：9
```

　　上方代码中，`indexOf()`方法中携带了两个参数，具体解释请看注释。

## includes()

　　**语法**：

```js
布尔值 = arr.includes(想要查找的元素, [position]);
```

　　**解释**：判断一个数组中是否包含指定的元素。如果是，则会返回 true；否则返回 false。

　　参数中的 `position`：如果不指定，则默认为0；如果指定，则规定了检索的起始位置。

```js
const arr = [11, 12, 13, 14, 15];
console.log(arr.includes(12)); // 打印结果：true
console.log(name.includes(20)); // 打印结果：false

console.log(name.includes(11, 1)); // 打印结果：false
```

## find()

　　**语法**：

```javascript
find((item, index, arr) => {
    return true;
});
```

　　**作用**：找出**第一个**满足「指定条件返回 true」的元素；如果没找到，则返回 undefined。

　　备注：一旦找到符合条件的第一个元素，将不再继续往下遍历。

　　举例：

```javascript
let arr = [2, 3, 2, 5, 7, 6];

let result = arr.find((item, index) => {
    return item > 4; //遍历数组arr，一旦发现有第一个元素大于4，就把这个元素返回
});

console.log(result); //打印结果：5
```

## findIndex()

　　**语法**：

```javascript
findIndex((item, index, arr) => {
    return true;
});
```

　　**作用**：找出**第一个**满足「指定条件返回 true」的元素的 index。

　　举例：

> 我们直接把上面的代码中的 find 方法改成 findIndex，来看看效果。
>

```javascript
let arr = [2, 3, 2, 5, 7, 6];

let result = arr.findIndex((item, index) => {
    return item > 4; //遍历数组arr，一旦发现有第一个元素大于4，就把这个元素的index返回
});

console.log(result); //打印结果：3
```

## every()

　　`every()`：对数组中每一项运行回调函数，如果都返回 true，every 就返回 true；如果有一项返回 false，则停止遍历，此方法返回 false。

　　注意：every()方法的返回值是 boolean 值，参数是回调函数。

　　举例：

```javascript
var arr1 = ['千古', '宿敌', '南山忆', '素颜'];
var bool1 = arr1.every(function (element, index, array) {
    if (element.length > 2) {
        return false;
    }
    return true;
});
console.log(bool1); //输出结果：false。只要有一个元素的长度是超过两个字符的，就返回false

var arr2 = ['千古', '宿敌', '南山', '素颜'];
var bool2 = arr2.every(function (element, index, array) {
    if (element.length > 2) {
        return false;
    }
    return true;
});
console.log(bool2); //输出结果：true。因为每个元素的长度都是两个字符。
```

## some()

　　`some()`：对数组中每一个元素运行回调函数，只要有一个元素返回 true，则停止遍历，此方法返回 true。

　　注意：some()方法的返回值是 boolean 值。

### every() 和 some() 的使用场景

　　every() 和 some() 这两个方法，初学者很容易搞混。要怎么区分呢？你可以这样记：

- every()：全部真，才为真。当你需要让数组中的每一个元素都满足指定条件时，那就使用 every()。
- some()：一个真，则为真，点到为止。数组中只要有一个元素满足指定条件时，就停止遍历。那就使用 some()。

## valueOf()：返回数组本身

```javascript
数组本身 = 数组.valueOf();
```

　　这个方法的意义不大。因为我们直接写数组对象的名字，就已经是数组本身了。

## 概念：数组的遍历

　　遍历数组即：获取并操作数组中的每一个元素，然后得到想要的返回结果。在我们的实战开发中，使用得非常频繁。

　　遍历数组的方法包括：every()、filter()、forEach()、map()等。

　　PS：这几个方法**不会修改原数组**。

　　语法格式：

```
数组/boolean/无 = 数组.every/filter/forEach/map/some(
                        function(item, index, arr){
                                        程序和返回值；
                        })
```

　　有了这几种方法，就可以替代一些 for 循环了。下面依次来介绍。

## for 循环遍历

　　举例：

```javascript
const arr = ['生命壹号', '许嵩', '永不止步'];
for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]); // arr[i]代表的是数组中的每一个元素i
}

console.log(JSON.stringify(arr));
```

　　打印结果：

```
生命壹号
许嵩
永不止步

["生命壹号","许嵩","永不止步"]
```

## forEach() 遍历

> `forEach()` 这种遍历方法只支持 IE8 以上的浏览器。IE8 及以下的浏览器均不支持该方法。所以如果需要兼容 IE8，则不要使用 forEach，改为使用 for 循环来遍历即可。
>

　　forEach()方法需要一个函数作为参数。这种函数，是由我们创建但是不由我们调用的，我们称为回调函数。

　　数组中有几个元素，该回调函数就会执行几次。

　　回调函数中传递三个参数：

- 第一个参数，就是当前正在遍历的元素
- 第二个参数，就是当前正在遍历的元素的索引
- 第三个参数，就是正在遍历的数组

　　代码举例：

```javascript
let myArr = ['王一', '王二', '王三'];

myArr.forEach((item, index, arr) => {
    console.log('item:' + item);
    console.log('index:' + index);
    console.log('arr:' + JSON.stringify(arr));
    console.log('----------');
});
```

　　打印结果：

```javascript
item:王一
index:0
arr:["王一","王二","王三"]
----------
item:王二
index:1
arr:["王一","王二","王三"]
----------
item:王三
index:2
arr:["王一","王二","王三"]
----------
```

　　注意，forEach() 没有返回值。也可以理解成：forEach() 的返回值是 undefined。如果你尝试 `tempArry = myArr.forEach()`这种方式来接收，是达不到效果的。

### forEach() 能不能改变原数组？

　　forEach() 能不能改变原数组？关于这个问题，大部分人会搞错。我们来看看下面的代码。

　　**1、数组的元素是基本数据类型**：（无法改变原数组）

```js
let numArr = [1, 2, 3];

numArr.forEach((item) => {
    item = item * 2;
});
console.log(JSON.stringify(numArr)); // 打印结果：[1, 2, 3]
```

　　上面这段代码，你可要看仔细了，打印结果是 `[1, 2, 3]`，不是 `[2, 4, 6]`。

　　**2、数组的元素是引用数据类型**：（直接修改整个元素对象时，无法改变原数组）

```js
let objArr = [
    { name: '千古壹号', age: 20 },
    { name: '许嵩', age: 30 },
];

objArr.forEach((item) => {
    item = {
        name: '邓紫棋',
        age: '29',
    };
});
console.log(JSON.stringify(objArr)); // 打印结果：[{"name":"千古壹号","age":20},{"name":"许嵩","age":30}]
```

　　**3、数组的元素是引用数据类型**：（修改元素对象里的某个属性时，可以改变原数组）

```js
let objArr = [
    { name: '千古壹号', age: 28 },
    { name: '许嵩', age: 30 },
];

objArr.forEach((item) => {
    item.name = '邓紫棋';
});
console.log(JSON.stringify(objArr)); // 打印结果：[{"name":"邓紫棋","age":28},{"name":"邓紫棋","age":30}]
```

　　如果你需要通过 forEach 修改原数组，建议用 forEach 里面的参数 2 和参数 3 来做，具体请看下面的标准做法。

　　**4、forEach() 通过参数 2、参数 3 修改原数组**：（标准做法）

```js
// 1、数组的元素是基本数据类型
let numArr = [1, 2, 3];

numArr.forEach((item, index, arr) => {
    arr[index] = arr[index] * 2;
});
console.log(JSON.stringify(numArr)); // 打印结果：[2,4,6]

// 2、数组的元素是引用数据类型时，直接修改对象
let objArr = [
    { name: '千古壹号', age: 28 },
    { name: '许嵩', age: 34 },
];

objArr.forEach((item, index, arr) => {
    arr[index] = {
        name: '小明',
        age: '10',
    };
});
console.log(JSON.stringify(objArr)); // 打印结果：[{"name":"小明","age":"10"},{"name":"小明","age":"10"}]

// 3、数组的元素是引用数据类型时，修改对象的某个属性
let objArr2 = [
    { name: '千古壹号', age: 28 },
    { name: '许嵩', age: 34 },
];

objArr2.forEach((item, index, arr) => {
    arr[index].name = '小明';
});
console.log(JSON.stringify(objArr2)); // 打印结果：[{"name":"小明","age":28},{"name":"小明","age":34}]
```

　　**总结**：

　　如果纯粹只是遍历数组，那么，可以用 forEach() 方法。但是，如果你想在遍历数组的同时，去改变数组里的元素内容，那么，最好是用 map() 方法来做，不要用 forEach()方法，避免出现一些低级错误。

　　参考链接：

- [forEach 到底可以改变原数组吗？](https://juejin.im/post/5d526a4ae51d4557dc774e7d)
- [forEach 会改变原数组值吗](https://lhajh.github.io/js/2018/05/26/Does-forEach-change-the-original-array-value.html)

## map()方法

　　语法：

```js
arr.map(function (item, index, arr) {
    return newItem;
});
```

　　解释：对数组中每一项运行回调函数，返回该函数的结果，组成的新数组（返回的是**加工之后**的新数组）。不会改变原数组。

　　作用：对数组中的每一项进行加工。

　　**举例 1**：（拷贝的过程中改变数组元素的值）

　　有一个已知的数组 arr1，我要求让 arr1 中的每个元素的值都加 10，这里就可以用到 map 方法。代码举例：

```javascript
var arr1 = [1, 3, 6, 2, 5, 6];

var arr2 = arr1.map(function (item, index) {
    return item + 10; //让arr1中的每个元素加10
});
console.log(arr2);
```

　　打印结果：

　　![](http://img.smyhvae.com/20180402_0938.png)

　　**举例 2**：【重要案例，实际开发中经常用到】

　　将 A 数组中某个属性的值，存储到 B 数组中。代码举例：

```javascript
const arr1 = [
    { name: '千古壹号', age: '28' },
    { name: '许嵩', age: '32' },
];

// 将数组 arr1 中的 name 属性，存储到 数组 arr2 中
const arr2 = arr1.map((item) => item.name);

// 将数组 arr1 中的 name、age这两个属性，改一下“键”的名字，存储到 arr3中
const arr3 = arr1.map((item) => ({
    myName: item.name,
    myAge: item.age,
})); // 将数组 arr1 中的 name 属性，存储到 数组 arr2 中

console.log('arr1:' + JSON.stringify(arr1));
console.log('arr2:' + JSON.stringify(arr2));
console.log('arr3:' + JSON.stringify(arr3));
```

　　打印结果：

```
arr1:[{"name":"千古壹号","age":"28"},{"name":"许嵩","age":"32"}]

arr2:["千古壹号","许嵩"]

arr3:[{"myName":"千古壹号","myAge":"28"},{"myName":"许嵩","myAge":"32"}]

```

　　map 的应用场景，主要就是以上两种。

### 注意：map() 方法真的不会改变原数组吗？

　　答案：不一定。

　　举例：

```javascript
      const arr = [
        {
          name: "qianguyihao1",
          age: 22,
        },
        {
          name: "qianguyihao2",
          age: 23,
        },
      ];

      arr.map((item) => {
        item.name = "haha"; // 修改 item 里的某个属性
        return item;
      });
      console.log(JSON.stringify(arr));
```

　　打印结果：

```
[{"name":"haha","age":22},{"name":"haha","age":23}]
```

　　总结：map方法如果是修改整个item的值，则不会改变原数组。但如果是修改 item 里面的某个属性，那就会改变原数组。

##  filter()

　　语法：

```js
arr.filter(function (item, index, arr) {
    return true;
});
```

　　解释：对数组中的**每一项**运行回调函数，该函数返回结果是 true 的项，将组成新的数组（返回值就是这个新的数组）。不会改变原数组。

　　作用：对数组进行过滤。

　　**举例 1**：找出数组 arr1 中大于 4 的元素，返回一个新的数组。代码如下：

```javascript
let arr1 = [1, 3, 6, 2, 5, 6];

let arr2 = arr1.filter((item) => {
    if (item > 4) {
        return true; // 将arr1中大于4的元素返回，组成新的数组
    }
    return false;
});

console.log(JSON.stringify(arr1)); // 打印结果：[1,3,6,2,5,6]
console.log(JSON.stringify(arr2)); // 打印结果：[6,5,6]
```

　　上方代码更简洁的写法如下：

```javascript
let arr1 = [1, 3, 6, 2, 5, 6];

let arr2 = arr1.filter((item) => item > 4); // 将arr1中大于4的元素返回，组成新的数组

console.log(JSON.stringify(arr1)); // 打印结果：[1,3,6,2,5,6]
console.log(JSON.stringify(arr2)); // 打印结果：[6,5,6]
```

　　**举例 2**：

　　获取数组 A 中指定类型的对象，放到数组 B 中。代码举例如下：

```javascript
const arr1 = [
    { name: '许嵩', type: '一线' },
    { name: '周杰伦', type: '过气' },
    { name: '邓紫棋', type: '一线' },
];

const arr2 = arr1.filter((item) => item.type == '一线'); // 筛选出一线歌手

console.log(JSON.stringify(arr2));
```

　　打印结果：

```javascript
[
    { name: '许嵩', type: '一线' },
    { name: '邓紫棋', type: '一线' },
];
```

## reduce()方法

### reduce() 语法

> reduce 的发音：[rɪ'djuːs]。中文含义是减少，但这个方法跟“减少”没有任何关系。
>

　　reduce() 方法接收一个函数作为累加器，数组中的每个值（从左到右）开始缩减，最终计算为一个值。返回值是回调函数累计处理的结果。

　　**语法**：

```javascript
arr.reduce(function (previousValue, currentValue, currentIndex, arr) {}, initialValue);
```

　　参数解释：

- previousValue：必填，上一次调用回调函数时的返回值
- currentValue：必填，当前正在处理的数组元素
- currentIndex：选填，当前正在处理的数组元素下标
- arr：选填，调用 reduce()方法的数组
- initialValue：选填，可选的初始值（作为第一次调用回调函数时传给 previousValue 的值）

　　在以往的数组方法中，匿名的回调函数里是传三个参数：item、index、arr。但是在 reduce() 方法中，前面多传了一个参数`previousValue`，这个参数的意思是上一次调用回调函数时的返回值。第一次执行回调函数时，previousValue 没有值怎么办？可以用 initialValue 参数传给它。

　　备注：绝大多数人在一开始接触 reduce() 的时候会很懵逼，但是没关系，有事没事多看几遍，自然就掌握了。如果能熟练使用 reduce() 的用法，将能替代很多其他的数组方法，并逐渐走上进阶之路，领先于他人。

　　为了方便理解 reduce()，我们先来看看下面的简单代码，过渡一下：

```js
let arr1 = [1, 2, 3, 4, 5, 6];

arr1.reduce((prev, item) => {
    console.log(prev);
    console.log(item);
    console.log('------');
    return 88;
}, 0);
```

　　打印结果：

```
0
1
------
88
2
------
88
3
------
88
4
------
88
5
------
88
6
------
```

　　上面的代码中，由于`return`的是固定值，所以 prev 打印的也是固定值（只有初始值是 0，剩下的遍历中，都是打印 88）。

　　现在来升级一下，实际开发中，prev 的值往往是动态变化的，这便是 reduce()的精妙之处。我们来看几个例子就明白了。

### reduce() 的常见应用

　　**举例 1**、求和：

　　计算数组中所有元素项的总和。代码实现：

```javascript
const arr = [2, 0, 1, 9, 6];
// 数组求和
const total = arr.reduce((prev, item) => {
    return prev + item;
});

console.log('total:' + total); // 打印结果：18
```

　　**举例 2**、统计某个元素出现的次数：

　　代码实现：

```js
// 定义方法：统一 value 这个元素在数组 arr 中出现的次数
function repeatCount(arr, value) {
    if (!arr || arr.length == 0) return 0;

    return arr.reduce((totalCount, item) => {
        totalCount += item == value ? 1 : 0;
        return totalCount;
    }, 0);
}

let arr1 = [1, 2, 6, 5, 6, 1, 6];

console.log(repeatCount(arr1, 6)); // 打印结果：3
```

　　**举例 3**、求元素的最大值：

　　代码实现：

```js
const arr = [2, 0, 1, 9, 6];
// 数组求最大值
const maxValue = arr.reduce((prev, item) => {
    return prev > item ? prev : item;
});

console.log(maxValue); // 打印结果：9
```

　　参考链接：

- [JS reduce 函数](https://juejin.im/post/5d78aa3451882521397645ae)

## 数组练习

### splice()练习：数组去重

　　代码实现：

```javascript
//创建一个数组
var arr = [1, 2, 3, 2, 2, 1, 3, 4, 2, 5];

//去除数组中重复的数字
//获取数组中的每一个元素
for (var i = 0; i < arr.length; i++) {
    //console.log(arr[i]);
    /*获取当前元素后的所有元素*/
    for (var j = i + 1; j < arr.length; j++) {
        //console.log("---->"+arr[j]);
        //判断两个元素的值是否相等
        if (arr[i] == arr[j]) {
            //如果相等则证明出现了重复的元素，则删除j对应的元素
            arr.splice(j, 1);
            //当删除了当前j所在的元素以后，后边的元素会自动补位
            //此时将不会在比较这个元素，我需要再比较一次j所在位置的元素
            //使j自减
            j--;
        }
    }
}

console.log(arr);
```

### 清空数组

　　清空数组，有以下几种方式：

```javascript
var array = [1, 2, 3, 4, 5, 6];

array.splice(0); //方式1：删除数组中所有项目
array.length = 0; //方式2：length属性可以赋值，在其它语言中length是只读
array = []; //方式3：推荐
```

### join() 练习

　　**问题**：将一个字符串数组输出为`|`分割的形式，比如“千古|宿敌|素颜”。使用两种方式实现。

　　答案：

　　方式 1：（不推荐）

```javascript
var arr = ['千古', '宿敌', '素颜'];
var str = arr[0];
var separator = '|';
for (var i = 1; i < arr.length; i++) {
    str += separator + arr[i]; //从第1个数组元素开始，每个元素前面加上符号"|"
}

console.log(str);
```

　　输出结果：

　　![](http://img.smyhvae.com/20180126_1336.png)

　　不推荐这种方式，因为：由于字符串的不变性，str 拼接过多的话，容易导致内存溢出（很多个 str 都堆放在栈里）。

　　方式 2：（推荐。通过 array 数组自带的 api 来实现）

```javascript
var arr = ['千古', '宿敌', '素颜'];

console.log(arr.join('|'));
```

　　结果：

　　![](http://img.smyhvae.com/20180126_1339.png)

### reverse() 练习

　　题目：将一个字符串数组的元素的顺序进行反转，使用两种种方式实现。提示：第 i 个和第 length-i-1 个进行交换。

　　答案：

　　方式 1：

```javascript
function reverse(array) {
    var newArr = [];
    for (var i = array.length - 1; i >= 0; i--) {
        newArr[newArr.length] = array[i];
    }
    return newArr;
}
```

　　方式 2：（算法里比较常见的方式）

```javascript
function reverse(array) {
    for (var i = 0; i < array.length / 2; i++) {
        var temp = array[i];
        array[i] = array[array.length - 1 - i];
        array[array.length - 1 - i] = temp;
    }
    return array;
}
```

　　方式 3：（数组自带的 reverse 方法）

　　现在我们学习了数组自带的 api，我们就可以直接使用 reverse()方法。

### 练习

　　问题：找到数组["c","a","z","a","x","a"]中每一个元素出现的次数。

　　分析：这道题建议用 json 数据来做，因为我们想知道 a 出现了几次，c 出现了几次，x 出现了几次。恰好`k:v .. k:v`这种键值对的形式就比数组方便很多了。

　　键值对的形式：用 key 代表数组中的元素，用 value 代表元素出现的次数。

　　略难，答案暂略。

### 练习：数组去重

　　问题：编写一个方法去掉一个数组中的重复元素。

　　分析：创建一个新数组，循环遍历，只要新数组中有老数组的值，就不用再添加了。

　　答案：

```javascript
//    编写一个方法 去掉一个数组的重复元素
var arr = [1, 2, 3, 4, 5, 2, 3, 4];
console.log(arr);
var aaa = fn(arr);
console.log(aaa);
//思路：创建一个新数组，循环遍历，只要新数组中有老数组的值，就不用再添加了。
function fn(array) {
    var newArr = [];
    for (var i = 0; i < array.length; i++) {
        //开闭原则
        var bool = true;
        //每次都要判断新数组中是否有旧数组中的值。
        for (var j = 0; j < newArr.length; j++) {
            if (array[i] === newArr[j]) {
                bool = false;
            }
        }
        if (bool) {
            newArr[newArr.length] = array[i];
        }
    }
    return newArr;
}
```

　　

　　
