## 1. 接口描述
 
本接口(DescribeAddressGroups)用于查询(网络)参数模板IP地址组列表。
接口请求域名：<font style="color:red">vpc.api.qcloud.com</font>
 

## 2. 输入参数
 
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见公共请求参数页面。其中，此接口的Action字段为DescribeAddressGroups。
<table class="t"><tbody><tr>
<th><b>参数名称</b></th>
<th><b>必选</b></th>
<th><b>类型</b></th>
<th><b>描述</b></th>
<tr>
<td> addressGroupId <td> 否 <td> String <td> IP地址组ID，支持模糊搜索
<tr>
<td> addressGroupName <td> 否 <td> String <td> IP地址组名称，支持模糊搜索
<tr>
<td> offset <td> 否 <td> Int <td> 初始行的偏移量，默认为0。
<tr>
<td> limit <td> 否 <td> Int <td> 每页行数，默认为20。
</tbody></table>

注：addressGroupId 和 addressGroupName 作为查询条件为逻辑与关系

## 3. 输出参数
 

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code |  Int | 错误码, 0: 成功, 其他值: 失败 |
| message |   String | 错误信息 |
| codeDesc |   String | 英文错误码 |
| data |   Object |返回的数据结构 |

data 结构

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| data.totalCount |   Int | 返回的 IP 地址组总数 |
| data.data |   Array | IP地址组详情列表|

data.data 结构
<table class="t"><tbody><tr>
<th><b>参数名称</b></th>
<th><b>类型</b></th>
<th><b>描述</b></th>
<tr>
<td> data.data.n.addressGroupId <td> String <td> IP地址组ID
<tr>
<td> data.data.n.addressGroupName <td> String <td> IP地址组名称
<tr>
<td> data.data.n.addressGroup <td> Array <td> IP地址组成员
<tr>
<td> data.data.n.createTime <td> String <td> 创建时间
</tbody></table>

data.data.n.addressGroup结构
<table class="t"><tbody><tr>
<th><b>参数名称</b></th>
<th><b>类型</b></th>
<th><b>描述</b></th>
<tr>
<td> data.data.n.addressGroup.n <td> String <td> IP地址组成员
</tbody></table>

 ## 4. 错误码表
 <table class="t"><tbody><tr>
<th><b>错误码数值</b></th>
<th><b>原因</b></th>
<tr>
<td> 29257 <td> 后台错误，请求失败
<tr>
<td> 29258 <td> 引用资源不存在
<tr>
<td> 29259 <td> 关联对象因规则展开过大拒绝您的关联
<tr>
<td> 29260 <td> 参数模板总数或成员数使用超限
<tr>
<td> 29254 <td> 鉴权失败
<tr>
<td> 9003 <td> 参数错误
<tr>
<td> 9005 <td> 系统忙或有相关资源正在被编辑
</tbody></table>


## 5. 示例
 
输入
<pre>

  https://vpc.api.qcloud.com/v2/index.php?Action=DescribeAddressGroups
  &<<a href="https://www.qcloud.com/doc/api/229/6976">公共请求参数</a>>
  &addressGroupId=q

</pre>

输出
```
{
    "code": 0,
    "message": "",
	"codeDesc": "Success",
    "data": {
        "totalCount": 2,
        "data": [
            {
                "addressGroupId": "ipmg-8sasuc8q",
                "addressGroupName": "ddd",
                "addressGroup": [
                    {
                        "addressId": "ipm-kj9sucnx",
                        "addressName": "test1"
                    }
                ],
                "createTime": "2017-06-07 19:39:05"
            },
            {
                "addressGroupId": "ipmg-n28suc8q",
                "addressGroupName": "aaaabbb",
                "addressGroup": [
                    {
                        "addressId": "ipm-kj9sucnx",
                        "addressName": "test2"
                    }
                ],
                "createTime": "2017-06-07 17:33:54"
            }
        ]
    }
}
```

