Jq bind data to form   


Read data from net , ,,werite to ui

// 使用选择器来批量绑定数据
$.each(data, function(key, value) {
  $('#myForm [name="' + key + '"]').val(value);
});
 

上述代码中，我们首先定义了一个包含表单元素的HTML结构，并准备了一个包含数据的对象。然后使用 .each() 方法遍历数据对象，通过选择器来选取相应的表单元素，并使用 .val() 方法来设置元素的值。
-----------------------------------
©著作权归作者所有：来自51CTO博客作者mob649e8166858d的原创作品，请联系作者获取转载授权，否则将追究法律责任
jquery 表单批量绑定数据
https://blog.51cto.com/u_16175509/7440346
