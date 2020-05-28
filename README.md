# bignews-nm
## horse 远biss
### 注意点
  - 所有接口带token
    + 原生js 是xhr.setRequestHeader("Authorization","token的值")
    + jq是header:{"Authorization","token的值"}
    + jq js文件里 $.ajaxSetup({beforeSend(xhr){xhr.setRequestHeader("Authorization","token的值")}})