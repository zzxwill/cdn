# DeleteRealtimeLogDelivery {#reference_hzn_d3y_dgb .reference}

删除实时日志推送域名。

## 请求参数 {#section_t1g_ygy_dgb .section}

|参数|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：DeleteRealtimeLogDelivery。|
|Domain|String|是|删除实时日志投递服务域名,支持多个，以逗号分隔。|
|Project|String|是|实时投递sls的ProjectName|
|Logstore|String|是|实时投递sls的LogStoreName|
|Region|String|是|实时投递sls的Region，如上海:cn-shanghai。详情请参见 [附录](../../../../intl.zh-CN/旧版API参考/附录.md#table_nnm_mcz_dgb)。|

## 返回参数 {#section_uqf_jhy_dgb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|RequestId|

## 示例 {#section_ifn_qhy_dgb .section}

请求示例

```
https://cdn.aliyuncs.com?Action=DeleteRealtimeLogDelivery&Domain=xxx.com
```

返回示例

```
{
    "RequestId": "9732E117-8A37-49FD-A36F-ABBB87556CA7",
}
```

## 错误码 {#section_mmt_mhy_dgb .section}

|错误码|错误信息|HTTP 状态码|
|:--|:---|:-------|
|Unauthorized|没有开启实时投递授权|403|
|LogstoreNotExist|未找到对应Logstore 信息|404|

