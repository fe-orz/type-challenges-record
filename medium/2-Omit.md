# 2-Omit

## 1.结合JavaScript思考

如何获取Object的key呢，在JavaScript中，我们有Object.keys()方法

那在typescript中，获取key我们可以使用keyof关键字

eg: 

```typescript
interface Jiuran {
  a : string,
  b : number
}

// 获取key

type keys = keyof Jiuran
```

## 2.遍历对象

javascript: 
```javascript
forEach , map, for(let i = 0 ; i < 5; i++)
```

可以遍历union
```
type nor = '1' | '2' | '3'
```

typescript: 
```typescript
[p in keyof obj]
```

## 3.Key Remapping in Mapped Types (使用as进行类型重映射)

docs: [遍历时类型重映射] --> https://www.typescriptlang.org/docs/handbook/release-notes/typescript-4-1.html#key-remapping-in-mapped-types

[p in keyof obj + 条件判断]

## 4.答案
```typescript
type MyOmit<T, K> = { [P in keyof T as P extends K ? never : P]: T[P] };
```
