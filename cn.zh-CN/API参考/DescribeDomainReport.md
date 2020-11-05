# DescribeDomainReport

调用DescribeDomainReport获取域名Whois信息、数字证书、威胁类型、相关攻击团伙或安全事件信息。

默认接口请求频率限制：100次/秒。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Sasti&api=DescribeDomainReport&type=RPC&version=2020-05-12)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeDomainReport|系统规定参数。

 取值：**DescribeDomainReport**。 |
|Domain|String|是|\*.example.com|需要查询的域名。支持通配符域名。 |
|Field|String|否|ThreatTypes,Intelligences,AttackPreferenceTop5,AttackCntByThreatType|要查询的字段。可以输入多个参数值，以英文逗号分隔。

 取值：

 -   **ThreatTypes**：威胁情报事件的类型。
-   **Intelligences**：威胁情报事件。
-   **AttackPreferenceTop5**：被攻击的网站所属的Top 5行业。
-   **AttackCntByThreatType**：服务器遭受的攻击次数。
-   **为空**：表示仅返回域名、威胁等级、域名的基础信息、域名Whois信息和SSL证书信息。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|AttackCntByThreatType|String|\{"event\_cnt": 1583080, "threat\_type": "网络层入侵"\}|攻击的类型和次数统计信息。使用JSON数组表示，数组中的取值如下：

 -   **event\_cnt**：攻击事件的发生次数。
-   **threat\_type**：威胁类型，包括网络层入侵、网络服务扫描、网络共享发现、矿池 、漏洞利用 、暗网、恶意登录、恶意下载源、中控、Web Shell 、WEB攻击等。 |
|AttackPreferenceTop5|String|\{"event\_cnt": 2, "industry\_name": "媒体","gmt\_last\_attack": "2020-10-23 08:50:50"\}|被攻击的网站所属的Top 5行业。使用JSON数组表示。 |
|Basic|String|\{"domain": example\}|域名的基础信息。

 取值：

 -   **domain**：域名
-   **sld\_domain**：SLD域名
-   **reg\_date**：域名注册时间
-   **expire\_date**：域名过期时间
-   **child\_domain\_cnt**：子域名个数
-   **malicious\_child\_domain\_cnt**：恶意子域名个数
-   **ip\_cnt\_365d**：近1年解析IP数
-   **malicious\_ip\_cnt\_365d**：近1年解析IP为恶意IP的数量 |
|Domain|String|example.com|域名。 |
|Intelligences|String|\{"ip": "193.106.\*.\*","gmt\_last": "2020-10-24 21:35:30","threat\_type\_l3": "SQLServer服务扫描","source": "Aliyun"\}|威胁情报事件，使用JSON数组表示。

 取值：

 -   **source**：威胁来源。
-   **find\_time**：最近发现时间。
-   **threat\_types**：威胁类型。使用数组表示，数组的元素取值包括网络层入侵、网络服务扫描、网络共享发现、矿池 、漏洞利用 、暗网、恶意登录、恶意下载源、中控、Web Shell 、WEB攻击等。 |
|RequestId|String|718747A4-9A75-4130-88F9-C9B47350B7F5|阿里云为此次调用请求生成的唯一标识符。 |
|SslCert|String|\{ "serial\_number": "18395475168054001104", "validity\_end": "2029-12-02 06:00:31", "issuer": "kubevip-ca",...\}|域名绑定的SSL证书信息。使用JSON串表示。 |
|ThreatLevel|String|2|威胁等级。

 取值：

 -   **0**：正常
-   **1**：可疑
-   **2**：高危 |
|ThreatTypes|String|\{"threat\_type\_desc": "WEB攻击源","last\_find\_time": "2020-10-23 08:50:50","risk\_type": 1,"threat\_type": "WEB Attack"\}|从威胁情报、安全事件分析出来的风险标签和服务器标签。使用String数组表示，每一个数组中的取值如下：

 -   **threat\_type\_desc**：威胁来源。
-   **last\_find\_time**：最近发现时间。
-   **risk\_type**：表示是否是恶意标签。0表示非恶意标签，1表示恶意标签。
-   **threat\_types**：威胁类型。使用数组表示，数组的元素取值包括网络层入侵、网络服务扫描、网络共享发现、矿池 、漏洞利用 、暗网、恶意登录、恶意下载源、中控、Web Shell 、WEB攻击等。 |
|Whois|String|\{ "serial\_number": "18395475168054001104",...\}|域名的Whois信息。使用JSON串表示。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeDomainReport
&Domain=*.example.com
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeDomainReportResponse>
  <RequestId>718747A4-9A75-4130-88F9-C9B47350B7F5</RequestId>
  <data>
        <AttackCntByThreatType>
              <event_cnt>27</event_cnt>
              <threat_type>应用层入侵</threat_type>
        </AttackCntByThreatType>
        <Whois></Whois>
        <ThreatLevel>2</ThreatLevel>
        <Ip>
              <country>中国</country>
              <province>内蒙古自治区</province>
              <city>呼和浩特市</city>
              <ip>1.180.*.*</ip>
              <isp>电信</isp>
              <asn>4134</asn>
              <asn_label>CHINANET-BACKBONE - No.31,Jin-rong Street, CN</asn_label>
        </Ip>
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
        <Intelligences>
              <ip>1.180.*.*</ip>
              <gmt_last>2020-10-23 08:50:50</gmt_last>
              <threat_type_l3>code_exec</threat_type_l3>
              <source>Aliyun</source>
        </Intelligences>
        <Intelligences>
              <ip>1.180.*.*</ip>
              <gmt_last>2020-09-27 17:15:59</gmt_last>
              <threat_type_l3>SSH服务扫描</threat_type_l3>
              <source>Aliyun</source>
        </Intelligences>
        <Intelligences>
              <ip>1.180.*.*</ip>
              <gmt_last>2020-10-27 15:00:28</gmt_last>
              <threat_type_l3>ThinkPHP5 RCE</threat_type_l3>
              <source>Aliyun</source>
        </Intelligences>
        <Intelligences>
              <ip>1.180.*.*</ip>
              <gmt_last>2020-10-13 07:09:14</gmt_last>
              <threat_type_l3>webshell</threat_type_l3>
              <source>Aliyun</source>
        </Intelligences>
        <Intelligences>
              <ip>1.180.*.*</ip>
              <gmt_last>2020-10-15 11:02:09</gmt_last>
              <threat_type_l3>F5 RCE CVE-2020-5902</threat_type_l3>
              <source>Aliyun</source>
        </Intelligences>
        <Intelligences>
              <ip>1.180.*.*</ip>
              <gmt_last>2020-10-13 14:42:42</gmt_last>
              <threat_type_l3>lfilei</threat_type_l3>
              <source>Aliyun</source>
        </Intelligences>
        <Intelligences>
              <ip>1.180.*.*</ip>
              <gmt_last>2020-06-28 15:26:48</gmt_last>
              <threat_type_l3>Weblogic SSRF</threat_type_l3>
              <source>Aliyun</source>
        </Intelligences>
        <Intelligences>
              <ip>1.180.*.*</ip>
              <gmt_last>2020-10-13 07:10:07</gmt_last>
              <threat_type_l3>Weblogic RCE CVE-2019-2725</threat_type_l3>
              <source>Aliyun</source>
        </Intelligences>
        <Intelligences>
              <ip>1.180.*.*</ip>
              <gmt_last>2020-07-20 09:40:52</gmt_last>
              <threat_type_l3>Weblogic RCE CVE-2017-10271</threat_type_l3>
              <source>Aliyun</source>
        </Intelligences>
        <AttackPreferenceTop5>
              <event_cnt>2</event_cnt>
              <industry_name>媒体</industry_name>
              <gmt_last_attack>2020-10-23 08:50:50</gmt_last_attack>
        </AttackPreferenceTop5>
        <AttackPreferenceTop5>
              <event_cnt>89</event_cnt>
              <industry_name>金融</industry_name>
              <gmt_last_attack>2020-10-13 14:49:03</gmt_last_attack>
        </AttackPreferenceTop5>
        <AttackPreferenceTop5>
              <event_cnt>2</event_cnt>
              <industry_name>互联网</industry_name>
              <gmt_last_attack>2020-10-23 08:49:20</gmt_last_attack>
        </AttackPreferenceTop5>
  </data>
</DescribeDomainReportResponse>
```

`JSON` 格式

```
{
    "RequestId": "718747A4-9A75-4130-88F9-C9B47350B7F5",
    "data": [
        {
            "AttackCntByThreatType": [
                {
                    "event_cnt": 27,
                    "threat_type": "应用层入侵"
                }
            ],
            "Whois": "",
            "ThreatLevel": "2",
            "Ip": {
                "country": "中国",
                "province": "内蒙古自治区",
                "city": "呼和浩特市",
                "ip": "1.180.*.*",
                "isp": "电信",
                "asn": "4134",
                "asn_label": "CHINANET-BACKBONE - No.31,Jin-rong Street, CN"
            },
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
                },
                {
                    "ip": "1.180.*.*",
                    "gmt_last": "2020-10-23 08:50:50",
                    "threat_type_l3": "code_exec",
                    "source": "Aliyun"
                },
                {
                    "ip": "1.180.*.*",
                    "gmt_last": "2020-09-27 17:15:59",
                    "threat_type_l3": "SSH服务扫描",
                    "source": "Aliyun"
                },
                {
                    "ip": "1.180.*.*",
                    "gmt_last": "2020-10-27 15:00:28",
                    "threat_type_l3": "ThinkPHP5 RCE",
                    "source": "Aliyun"
                },
                {
                    "ip": "1.180.*.*",
                    "gmt_last": "2020-10-13 07:09:14",
                    "threat_type_l3": "webshell",
                    "source": "Aliyun"
                },
                {
                    "ip": "1.180.*.*",
                    "gmt_last": "2020-10-15 11:02:09",
                    "threat_type_l3": "F5 RCE CVE-2020-5902",
                    "source": "Aliyun"
                },
                {
                    "ip": "1.180.*.*",
                    "gmt_last": "2020-10-13 14:42:42",
                    "threat_type_l3": "lfilei",
                    "source": "Aliyun"
                },
                {
                    "ip": "1.180.*.*",
                    "gmt_last": "2020-06-28 15:26:48",
                    "threat_type_l3": "Weblogic SSRF",
                    "source": "Aliyun"
                },
                {
                    "ip": "1.180.*.*",
                    "gmt_last": "2020-10-13 07:10:07",
                    "threat_type_l3": "Weblogic RCE CVE-2019-2725",
                    "source": "Aliyun"
                },
                {
                    "ip": "1.180.*.*",
                    "gmt_last": "2020-07-20 09:40:52",
                    "threat_type_l3": "Weblogic RCE CVE-2017-10271",
                    "source": "Aliyun"
                }
            ],
            "AttackPreferenceTop5": [
                {
                    "event_cnt": 2,
                    "industry_name": "媒体",
                    "gmt_last_attack": "2020-10-23 08:50:50"
                },
                {
                    "event_cnt": 89,
                    "industry_name": "金融",
                    "gmt_last_attack": "2020-10-13 14:49:03"
                },
                {
                    "event_cnt": 2,
                    "industry_name": "互联网",
                    "gmt_last_attack": "2020-10-23 08:49:20"
                }
            ]
        }
    ]
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Sasti)查看更多错误码。

访问[错误中心](https://error-center.alibabacloud.com/status/product/Sasti)查看更多错误码。

