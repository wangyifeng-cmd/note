# ajax笔记

### get方法

```js
$.get('./ajax.json', function(data, status) {
	//console.log(index);
})
```



### load方法

```js
$(document).ready(function() {
     $("#div1").load("1.htm", function(responseTxt, statusTxt, xhr) {
          if (statusTxt == "success")
               alert("外部内容加载成功! ");
          if (statusTxt == "error")
               alert("Error: " + xhr.status + " : " + xhr.statusText);
     });
});
```

