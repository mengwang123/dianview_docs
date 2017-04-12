# APi for Developer

###dianview 视频广告提供APi接口便开发者获取数据，结果会返回对应数据的列表。
##概述
###开发者依据文档提供的参数，构造请求链接，获取相应的数据。
##请求格式

<b><font color="red">www.dianview.com/stats/transfer-api/index?ad_category=video&start_time=2016-12-01&end_time=2016-12-25&group_by_date=1&apikey=*******</font></b>

##参数列表

<table style="font-size:20px">
	<tr style="background-color:LightSteelBlue;">
		<td>参数名称</td>
		<td>是否必须</td>
		<td>类型</td>
		<td>备注说明</td>
	</tr>
	<tr>
		<td>ad_category</td>
		<td>是</td>
		<td>string</td>
		<td>广告类别,值为video(视频)或者interstitial(插屏)[注:无此参数默认为video]</td>
	</tr>
	<tr>
		<td>apikey</td>
		<td>是</td>
		<td>string</td>
		<td>用户惟一key</td>
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

##数据返回
###数据格式
####数据返回格式:json

##返回数据内容
###示例
<p>
####示例1
<b>用户唯一key为XXXXXXX,广告类别为video,查找其2016-12-01日到2016-12-25日的详情,需要按天分</b>
<pre>
GET   www.dianview.com/stats/transfer-api/index?start_time=2016-12-01&end_time=2016-12-25&group_by_date=1&ad_category=video&apikey=********
</pre>
####示例2
<b>用户唯一key为XXXXXXX,广告类别为interstitial,查找其2016-12-01日到2016-12-25日的总数据</b>
<pre>
GET   www.dianview.com/stats/transfer-api/index?start_time=2016-12-01&end_time=2016-12-25&group_by_date=0&ad_category=interstitial&apikey=********
</pre>
####示例3
<b>用户唯一key为XXXXXXX,广告类别为video,查其历史总数据</b>
<pre>
GET   www.dianview.com/stats/transfer-api/index?ad_category=video&apikey=********
</pre>

##返回参数列表
###视频参数列表
<table style="font-size:15px">
	<tr style="background-color:LightSteelBlue">
		<td>列名</td>
		<td>类型</td>
		<td>说明</td>
		<td>是否可以为空</td>
	</tr>
	<tr>
		<td>ad_click</td>
		<td>int</td>
		<td>点击数</td>
		<td>否</td>
	</tr>
	<tr>
		<td>req_num</td>
		<td>int</td>
		<td>返回数</td>
		<td>否</td>
	</tr>
	<tr>
		<td>app_id</td>
		<td>string</td>
		<td>应用id</td>
		<td>否</td>
	</tr>
	<tr>
		<td>earning</td>
		<td>string</td>
		<td>收入</td>
		<td>否</td>
	</tr>
	<tr>
		<td>video_start</td>
		<td>int</td>
		<td>播放开始数</td>
		<td>否</td>
	</tr>
	<tr>
		<td>video_start</td>
		<td>int</td>
		<td>播放完成数</td>
		<td>否</td>
	</tr>
	<tr>
		<td>ad_show</td>
		<td>int</td>
		<td>广告展示数</td>
		<td>否</td>
	</tr>			
	<tr>
		<td>day</td>
		<td>string</td>
		<td>日期</td>
		<td>是</td>
	</tr>			
</table>

###插屏返回参数列表
<table style="font-size:15px">
	<tr style="background-color:LightSteelBlue">
		<td>列名</td>
		<td>类型</td>
		<td>说明</td>
		<td>是否可以为空</td>
	</tr>
	<tr>
		<td>ad_notify</td>
		<td>int</td>
		<td>回调数</td>
		<td>否</td>
	</tr>
	<tr>
		<td>req_num</td>
		<td>int</td>
		<td>返回数</td>
		<td>否</td>
	</tr>
	<tr>
		<td>app_id</td>
		<td>string</td>
		<td>应用id</td>
		<td>否</td>
	</tr>
	<tr>
		<td>earning</td>
		<td>string</td>
		<td>收入</td>
		<td>否</td>
	</tr>
	<tr>
		<td>ad_click</td>
		<td>int</td>
		<td>点击数</td>
		<td>否</td>
	</tr>
	<tr>
		<td>ad_install</td>
		<td>int</td>
		<td>安装数</td>
		<td>否</td>
	</tr>
		<tr>
		<td>ad_imp</td>
		<td>int</td>
		<td>展示数</td>
		<td>否</td>
	</tr>
	<tr>
		<td>down_ok</td>
		<td>int</td>
		<td>下载数</td>
		<td>否</td>
	</tr>			
	<tr>
		<td>day</td>
		<td>string</td>
		<td>日期</td>
		<td>是</td>
	</tr>			
</table>

###提示
用户唯一key可以找相关人员获取。

