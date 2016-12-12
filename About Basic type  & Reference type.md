## 关于`基本数据类型`和`引用数据类型`的赋值问题  

```js  

<script>

 var obj = {person:{
        name:'小明'
      }}

      var tmp = obj.person//{name:'小明'}

      tmp.name = '小红'//｛　name:'小红'}
      //（tmp.name = obj.person.name = '小红'）
     
      var mm = {name:'小天'}
      var tmp = mm//{name:'小天'}

      console.log(tmp.name)//{name:'小天'}

      // tmp.name = mm.name = '小天'
     

      console.log(obj.person.name)//小红
      
      console.log(mm.name)//小天

</script>
```