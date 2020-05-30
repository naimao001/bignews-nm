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