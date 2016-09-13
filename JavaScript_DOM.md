1. document.onclick = function(e) {obj = $(e.srcElement || e.target);console.log(obj[0])}
    监听鼠标点击事件所在区域

2. 获取选择框所选中的项
function getSelectVal(id){
    var select = document.getElementById(id);
    var value = select.options[select.options.selectedIndex].value;
    return value;
}
