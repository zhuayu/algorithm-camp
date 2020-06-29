# 哈希表、映射、集合的实现与特性

日常数据结构除了数组、链表外，用得比较多的就是 map、set 。它们的底层结构使用哈希表来实现。
哈希表（ Hash table ），也叫离散表，是根据关联码（ key value ）而直接进行访问的数据结构。它通过把关键码映射到表中一个位置来访问记录，以加快查找的速度。这个映射函数叫做散列函数（ Hash Function），存放记录的数组叫哈希表（或散列表）。

- Map：key-value 对，key 不重复 Java Map 文档
- Set：不重复元素的集合 Java Set 文档

## JavaScript Map

Map 对象保存键值对，并且能够记住键的原始插入顺序。任何值(对象或者原始值) 都可以作为一个键或一个值。

```javascript
let myMap = new Map();
 
let keyObj = {};
let keyFunc = function() {};
let keyString = 'a string';
 
// 添加键
myMap.set(keyString, "和键'a string'关联的值");
myMap.set(keyObj, "和键keyObj关联的值");
myMap.set(keyFunc, "和键keyFunc关联的值");
 
myMap.size; // 3
 
// 读取值
myMap.get(keyString);    // "和键'a string'关联的值"
myMap.get(keyObj);       // "和键keyObj关联的值"
myMap.get(keyFunc);      // "和键keyFunc关联的值"
 
myMap.get('a string');   // "和键'a string'关联的值"
                         // 因为keyString === 'a string'
myMap.get({});           // undefined, 因为keyObj !== {}
myMap.get(function() {}); // undefined, 因为keyFunc !== function () {}
```

## JavaScript Set
Set 对象允许你存储任何类型的唯一值，无论是原始值或者是对象引用。

```javascript
let mySet = new Set();

mySet.add(1); // Set [ 1 ]
mySet.add(5); // Set [ 1, 5 ]
mySet.add(5); // Set [ 1, 5 ]
mySet.add("some text"); // Set [ 1, 5, "some text" ]
let o = {a: 1, b: 2};
mySet.add(o);

mySet.add({a: 1, b: 2}); // o 指向的是不同的对象，所以没问题

mySet.has(1); // true
mySet.has(3); // false
mySet.has(5);              // true
mySet.has(Math.sqrt(25));  // true
mySet.has("Some Text".toLowerCase()); // true
mySet.has(o); // true

mySet.size; // 5

mySet.delete(5);  // true,  从set中移除5
mySet.has(5);     // false, 5已经被移除

mySet.size; // 4, 刚刚移除一个值
console.log(mySet); // Set {1, "some text", Object {a: 1, b: 2}, Object {a: 1, b: 2}}
```
