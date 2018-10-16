3. 布尔类型

   ```javascript
   var g = true;
   var h = new Boolean(false);
   ```

4. 数组

   ```javascript
   var i = [1,2,3];
   var j = new Array();
   var k = new Array(1,2,3,4);
   ```

5. 对象

   ```javascript
   var person = new Object;
   person.id = 1001;
   person.name="jack";
   person.eat = new function(){
       alert("eat.....");
   }
   alert(person.id);
   ```

Select下拉框onchange事件获取option的value值

```html
<select name="type" onchange="show_sub(this.options[this.options.selectedIndex].value)">    
    <option value="0">请选择主菜名</option>    
    <option value="1">白菜</option>    
    <option value="2">萝卜</option>    
 </select> 
```

js代码

```javascript
<script>     
    function show_sub(v){     
        alert(v);     
    }     
</script>  
```

最重要的知识点是获在select onchange时获取option的value值：

```html
this.options[this.options.selectedIndex].value
```

