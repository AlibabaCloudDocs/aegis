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
|FileHash|String|是|file\_md5|要查询的文件hash（md5）。 |
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
|Basic|String|"Basic": \{"sha1": "","virus\_result": "1","sandbox\_result": "-1","sha256": "","sha512": "","virus\_name": "自变异木马","source": "aegis","md5": "<file\_md5\>","gmt\_first\_submit": "2020-03-15 19:22:25"\}|基础信息。字段说明如下：

 -   **md5**：文件MD5。
-   **sha1**：文件sha1。
-   **sha256**：文件sha256。
-   **sha512**：文件sha512。
-   **virus\_result**：文件静态扫描结果。0表示正常，1表示恶意。
-   **sandbox\_result**：文件动态沙箱运行结果。0表示正常，1表示恶意。
-   **source**：文件来源。 |
|FileHash|String|<file\_md5\>|文件Hash值。 |
|Intelligences|String|\{"ip": "193.106.\*.\*","gmt\_last": "2020-10-24 21:35:30", "threat\_type\_l3": "SQLServer服务扫描","source": "Aliyun"\}|威胁情报事件，使用JSON数组表示。

 取值：

 -   **source**：威胁来源。
-   **find\_time**：最近发现时间。
-   **threat\_types**：威胁类型。使用数组表示，数组的元素取值包括网络层入侵、网络服务扫描、网络共享发现、矿池 、漏洞利用 、暗网、恶意登录、恶意下载源、中控、Web Shell 、WEB攻击等。 |
|RequestId|String|718747A4-9A75-4130-88F9-C9B47350B123|阿里云为此次调用请求生成的唯一标识符。 |
|ThreatLevel|String|1|威胁等级。

 取值：

 -   **0**：正常
-   **1**：可疑
-   **2**：高危 |
|ThreatTypes|String|\{"threat\_type\_desc": "WEB攻击源","last\_find\_time": "2020-10-23 08:50:50","risk\_type": 1,"threat\_type": "WEB Attack"\}|从威胁情报、安全事件分析出来的风险标签和服务器标签。使用String数组表示，每一个数组中的取值如下：

 -   **threat\_type\_desc**：威胁来源。
-   **last\_find\_time**：最近发现时间。
-   **risk\_type**：表示是否是恶意标签。0表示非恶意标签，1表示恶意标签。
-   **threat\_types**：威胁类型。使用数组表示，数组的元素取值包括网络层入侵、网络服务扫描、网络共享发现、矿池 、漏洞利用 、暗网、恶意登录、恶意下载源、中控、Web Shell 、WEB攻击等。 |

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
  <message>success</message>
  <Basic>
        <sha1></sha1>
        <virus_result>1</virus_result>
        <sandbox_result>-1</sandbox_result>
        <sha256></sha256>
        <sha512></sha512>
        <virus_name>自变异木马</virus_name>
        <source>aegis</source>
        <md5>&lt;file_md5&gt;</md5>
        <gmt_first_submit>2020-03-15 19:22:25</gmt_first_submit>
  </Basic>
  <RequestId>964CD096-DCCC-44D2-B661-XXXXXXXXX</RequestId>
  <ThreatTypes>
        <threat_type_desc>WEB攻击源</threat_type_desc>
        <last_find_time>2020-10-23 08:50:50</last_find_time>
        <risk_type>1</risk_type>
        <threat_type>WEB Attack</threat_type>
  </ThreatTypes>
  <ThreatTypes>
        <threat_type_desc>网络服务扫描</threat_type_desc>
        <last_find_time>2020-09-27 17:15:59</last_find_time>
        <risk_type>1</risk_type>
        <threat_type>Network Service Scanning</threat_type>
  </ThreatTypes>
  <ThreatTypes>
        <threat_type_desc>漏洞利用</threat_type_desc>
        <last_find_time>2020-10-27 15:00:28</last_find_time>
        <risk_type>1</risk_type>
        <threat_type>Exploit</threat_type>
  </ThreatTypes>
  <Intelligences>
        <ip>1.180.*.*</ip>
        <gmt_last>2020-05-18 15:41:46</gmt_last>
        <threat_type_l3>sqli</threat_type_l3>
        <source>Aliyun</source>
  </Intelligences>
  <Intelligences>
        <ip>1.180.*.*</ip>
        <gmt_last>2020-10-13 14:49:03</gmt_last>
        <threat_type_l3>xss</threat_type_l3>
        <source>Aliyun</source>
  </Intelligences>
  <ThreatLevel>2</ThreatLevel>
  <FileHash>&lt;file_md5&gt;</FileHash>
</DescribeFileReportResponse>
```

`JSON` 格式

```
{
    "code":200,
    "message":"success",
    "Basic": {
        "sha1": "",
        "virus_result": "1",
        "sandbox_result": "-1",
        "sha256": "",
        "sha512": "",
        "virus_name": "自变异木马",
        "source": "aegis",
        "md5": "<file_md5>",
        "gmt_first_submit": "2020-03-15 19:22:25"
    },
    "RequestId": "964CD096-DCCC-44D2-B661-XXXXXXXXX",
    "ThreatTypes": [
                {
                    "threat_type_desc": "WEB攻击源",
                    "last_find_time": "2020-10-23 08:50:50",
                    "risk_type": 1,
                    "threat_type": "WEB Attack"
                },
                {
                    "threat_type_desc": "网络服务扫描",
                    "last_find_time": "2020-09-27 17:15:59",
                    "risk_type": 1,
                    "threat_type": "Network Service Scanning"
                },
                {
                    "threat_type_desc": "漏洞利用",
                    "last_find_time": "2020-10-27 15:00:28",
                    "risk_type": 1,
                    "threat_type": "Exploit"
                }
            ],
            "Intelligences": [
                {
                    "ip": "1.180.*.*",
                    "gmt_last": "2020-05-18 15:41:46",
                    "threat_type_l3": "sqli",
                    "source": "Aliyun"
                },
                {
                    "ip": "1.180.*.*",
                    "gmt_last": "2020-10-13 14:49:03",
                    "threat_type_l3": "xss",
                    "source": "Aliyun"
                }
    ],
    "ThreatLevel": "2",
    "FileHash": "<file_md5>"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Sasti)查看更多错误码。

访问[错误中心](https://error-center.alibabacloud.com/status/product/Sasti)查看更多错误码。

