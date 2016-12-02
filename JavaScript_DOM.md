1. 监听鼠标点击事件所在区域

    ```javascript
    document.onclick = function(e) {
        obj = $(e.srcElement || e.target);
        console.log(obj[0]);
    }
    ```

2. 获取选择框所选中的项

    ```javascript
    function getSelectVal(id){
        var select = document.getElementById(id);
        var value = select.options[select.options.selectedIndex].value;
        return value;
    }
    ```

3. 停止事件传播

    ```html
    <div onclick="event.stopPropagation()"></div>
    ```
    ```js
    document.querySelector('div').onclick = function (e) {
        e.stopPropagation();
    }
    ```
