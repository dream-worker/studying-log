## 关于函数的返回值  

```js  
<script>
//  1. 函数没有返回值，返回值默认为undefined
                var module = {}
                function haha(module){
                    module.name = '小明'
                
                   }

               var a =  haha(module)// a =undefined
             
               //haha这个函数没有返回值，所以haha(module)调用后 = undefined。即： a = undefined 
               

// 2. 函数有返回值。不论运算结果是什么，调用后得到的结果只能是return的返回值

                var module = {}
                function haha(module){
                    module.name = '小明'
                    return '小华'
                   }

               var a =  haha(module)// a = '小华'

//3. 综合练习

              function getData(){
                var module = {}
                function haha(module){
                    module.name = '小明'
                    return '小华'
                   }

               var a =  haha(module)
               if(a==undefined){
                return module
               }else{
                return a
              }
        }

      var result =   getData()
      console.log(result)// '小华'

      
      // haha这个函数有返回值，所以执行else的代码，返回a。
      // 而a得到的结果是return的返回值'小华'
      // 
      // 
      // 如果没有return '小华',执行if的代码，返回值为{name:'小明'}

</script>
```