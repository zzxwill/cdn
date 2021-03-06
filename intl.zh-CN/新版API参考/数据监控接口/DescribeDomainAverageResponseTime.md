# DescribeDomainAverageResponseTime {#reference2509 .reference}

获取加速域名的平均响应时间。

不指定StartTime和EndTime时，默认读取过去24小时的数据，同时支持按指定的起止时间查询，两者需要同时指定。

**说明：** 最多可获取最近90天的数据。

## 请求参数 { .section}

|参数|类型|是否必需|描述|
|--|--|----|--|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeDomainAverageResponseTime|
|DomainName|String|否| -   若参数为空，默认返回所有加速域名合并后数据。
-   可输入需要查询的加速域名。
-   支持批量域名查询，多个域名用逗号（半角）分隔。

 |
|StartTime|String|否|获取数据起始时间点。-   日期格式按照ISO8601表示法，并使用UTC时间。
-   格式为：YYYY-MM-DDThh:mm:ssZ。
-   最小数据粒度为5分钟， 不写默认读取过去24小时数据。

|
|EndTime|String|否| -   结束时间需大于起始时间。
-   获日期格式按照ISO8601表示法，并使用UTC时间。
-   格式为：YYYY-MM-DDThh:mm:ssZ。

 |
|TimeMerge|String|否|是否自适应计算interval值，如果timeMerge=1，会根据startTime和endTime自己计算出合适的inteval值，和interval参数任选。|
|Interval|String|否| -   查询数据的时间粒度，支持300、 3600和86400秒。
-   - 3天以内（不包含3天整）支持300、 3600、 86400。
-   - 3-31天（不包含31天整）支持3600和86400。
-   - 31天以上支持86400。
-   - 不传和传的值不支持时，使用默认值。

 |

## 返回参数 { .section}

|名称|类型|描述|
|--|--|--|
|DomainName|String|加速域名|
|StartTime|DateTime|开始时间|
|EndTime|DateTime|结束时间|
|DataInterval|String|数据时间间隔|
|AvgRTPerInterval|DataModule\[\]| |

## DataModule { .section}

|名称|类型|描述|
|--|--|--|
|TimeStamp|String|时间片起始时刻|
|Value|String|平均响应时间|

## 示例 { .section}

请求示例：

```
http://cdn.aliyuncs.com?Action=DescribeDomainAverageResponseTime&DomainName=example.com
&StartTime=2015-12-10T20:00:00Z
&EndTime=2015-12-11T21:00:00Z
&<公共请求参数>
```

返回示例：

JSON格式

```language-json
{
    "DomainName": "example.com",
    "RequestId": "3C6CCEC4-6B88-4D4A-93E4-D47B3D92CF8F",
    "StartTime": "2015-12-10T20:00:00Z",
    "EndTime": "2015-12-11T21:00:00Z",
    "DataInterval": "300",
    "AvgRTPerInterval": {
        "DataModule": [
            {
                "TimeStamp": "2015-12-10T20:00:00Z",
                "Value": "3"
            },
            {
                "TimeStamp": "2015-12-10T20:05:00Z",
                "Value": "3"
            }
        ]
    }
}

```

## 错误码 { .section}

|错误代码|错误信息|HTTP 状态码|描述|
|----|----|--------|--|
|InvalidStartTime.Malformed|Specified StartTime is malformed.|400|StartTime格式错误|
|InvalidEndTime.Malformed|Specified EndTime is malformed.|400|EndTime格式错误|
|InvalidStartTime.ValueNotSupported|The specified value of parameter StartTime is not supported.|400|EndTime和StartTime差值超过90天|

