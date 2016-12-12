# 关于对象  

## 声明一个空对象，进行以下操作：  

```js 
<script>

// 1.打印一个空对象
     var b = {}
   console.log(b)
 //得到的结果是一个空的对象。
 //里面只有一个指向原型的属性
   // {
   // 	__.p__proto: Object
   // }


  //2. 对空对象设置属性
   var module ={}
   module.name = '小明'
   var a = module.name



   console.log(a)// 小明（打印属性值）

   console.log(module)// {name:'小明'}（打印对象）

</script> 
```