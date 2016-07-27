```js
<script type="text/javascript">
  var count1 = 0;

  function Bubble1(arr) {
    for (var j = arr.length; j > 1; j--) {
      //在每一次内部循环前设置一个标记位，如果该标记位在内部循环中没有被修改过，说明这一趟内部循环之前已经是排序好的了，程序可以立即结束退出。
      var flag = true;
      for (var i = 0; i < j - 1; i++) {
        if (arr[i] > arr[i + 1]) {
          arr[i] = [arr[i + 1], arr[i + 1] = arr[i]][0];
          flag = false;
        }
        count1++;
      }
      if (flag) {
        return arr;
      }
    }
    return arr;
  }

  var count2 = 0;

  function Bubble2(arr) {
    for (var j = arr.length; j > 1; j--) {
      var k = [];
      for (var i = 0; i < j - 1; i++) {
        if (arr[i] > arr[i + 1]) {
          arr[i] = [arr[i + 1], arr[i + 1] = arr[i]][0];
          //flag=false;
          k.push(1);
        } else {
          k.push(0);
        }
        count2++;
      }
      j = k.lastIndexOf(1) + 2;
    }
    return arr;

    var count3 = 0;

    function Bubble3(arr) {
      for (var j = arr.length; j > 1; j--) {
        for (var i = 0; i < j - 1; i++) {
          if (arr[i] > arr[i + 1]) {
            arr[i] = [arr[i + 1], arr[i + 1] = arr[i]][0];
          }
          count3++;
        }
      }
      return arr;
    }
  }
</script>
```