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
|Domain|String|是|example.com|需要查询的域名。支持通配符域名。 |
|Field|String|否|ThreatTypes,Intelligences,AttackPreferenceTop5,AttackCntByThreatType|要查询的字段。可以输入多个参数值，以英文逗号分隔。

 取值：

 -   **ThreatTypes**：从威胁情报、安全事件分析出来的该域名所具备的风险标签。
-   **Intelligences**：详细的威胁情报事件。
-   **AttackPreferenceTop5**：被攻击的网站所属的Top 5行业。
-   **AttackCntByThreatType**：服务器遭受的攻击次数。
-   **为空**：表示仅返回域名、威胁等级、域名的基础信息、域名Whois信息和SSL证书信息。 |

默认接口请求频率限制：100次/秒。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|AttackCntByThreatType|String|\{"event\_cnt": 27, "threat\_type": "网络层入侵"\}|不同攻击阶段的攻击次数。

 该参数使用JSON数组表示，数组中的字段含义说明如下：

 字段含义：

 -   **event\_cnt**：攻击次数。
-   **threat\_type**：攻击所属 ATT&CK 阶段。 |
|AttackPreferenceTop5|String|\[\{"event\_cnt":586,"industry\_name":"Gaming","gmt\_last\_attack":"2020-06-14 21:54:04"\}\]|被攻击的网站所属的Top 5行业。使用JSON数组表示。

 字段含义：

 -   **event\_cnt**：攻击次数。
-   **industry\_name**：攻击行业类别。
-   **gmt\_last\_attack**：最后攻击活跃时间。 |
|Basic|String|\{ "ip\_cnt": "36", "domain": "example.com", "child\_domain\_cnt": "18", "sld\_domain": "example.com", "malicious\_ip\_cnt": "28", "malicious\_child\_domain\_cnt": "4" \}|域名的基础信息。使用JSON格式表示。

 字段含义如下：

 -   **domain**：域名
-   **sld\_domain**：SLD域名
-   **reg\_date**：域名注册时间
-   **expire\_date**：域名过期时间
-   **child\_domain\_cnt**：子域名数量
-   **malicious\_child\_domain\_cnt**：恶意子域名数量
-   **ip\_cnt\_365d**：近1年该域名的解析IP数量
-   **malicious\_ip\_cnt\_365d**：近1年该域名解析IP为恶意IP的数量 |
|Confidence|String|95|对判定结果的置信程度，置信度值越高，说明对判定结果（判定结果是ThreatLevel字段）有多少信心。通常认为置信度大于90的结果可以作为精准结果，对于恶意的高威胁等级的指标可以进行拦截。对于正常（ThreatLevel等于0）的结果可以放行。

 取值范围60-100：

 -   **\[90-100\)**：认为该情报是高可信的，可以作为拦截或者放行依据，如果ThreatLevel表示高危（ThreatLevel=3）则可拦截，如果ThreatLevel表示正常（ThreatLevel=0）。
-   **\[60-90\)**：认为情报有一定的可行，但是还不能达到拦截指标，通常是有一些恶意行为的域名。可作为安全分析运营的辅助依据。 |
|Context|String|""|保留字段，暂空 |
|Domain|String|example.com|域名。 |
|Intelligences|String|\[\{ "last\_find\_time": "2020-06-17 03:54:23", "threat\_type\_l2": "恶意下载源", "first\_find\_time": "2020-01-01 00:59:52", "source": "aliyun" \}, \{ "last\_find\_time": "2020-11-10 14:45:12", "threat\_type\_l2": "regsvr32.exe执行恶意文件", "first\_find\_time": "2017-09-22 11:15:00", "source": "aliyun" \} \]|详细的威胁情报事件，使用JSON数组表示。

 字段含义：

 -   **source**：威胁情报数据来源。
-   **last\_find\_time**：最后活跃时间。
-   **threat\_type\_l2**：威胁情报详细标签，可以使家族团伙的标签，例如mykings，apt32，可以使攻击手法，例如bits job，描述连接域名使用的手法。 |
|RequestId|String|718747A4-9A75-4130-88F9-C9B47350B7F5|阿里云为此次调用请求生成的唯一标识符。 |
|Scenario|String|"失陷指标"|该域名所适用的攻击场景。

 可以取以下的一个或者多个值：

 -   **攻击指标**：域名通常不为攻击指标。
-   **失陷指标**：攻击者植入的脚本或者恶意代码会回联该域名进行通讯和数据传输，如果在流量或者日志中发现该域名意味着当前主机已经被攻破。失陷以后对外的C2连接
-   **信息数据**：白名单等类型，该字段为信息数据，不具有风险场景 |
|SslCert|String|\{ "serial\_number": "18395475168054001104", "validity\_end": "2029-12-02 06:00:31", "issuer": "example.ca",...\}|域名绑定的SSL证书信息。使用JSON串表示。 |
|ThreatLevel|String|2|威胁等级，命中以后造成的危害等级，恶意的等级有高危、中危、低危、正常和未知五个等级。使用的时候可以结合置信度（Confidence字段）来使用，对高危并且高置信度的数据进行拦截。对于正常（即白名单）的类型可以进行放行。

 取值：

 -   **-1**：未知
-   **0**：正常，即白名单，可以放行
-   **1**：低危
-   **2**：中危
-   **3**：高危 |
|ThreatTypes|String|\[\{ "threat\_type\_desc": "恶意下载源", "last\_find\_time": "2020-06-17 03:54:23", "risk\_type": 3, "scenario": "失陷指标", "threat\_type": "Malicious Source", "first\_find\_time": "2020-01-01 00:59:52", "attck\_stage": "delivery" \}, \{ "threat\_type\_desc": "Regsvr32执行", "last\_find\_time": "2020-11-10 14:45:12", "risk\_type": 3, "scenario": "失陷指标", "threat\_type": "Regsvr32", "first\_find\_time": "2017-09-22 11:15:00", "attck\_stage": "defense evasion" \} \]|该域名相关的详细威胁情报数据，使用JSON数组表示，每一个数组的字段含义如下：

 -   **threat\_type\_desc**：标签的中文描述。
-   **first\_find\_time**：首次标记时间。
-   **last\_find\_time**：最后标记时间。
-   **risk\_type**：表示是否是恶意标签。**0**表示非恶意标签，**1**表示可疑标签，**2**表示恶意标签，**-1**表示未知。
-   **scenario**： 该域名所归属的场景，失陷指标或攻击指标。
-   **attck\_stage**：该恶意行为所属的 ATT&CK 攻击阶段。
-   **threat\_type**：威胁类型。

 常见的威胁标签（threat\_type字段）取值：

 -   **Botnet**：僵尸网络
-   **Trojan**：木马
-   **Worm**：蠕虫
-   **Malware**：恶意软件
-   **Ransomware**：勒索软件
-   **APT**：高级持续威胁攻击
-   **RAT**：远控
-   **C&C Server**：命令与控制服务器
-   **Miner Pool**：矿池
-   **Malicious Source**：恶意下载源
-   **Scheduled Task**：Windows计划任务
-   **BITS Jobs**：BITS作业
-   **Command-Line Interface**：恶意命令
-   **Mshta执行**：Mshta执行
-   **Regsvr32**：Regsvr32执行
-   **Signed Binary Proxy Execution**：签名的二进制代理执行
-   **Local Job Scheduling**：Linux计划任务
-   **Rundll32**：Rundll32执行 |
|Whois|String|\{"registrant\_phone": "", "registrar": "科技有限公司", "registrar\_url": "", "whois\_server": "whois.cnnic.cn", "admin\_phone": "", "registrar\_phone": "", "registrant\_email": "", "admin\_email": "", "admin\_organization": "", "tech\_name": "", "registrant\_city": "", "tech\_street": "", "tech\_phone": "", "dnssec": "unsigned", "admin\_province": "", "tech\_organization": "", "registrant\_country": "", "admin\_city": "", "registrant\_province": "", "admin\_street": "", "tech\_email": "", "nameservers": "ns4.myhostadmin.net,ns1.myhostadmin.net,ns2.myhostadmin.net,ns3.myhostadmin.net,ns5.myhostadmin.net,ns6.myhostadmin.net", "registrar\_email": "", "domain\_status": "ok", "domain": "example.com", "tech\_city": "", "registrant\_name": "朱轩", "registrant\_organization": "", "tech\_country": "", "registrant\_street": "", "admin\_name": "", "tech\_province": "", "admin\_country": ""\}|域名的Whois信息。使用JSON串表示。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeDomainReport
&Domain=example.com
&Field=ThreatTypes%2CIntelligences%2CAttackPreferenceTop5%2CAttackCntByThreatType
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<Context/>
<Basic>
    <ip_cnt>36</ip_cnt>
    <domain>example.com</domain>
    <child_domain_cnt>18</child_domain_cnt>
    <sld_domain>example.com</sld_domain>
    <malicious_ip_cnt>28</malicious_ip_cnt>
    <malicious_child_domain_cnt>4</malicious_child_domain_cnt>
</Basic>
<RequestId>55B99BBE-AD29-4220-A650-A24F16C61071</RequestId>
<SslCert/>
<ThreatTypes>
    <threat_type_desc>中控</threat_type_desc>
    <last_find_time>2019-12-19 10:20:47</last_find_time>
    <risk_type>3</risk_type>
    <scenario>失陷指标</scenario>
    <threat_type>C&amp;C Server</threat_type>
    <first_find_time>2019-06-20 22:18:58</first_find_time>
    <attck_stage/>
</ThreatTypes>
<ThreatTypes>
    <threat_type_desc>Regsvr32执行</threat_type_desc>
    <last_find_time>2020-11-10 14:45:12</last_find_time>
    <risk_type>3</risk_type>
    <scenario>失陷指标</scenario>
    <threat_type>Regsvr32</threat_type>
    <first_find_time>2017-09-22 11:15:00</first_find_time>
    <attck_stage>defense evasion</attck_stage>
</ThreatTypes>
<Intelligences>
    <last_find_time>2020-06-17 03:54:23</last_find_time>
    <threat_type_l2>恶意下载源</threat_type_l2>
    <first_find_time>2020-01-01 00:59:52</first_find_time>
    <source>aliyun</source>
</Intelligences>
<Intelligences>
    <last_find_time>2020-11-10 14:45:12</last_find_time>
    <threat_type_l2>regsvr32.exe执行恶意文件</threat_type_l2>
    <first_find_time>2017-09-22 11:15:00</first_find_time>
    <source>aliyun</source>
</Intelligences>
<Scenario>失陷指标</Scenario>
<Whois/>
<AttackCntByThreatType/>
<ThreatLevel>2</ThreatLevel>
<Confidence>98</Confidence>
<Domain>js.example.com</Domain>
<AttackPreferenceTop5/>
```

`JSON`格式

```
{
    "Context": "",
    "Basic": {
        "ip_cnt": "36",
        "domain": "example.com",
        "child_domain_cnt": "18",
        "sld_domain": "example.com",
        "malicious_ip_cnt": "28",
        "malicious_child_domain_cnt": "4"
    },
    "RequestId": "55B99BBE-AD29-4220-A650-A24F16C61071",
    "SslCert": "",
    "ThreatTypes": [
        {
            "threat_type_desc": "中控",
            "last_find_time": "2019-12-19 10:20:47",
            "risk_type": 3,
            "scenario": "失陷指标",
            "threat_type": "C&C Server",
            "first_find_time": "2019-06-20 22:18:58",
            "attck_stage": ""
        },
        {
            "threat_type_desc": "Regsvr32执行",
            "last_find_time": "2020-11-10 14:45:12",
            "risk_type": 3,
            "scenario": "失陷指标",
            "threat_type": "Regsvr32",
            "first_find_time": "2017-09-22 11:15:00",
            "attck_stage": "defense evasion"
        }
    ],
    "Intelligences": [
        {
            "last_find_time": "2020-06-17 03:54:23",
            "threat_type_l2": "恶意下载源",
            "first_find_time": "2020-01-01 00:59:52",
            "source": "aliyun"
        },
        {
            "last_find_time": "2020-11-10 14:45:12",
            "threat_type_l2": "regsvr32.exe执行恶意文件",
            "first_find_time": "2017-09-22 11:15:00",
            "source": "aliyun"
        }
    ],
    "Scenario": "失陷指标",
    "Whois": "",
    "AttackCntByThreatType": "",
    "ThreatLevel": 2,
    "Confidence": 98,
    "Domain": "js.example.com",
    "AttackPreferenceTop5": ""
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Sasti)查看更多错误码。

