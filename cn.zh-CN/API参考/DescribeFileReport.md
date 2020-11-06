# DescribeFileReport

调用DescribeFileReport获取文件静态扫描结果、动态沙箱运行结果。

默认接口请求频率限制：100次/秒。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Sasti&api=DescribeFileReport&type=RPC&version=2020-05-12)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeFileReport|系统规定参数。

 取值：**DescribeFileReport**。 |
|FileHash|String|是|file\_md5|要查询的文件hash（MD5值）。 |
|Field|String|否|ThreatTypes,Intelligences,AttackPreferenceTop5,AttackCntByThreatType|要查询的字段。可以输入多个参数值，以英文逗号分隔。

 取值：

 -   **ThreatTypes**：威胁情报事件的类型。
-   **Intelligences**：威胁情报事件。
-   **AttackPreferenceTop5**：被攻击网站所属行业的Top 5。
-   **AttackCntByThreatType**：服务器遭受的攻击次数。
-   **为空**：表示仅返回域名、威胁等级、域名的基础信息、域名Whois信息和SSL证书信息。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Basic|String|"Basic": \{"sha1": "","virus\_result": "1","sandbox\_result": "-1","sha256": "","sha512": "","virus\_name": "自变异木马","source": "aegis","md5": "...\}|基础信息。字段说明如下：

 -   **md5**：文件MD5值。
-   **sha1**：文件SHA1值。
-   **sha256**：文件SHA256值。
-   **sha512**：文件SHA512值。
-   **virus\_result**：文件静态扫描结果。**0**表示正常，**1**表示恶意，**-1**表示未知。
-   **sandbox\_result**：文件动态沙箱运行结果。**0**表示正常，**1**表示恶意，**-1**表示未知。
-   **source**：文件来源。唯一取值为**aegis**，表示是由云安全中心检测出该文件。 |
|FileHash|String|02e6b7cf0d34c6eac059f754b751208b|文件Hash值。 |
|RequestId|String|3F2BBCA2-4EE5-456F-93B1-DE0B69CAFD71|阿里云为此次调用请求生成的唯一标识符。 |
|Intelligences|String|\["DDOS木马"\]|威胁情报事件，使用JSON数组表示。

 取值：

 -   **source**：威胁来源。
-   **find\_time**：最近发现时间。
-   **threat\_types**：威胁类型。使用数组表示，数组的元素取值包括网络层入侵、网络服务扫描、网络共享发现、矿池 、漏洞利用 、暗网、恶意登录、恶意下载源、中控、Web Shell 、Web攻击等。 |
|ThreatLevel|String|2|威胁等级。

 取值：

 -   **0**：正常
-   **1**：可疑
-   **2**：高危 |
|ThreatTypes|String|\[\{"threat\_type\_desc": "DDoS木马","risk\_type": 1,"threat\_type": "DDOS"\}\]|从威胁情报、安全事件分析出来的风险标签和服务器标签。使用String数组表示，每一个数组中的取值如下：

 -   **threat\_type\_desc**：威胁类型。取值包括：Rootkit、后门程序、可疑程序、挖矿程序、DDOS木马、恶意程序、蠕虫病毒、可疑黑客工具木马程序、被污染的基础软件（被植入了恶意代码）、感染型病毒、漏洞利用程序、勒索病毒、自变异木马、高危程序、黑客工具。
-   **last\_find\_time**：最近发现时间。
-   **risk\_type**：表示是否是恶意标签。**0**表示非恶意标签，**1**表示恶意标签，**-1**表示未知。
-   **threat\_types**：威胁类型。使用数组表示，数组的元素取值包括网络层入侵、网络服务扫描、网络共享发现、矿池 、漏洞利用 、暗网、恶意登录、恶意下载源、中控、Web Shell 、Web攻击等。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeFileReport
&FileHash=<file_md5>
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeFileReportResponse>
  <code>200</code>
  <data>
        <Basic>
              <sha1></sha1>
              <virus_result>1</virus_result>
              <sandbox_result>-1</sandbox_result>
              <sha256></sha256>
              <sha512></sha512>
              <virus_name>DDOS木马</virus_name>
              <source>aegis</source>
              <md5>02e6b7cf0d34c6eac059f754b751208b</md5>
              <gmt_first_submit>2019-02-06 12:12:58</gmt_first_submit>
        </Basic>
        <ThreatLevel>2</ThreatLevel>
        <FileHash>02e6b7cf0d34c6eac059f754b751208b</FileHash>
        <ThreatTypes>
              <threat_type_desc>DDoS木马</threat_type_desc>
              <risk_type>1</risk_type>
              <threat_type>DDOS</threat_type>
        </ThreatTypes>
        <Intelligences>DDOS木马</Intelligences>
  </data>
  <requestId>3F2BBCA2-4EE5-456F-93B1-DE0B69CAFD71</requestId>
  <success>true</success>
</DescribeFileReportResponse>
```

`JSON` 格式

```
{
	"code": 200,
	"data": {
		"Basic": {
			"sha1": "",
			"virus_result": "1",
			"sandbox_result": "-1",
			"sha256": "",
			"sha512": "",
			"virus_name": "DDOS木马",
			"source": "aegis",
			"md5": "02e6b7cf0d34c6eac059f754b751208b",
			"gmt_first_submit": "2019-02-06 12:12:58"
		},
		"ThreatLevel": "2",
		"FileHash": "02e6b7cf0d34c6eac059f754b751208b",
		"ThreatTypes": [{
			"threat_type_desc": "DDoS木马",
			"risk_type": 1,
			"threat_type": "DDOS"
		}],
		"Intelligences": ["DDOS木马"]
	},
	"requestId": "3F2BBCA2-4EE5-456F-93B1-DE0B69CAFD71",
	"success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Sasti)查看更多错误码。

