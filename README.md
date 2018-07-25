#### 简要描述：

- 仓储管理员查看可能需要拣货退库或已经退库的申领单
- 用户：各仓储的仓储管理员
- 权限：仓储管理员只能查看自己的所属仓储的拣货退库信息

#### 接口版本：

|版本号|制定人|制定日期|修订日期|
|:----    |:---|:----- |-----   |
|0.0.1 |吴俊  |2018-07-24 |  2018-07-24  |

#### 请求URL:

- http://10.0.0.65:8080/esms/ws/webApplyWs/list

#### 请求方式：

- POST

#### 请求头：

|参数名|是否必须|类型|说明|
|:----    |:---|:----- |-----   |
|Content-Type |是  |string |请求类型： application/json   |
|Authorization |是  |string | 服务器签发的Token    |
|ResourceId |是  |string | 菜单编号(SYS_MENU表的RESOURCE_NAME字段)    |


#### 请求参数说明:

|参数名|是否必须|类型|说明|
|:----    |:---|:----- |-----   |
|apply_code |否  |string | APPLY_DOC_CODE  |
|project_code |否  |string | 项目编码    |
|project_name |否  |string | 项目名称    |
|apply_unit |否  |string | 申请单位    |
|receiver |否  |string | 接收人    |
|status |否  |string | 状态    |
|start_date |否  |string | 查询起始日期    |
|end_date |否  |string | 查询结束日期    |
|warehouse_id |是  |string | 仓库id    |
|user_id |是  |string | 登录用户id    |
|no_page |是  |Int | 请求页码（从1开始）    |
|isSue |是  |Int | 是否为出库(0：出库 1：退库)    |
#### 请求参数示例:
```
{
	"apply_code": null,
	"project_code": null,
	"project_name": null,
	"apply_unit": null,
	"receiver": null,
	"status": null,
	"start_date": null,
	"end_date": null,
	"warehouse_id": "A111",
	"user_id": "rfid",
	"no_page": 1,
	"isSue": 0
}
```

#### 返回示例:

**正确时返回:**

```
{
  "success": true,
  "msg": "操作成功",
  "data": {
    "page_num": "30",
    "apply_list": [{
      "reserve_code": "",
      "apply_code": "AUTO-APPLY-20180420-5607",
      "apply_date": "2018-04-20 04:19:09",
      "apply_unit": "郑州分公司\\网络部\\全业务支撑中心",
      "apply_person": "李守捷",
      "receiver": "郭辉15939040774",
      "project_code": "B1700001",
      "project_name": "郑州17家客一期（一）",
      "remark": "",
	  "callbackDate":"退库操作时间",
	  "callBackStaff":"退库操作人"
    }]
  }
}
```

**错误时返回:**


```
{
  "success": false,
  "msg": "服务器未知错误，xxxxxxxx",
  "data": {}
}
```

#### 返回参数说明:

|参数名|类型|说明|
|:-----  |:-----|-----                           |
|success |bool   |true:成功 false:失败  |
|msg |string   |消息  |
|data |Array   |数据  |
|apply_code |String   |申领单号  |
|project_code |String   |项目编号  |
|apply_date |String   |申领日期  |
|project_name |String   |项目名称  |
|apply_unit |String   |申领单位  |
|receiver |String   |领取人  |
|status |String   |状态  |

#### 备注:

- 更多详细情况请联系接口制定人