"# YixiWangCarol.github.io" 

1.String algorithms
## 1.把字符串变成【字符数组】，如“abc”变成数组[’a’,’b’,’c’]

/github

方法1：

```jsx
let a = "abc";
let b = [...a];
console.log(b);//输出结果为： ['a','b','c']
```

方法2：

```jsx
let b = a.split("")
console.log(b)//输出结果为： ['a','b','c']
```

<aside>
💡 **`split()`** 方法接受一个模式，通过搜索模式将[字符串](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String)分割成一个有序的子串列表，将这些子串放入一个数组，并返回该数组。

</aside>

[String.prototype.split() - JavaScript | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/split)

## 2.reduce Array.prototype.reduce()

1**.展平**嵌套数组：

用到的有：reduce 和 concat

**`concat()`** 方法用于合并两个或多个数组。此方法不会更改现有数组，而是返回一个新数组。

```jsx
const flattened = [
  [0, 1],
  [2, 3],
  [4, 5],
].reduce((accumulator, currentValue) => accumulator.concat(currentValue), []);
// flattened 的值是 [0, 1, 2, 3, 4, 5]
```

<aside>
💡 一开始的想法是用展开syntax→ ...   但是发现不行，因为一个二维数组，用…展开只能展开一层,如图所示

</aside>

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/54e8e0c4-06cb-4d99-b959-b98f313499fb/372c188a-c0f6-496c-a6be-82f13c2f98e3/Untitled.png)

2**.统计对象中值的出现次数**

方法1：

```jsx
const names = ["Carol","Betty","Alice","Betty","Mike"]

const nameCount = names.reduce((allNames,name)=>{
	let count = allNames[name] ?? 0
	return{
		...allNames,
		[name] : count+1
	}
},{})

console.log(nameCount)

//{ Carol: 1, Betty: 2, Alice: 1, Mike: 1 }
```

方法2：

```jsx
const names = ["Carol","Betty","Alice","Betty","Mike"]

const nameCount = names.reduce((allNames,name)=>{
	allNames[name]? allNames[name]++  : ( allNames[name]=1)//注意这里是 "allNames[name]=1" 而不是直接是1
    return allNames
},{})

console.log(nameCount)
```

<aside>
💡 注意：这里初始传递了一个{}，object，所以才能有allNames[name]这种形式

</aside>

## 3.sort 进行排序 Array.prototype.sort()

sort就地对数组排序 默认是把元素转换成字符串，然后按照UTF-16码元值升序排序

问题1：有一句英文，把每个单词按照字母顺序从小到大排序，返回新的句子

```jsx
const a ="this is a room not a abc"
let b = a.split(" ")
let c = b.map(e=>[...e].sort().join(""))

console.log(c.join(" ")) //hist is a moor not a abc
```

如果按照ASCII码降序排序，则
