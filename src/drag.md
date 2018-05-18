写出一个可以在页面上随意拖动的圆形div。
ex：

### answer

``` js

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Drag</title>
</head>
<style>
  body, html {
    width: 100%;
    height: 100%;
  }
  * {
    margin: 0;
    padding: 0;
  }
  #drag {
    width: 100px;
    height: 100px;
    border-radius: 100%;
    background-color: pink;
    position: relative;
  }
</style>
<body>
  <div id="drag"></div>
  
</body>
<script>
  var params = {
    left: 0,
    top: 0,
    currentX: 0,
    currentY: 0,
    flag: false,
  };
  
  var dragEle = document.getElementById('drag');
  
  dragEle.addEventListener('mousedown', function(e) {
    console.log(dragEle.style)
    params.currentX = e.clientX;
    params.currentY = e.clientY;
    params.flag = true;
  }, false)
  document.addEventListener('mousemove', function(e) {
    if(params.flag) {
      var maxTop = document.documentElement.clientHeight - dragEle.offsetHeight;
      var maxLeft = document.documentElement.clientWidth - dragEle.offsetWidth;
      var currentX = e.clientX, currentY = e.clientY;
      var moveX = currentX - params.currentX, moveY = currentY - params.currentY;
      var targetX = parseInt(params.left) + moveX > maxLeft ? maxLeft : parseInt(params.left) + moveX;
      var targetY = parseInt(params.top) + moveY > maxTop ? maxTop : parseInt(params.top) + moveY;
      console.log(maxLeft, targetX)
      targetX = targetX > 0 ? targetX : 0;
      targetY = targetY > 0 ? targetY : 0;
      dragEle.style.left = targetX + 'px';
      dragEle.style.top = targetY + 'px';
      e.preventDefault();
      return false;
    }
  }, false)
  document.addEventListener('mouseup', function(e) {
    params.flag = false;
  }, false)
</script>
</html>

```
