# Symbol 

## JavaScript数据类型之一，是原始类型，因为不能用`new Symbol()`创建
> JavaScript七种原始类型: null、undefind、boolean、number、string、bigint、symbol
> 一种引用类型：object



## 声明symbol值： Symbol([description])，支持一个可选参数，参数可以是除Symbol值以外任意类型的值。就是给symbol起一个名字。
```
const s1 = Symbol()  
const s2 = Symbol("id")  //s2的描述为“id”
const s4 = Symbol("id")  //s4的描述也为“id”，但是名字相同，但是值不同  

const s1 = Symbol()
console.log(s1)
const s2 = Symbol(42)
console.log(s2)
const s3 = Symbol("42")
console.log(s3)
const s4 = Symbol(false)
console.log(s4)
const s5 = Symbol({name:'sym'})
console.log(s5)
const s6 = Symbol(null)
console.log(s6)
const s7 = Symbol(undefined)
console.log(s7)
const s8 = Symbol(1234567890123456789012345678901234567890n)
console.log(s8)
const s9 = Symbol(Symbol())  //TypeError
console.log(s9)

```


## 对象的属性除了用字符串作为属性名，还可以用symbol值，好处是标识符之间不会冲突。
```
const id = Symbol('id')
const obj = {
    name: '张三',
    age: 19,
    [id]: 66666
}
obj[id] = 8888888
obj[Symbol()] = "笑嘻嘻"
console.log(obj)
console.log(obj[id])
```

## symbol 属性不能通过Object.keys()或者for...in来枚举的
```
const age = Symbol('age')
let user = {
    name: '小红',
    sex: '女',
    [age]: 18
}
for( item in user){
    console.log(item)  //user 、  sex
}

```

## Object.assign() 会同时复制字符串和 symbol 属性
```
 let user = {
        name: '小红',
        sex: '女',
        [age]: 18
    }
    
    let clone = Object.assign({},user)
    console.log('clone',clone)

```





## Symbol.for(key) 方法会根据给定的键 key，从运行时的 symbol 注册表中找到对应的 symbol，如果找到了，则返回它，否则，新建一个与该键关联的 symbol，并放入全局 symbol 注册表中。
```
//从全局注册表中读取
const sym1 = Symbol.for('张')  // 如果该 symbol 不存在，则创建它
const sym2 = Symbol.for('张')  //再次读取（可能是在代码中的另一个位置）
console.log(sym1 === sym2) // 相同的 symbol
```

## Symbol.for(key) 按名字返回一个 symbol。Symbol.keyFor(sym)根据全局symbol返回名字
```
let sym = Symbol.for("name");
let sym2 = Symbol.for("id");

// 通过 symbol 获取 name
console.log(Symbol.keyFor(sym)); // name
console.log(Symbol.keyFor(sym2)); // id
}

```

