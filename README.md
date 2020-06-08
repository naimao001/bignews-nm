# bignews-nm
## horse 远biss
### 注意点
  - 所有接口带token
    + 原生js 是xhr.setRequestHeader("Authorization","token的值")
    + jq是header:{"Authorization","token的值"}
    + jq js文件里 $.ajaxSetup({beforeSend(xhr){xhr.setRequestHeader("Authorization","token的值")}})

  - 原生DOM对象的click()方法与jq对象click()方法的区别
     + 原生DOM对象的click()方法 ： 触发该对象的`默认行为` + `点击事件`
     + jq对象的click()方法 ： 只触发该对象的`点击事件`

###  jQ的serialize方法

作用: 也是可以把form表单里面带有name属性的标签的值一次性取出来,

​          取出来的值是这样:  key=value&key2=value2 这种格式的字符串.

和FormData的区别:

​	1.FormData是原生js就有的,jQuery他也封装了,可以用 ;   serialize()是jQuery提供的方法.

​	2.FormData对象需要创建,传入是form表单dom对象,      serialize()直接是form表单jQuery对象调用

​	3.FormData不需要设置请求头.

​	4.FormData传递过去的是一个formData对象,  而serialize()传过去的是一个字符串.

​	5.FormData可以传递文件, 但是serialize()不行.

### jq分页插件

 - 发现问题
    +   a. loadPagination(22,1)在加载的时候会默认执行一次 点击第一页的事件
    +   b. 点击第一页事件处理函数会调用  getArticleList(1)
    +   c. getArticleList(1)中ajax回调函数会调用 loadPagination(22,1)
    +   d. 两个函数之间会形成递归调用
 - 分析问题
    +  递归一定要有结束条件，否则会形成死循环
 - 解决问题
    +  方案一：给递归添加结束条件判断当前页与点击页是否相等，只有不等才调用  getArticleList()
    +  方案二：给getArticleList()额外添加一个布尔类型参数，只有点击筛选才会重新加载分页插件

### iframe嵌套页面时 子页面给父页面的dom添加事件
  - 技术点：$() jq选择器的第二个参数其实是document文档，一般不写默认就是当前页面的document。如果希望找到父window的元素，则可以添加第二个参数

 -  官方文档传送门：http://jquery.cuishifeng.cn/jQuery_selector_context.html
      
