# APi for cp

### dianview 视频广告提供APi接口便广告主获取数据，结果会返回对应数据的列表。
### 版本1.0
## 概述
### 广告主依据文档提供的参数，构造请求链接，获取相应的数据。
## 请求格式
<b><font color="red">www.dianview.com/stats/transfer-api/index?ad_id=21ce1eb2ca4d1a82&start_time=2016-12-01&end_time=2016-12-25&group_by_date=1&apikey=*******</font></b>

## 参数列表
<table style="font-size:20px">
	<tr style="background-color:LightSteelBlue;">
		<td>参数名称</td>
		<td>是否必须</td>
		<td>类型</td>
		<td>备注说明</td>
	</tr>
	<tr>
		<td>apikey</td>
		<td>是</td>
		<td>string</td>
		<td>用户惟一key</td>
	</tr>
	<tr>
		<td>ad_id</td>
		<td>是</td>
		<td>string</td>
		<td>查询的广告id</td>
	</tr>
	<tr>
		<td>start_time</td>
		<td>否</td>
		<td>string</td>
		<td>起始时间，只有日期，例如2016-12-22</td>
	</tr>
		<tr>
		<td>end_time</td>
		<td>否</td>
		<td>string</td>
		<td>结束时间，例如2016-12-25</td>
	</tr>
		<tr>
		<td>group_by_date</td>
		<td>否</td>
		<td>string</td>
		<td>是否按天分组，值为0或者1</td>
	</tr>	
</table>

### apikey

登陆dianview Ads后台，在账户页面可得到key。每一次请求都需要带上当前key。

## 数据返回
### 数据格式
#### 数据返回格式:array

## 返回数据内容
### 示例
<p>
#### 示例1
<b>用户唯一key为XXXXXXX,广告ID为21ce1eb2ca4d1a82,查找其2016-12-01日到2016-12-25日的详情,需要按天分</b>
<pre>
GET   www.dianview.com/stats/transfer-api/index?ad_id=21ce1eb2ca4d1a82&start_time=2016-12-01&end_time=2016-12-25&group_by_date=1&apikey=********
</pre>
<b>返回结果</b>
<pre>
Array
(
    [0] => Array
        (
            [视频播放完成的次数] => 2809
            [广告点击次数] => 568
            [广告安装次数] => 99
            [日期] => 2016-12-20
        )
    [1] => Array
        (
            [视频播放完成的次数] => 5321
            [广告点击次数] => 1065
            [广告安装次数] => 211
            [日期] => 2016-12-21
        )
    [2] => Array
        (
            [视频播放完成的次数] => 18631
            [广告点击次数] => 4134
            [广告安装次数] => 818
            [日期] => 2016-12-22
        )
    [3] => Array
        (
            [视频播放完成的次数] => 15159
            [广告点击次数] => 3056
            [广告安装次数] => 622
            [日期] => 2016-12-23
        )
    [4] => Array
        (
            [视频播放完成的次数] => 14646
            [广告点击次数] => 2883
            [广告安装次数] => 618
            [日期] => 2016-12-24
        )
    [5] => Array
        (
            [视频播放完成的次数] => 15495
            [广告点击次数] => 3157
            [广告安装次数] => 619
            [日期] => 2016-12-25
        )

)
</pre>
#### 示例2
<b>用户唯一key为XXXXXXX,广告ID为21ce1eb2ca4d1a82,查找其2016-12-01日到2016-12-25日的总数据</b>
<pre>
GET   www.dianview.com/stats/transfer-api/index?ad_id=21ce1eb2ca4d1a82&start_time=2016-12-01&end_time=2016-12-25&group_by_date=0&apikey=********
</pre>
<b>返回结果</b>

<pre>
Array
(
    [视频播放完成的次数] => 72061
    [广告点击次数] => 14863
    [广告安装次数] => 2987
)

</pre>
#### 示例3
<b>用户唯一key为XXXXXXX,广告ID为21ce1eb2ca4d1a82,查其历史总数据</b>
<pre>
GET   www.dianview.com/stats/transfer-api/index?ad_id=21ce1eb2ca4d1a82&apikey=********
</pre>
<b>返回结果</b>

<pre>
Array
(
    [视频播放完成的次数] => 126819
    [广告点击次数] => 25345
    [广告安装次数] => 4834
)
</pre>

### 错误格式
| 错误码  | 错误信息 | 错误说明 |
|--------|----------|--------|
| 400 | Bad Request | 请求参数有错误 |
| 401 | Unauthorized  | 用户验证失败 |
### 请求限制
服务端对一次请求的最长处理时间是60s，如果超过这个时间，请求没有处理完成，那么终止处理，并返回错误。

