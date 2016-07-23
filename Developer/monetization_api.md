# Monetization Stats API

dianview Ads 提供了API接口便于开发者获取统计数据，结果会以json|xml的方式返回。当前接口是为方便开发者将数据加载到自己的统计平台。  

## 概述
开发者依据文档所提供的参数，构造请求连接，将数据GET到自己本地进行二次处理。这个过程会对请求接口做用户验证，过滤参数，并按照请求所要求的格式返回结果。

## 验证
要想使用当前接口，需要带上一个API KEY。这个key是在用户注册的过程就给予的，一个账户只会有一个key。如果修改了配置中的key，那么对应接口请求也需要及时更改。
如果验证失败，将返回Http 401: Unauthorized 的错误。

## 请求格式

<span style="color:red">`http://example.com/stats/monetization-api?apikey=<apikey>&fields=<fields>[&splitBy=<splitbyfields>][&scale=<scale>][&start=<startDate>][&end=<endDate>][&sourceIds=<sourceIds>]`</span>

### 参数列表

| 参数名称 | 是否必须 | 类型 | 备注说明 |
|--------|----------|--------|---------|
| [apikey](#apikey) | 是 | string | 一个账户一个key |
| [fields](#fields) | 是 | string | 想要获取的信息 |
| [splitBy](#splitBy) | 否 | string | 按照哪一个维度分组，默认应用id |
| [scale](#scale) | 否 | string | 聚合时间维度，默认是all |
| [start](#date) | 否 | integer/datetime | 查询的开始时间 | 
| [end](#date) | 否 | integer/datetime | 查询的结束时间 |
| [sourceIds](#sourceIds) | 否 | string | 要查询的app id|


#### <span id="apikey">apikey</span>

登陆dianview Ads后台，在账户页面可得到key。每一次请求都需要带上当前key。

#### <span id="fields">fields</span>
需要获取的数据，目前能使用的参数值有：`revenue, started, finished, show`，不在范围内的取值都会被忽略。  

	revenue 	收入
	started 	视频开始播放的次数
	finished 	视频播放完成的次数
	show 		广告详情页展示的次数

#### <span id="splitBy">splitBy</span>
数据依据那一列来分组，目前能使用的参数值：`source`，不在范围内的取值都会被忽略。默认会选取source。  
	
	source		按照应用来分组

#### <span id="scale">scale</span>
数据聚类统计的时间维度，目前能使用的参数值有：`all, hour, day, week, month, quarter, year`，不在范围内的数据都会被忽略。默认会选用all。

	all		忽略时间范围维度，算出来是个总计数据
	hour	以小时作为维度，统计出来的结果是以小时为时间长度，将每一个小时数据聚类出来
	day		天
	week	周
	month	月
	quarter	季度
	year	年

#### <span id="date">date</span>
请求数据的请求时间，开始时间以及结束时间。取值上可以有两种格式：

	负数，表明是以当前时间为七点，回溯到固定天数前。-7就是表明一周前。  
	datetime，需要使用固定的格式iso8601发送 yyyy-mm-ddThh:ii:ss+timezone 比如: 2016-07-10T19:00:00+08:00。
**注意，datetime格式中有+，需要编码为%2b，否则会出错。所以需要datetime这个数值需要做url encode**

#### <span id="sourceIds">sourceIds</span>
请求数据指定需要的应用，如果指定并且数值正确那么，只会返回当前sourceIds指定应用的数据。如果要查询多个使用逗号隔开。

## 数据返回

### 数据格式
数据返回目前支持两种格式：json | xml  
具体返回的什么格式，需要client端指定。

	Accept:application/json => json

	Accept:application/xml	=> xml
	
### 错误格式

| 错误码  | 错误信息 | 错误说明 |
|--------|----------|--------|
| 400 | Bad Request | 请求参数有错误 |
| 401 | Unauthorized  | 用户验证失败 |


## 请求限制
服务端对一次请求的最长处理时间是60s，如果超过这个时间，请求没有处理完成，那么终止处理，并返回错误。