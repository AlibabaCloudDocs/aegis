# DescribeIpReport

调用DescribeIpReport获取IP地址相关地理位置信息、域名解析信息、威胁类型、相关攻击团伙或安全事件信息。

默认接口请求频率限制：100次/秒。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Sasti&api=DescribeIpReport&type=RPC&version=2020-05-12)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeIpReport|系统规定参数。

 取值：**DescribeIpReport**。 |
|Ip|String|是|X.X.X.X|要查询的IP。 |
|Field|String|否|TagsThreatTypes,Intelligences,AttackPreferenceTop5,AttackCntByThreatType|要查询的字段。可以输入多个参数值，以英文逗号分隔。

 取值：

 -   **ThreatTypes**：威胁情报事件的类型。
-   **Intelligences**：威胁情报事件。
-   **AttackPreferenceTop5**：被攻击的网站所属的Top 5行业。
-   **AttackCntByThreatType**：服务器遭受的攻击次数。
-   **为空**：表示仅返回域名、威胁等级、域名的基础信息、域名Whois信息和SSL证书信息。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|AttackCntByThreatType|String|\[\{"event\_cnt": 2536, "threat\_type": "应用层入侵"\}\]|不同攻击阶段的攻击次数。

 该参数使用JSON数组表示，数组中的字段含义说明如下：

 字段含义：

 -   **event\_cnt**：攻击次数。
-   **threat\_type**：攻击所属 ATT&CK 阶段。 |
|AttackPreferenceTop5|String|\{"event\_cnt":586,"industry\_name":"Gaming","gmt\_last\_attack":"2020-06-14 21:54:04"\}\]|该 IP 攻击目标的 Top 5 行业分布。

 字段含义：

 -   **event\_cnt**：攻击次数。
-   **industry\_name**：攻击行业类别。
-   **gmt\_last\_attack**：最后攻击活跃时间。 |
|Intelligences|String|\[\{"last\_find\_time": "2021-01-29 10:50:00", "threat\_type\_l2": "一句话木马扫描", "first\_find\_time": "2021-01-29 00:28:43", "source": "aliyun"\}\]|威胁情报事件信息。

 字段含义：

 -   **source**：威胁情报事件的来源。
-   **first\_find\_time**：首次发现时间。
-   **last\_find\_time**：最后活跃时间。
-   **threat\_type\_l2**：威胁情报详细标签，可以使家族团伙的标签，例如Mykings，可以使攻击手法，例如SQL注入，描述了这个IP具体的威胁基本标签。 |
|Ip|String|\{ "country": "美国", "province": "加利福尼亚州", "city": "洛杉矶", "ip": "X.X.X.X", "isp": "example.com", "idc\_name": "\*", "asn": "XXXXXX", "asn\_label": "VNET" \}|IP的基础信息。

 字段含义：

 -   **ip**：IP地址
-   **idc\_name**：IDC服务器
-   **isp**：运营商
-   **country**：国家
-   **province**：省份
-   **city**：城市
-   **asn**：ASN（Autonomous System Numbers，自治系统编号）
-   **asn\_label**：ASN名称 |
|RequestId|String|BE036526-FE84-46A8-9165-F086E9810E2F|阿里云为此次调用请求生成的唯一标识符。 |
|ThreatLevel|String|"3"|威胁等级，命中以后造成的危害等级，恶意的等级有高危、中危、低危、正常和未知五个等级。使用的时候可以结合置信度（Confidence字段）来使用，对高危并且高置信度的数据进行拦截。对于正常（即白名单）的类型可以进行放行。

 取值：

 -   **-1**：未知
-   **0**：正常，即白名单，可以放行
-   **1**：低危
-   **2**：中危
-   **3**：高危 |
|Whois|String|\{ "serial\_number": "18395475168054001104",...\}|IP 的Whois信息。 |
|ThreatTypes|String|\[\{"threat\_type\_desc": "漏洞扫描", "last\_find\_time": "2021-01-29 10:50:00", "risk\_type": 2, "scenario": "攻击指标", "threat\_type": "Exploit Scanning", "first\_find\_time": "2021-01-29 00:28:43", "attck\_stage": "initial access" \}, \{"threat\_type\_desc": "SQL注入", "last\_find\_time": "2021-02-28 00:18:40", "risk\_type": 3, "scenario": "攻击指标", "threat\_type": "SQL Injection", "first\_find\_time": "2021-02-25 15:54:09", "attck\_stage": "" \}\]|从威胁情报、安全事件分析出来的风险标签，例如远程控制、恶意软件等。

 字段含义：

 -   **threat\_type**: 英文标签名称
-   **threat\_type\_desc**: 中文标签含义
-   **risk\_type**: 威胁级别（3高危，2中危，1可疑，0正常，-1未知）
-   **scenario**: 适用的安全场景（攻击指标、失陷指标）
-   **first\_find\_time**: 首次标记时间
-   **last\_find\_time**: 最后标记时间
-   **attck\_stage**: 所属的ATT&CK攻击阶段

 常见的威胁标签（threat\_type字段）取值：

 -   **IDC**：IDC服务器
-   **Tor**：暗网
-   **Proxy**：代理
-   **NAT**：公共出口
-   **Miner Pool**：矿池
-   **C&C Server**：命令与控制服务器
-   **Brute Force**：暴力破解
-   **Malicious Login**：恶意登录
-   **WEB Attack**：WEB攻击
-   **Malicious Source**：恶意下载源
-   **Network Service Scanning**：网络服务扫描
-   **Exploit**：漏洞利用
-   **Network Share Discovery**：网络共享发现
-   **Scheduled Task**：Windows计划任务
-   **BITS Jobs**：BITS作业
-   **Command-Line Interface**：恶意命令
-   **Mshta执行**：Mshta执行
-   **Regsvr32**：Regsvr32执行
-   **Signed Binary Proxy Execution**：签名的二进制代理执行
-   **Local Job Scheduling**：Linux计划任务
-   **Rundll32**：Rundll32执行
-   **Web Shell**：WebShell通信
-   **SQL Injection**：SQL注入攻击
-   **XSS Attack**：XSS攻击 |
|Confidence|String|"98"|对判定结果的置信程度，置信度值越高，说明对判定结果（判定结果是ThreatLevel字段）有多少信心。通常认为置信度大于90的结果可以作为精准结果，对于恶意的高威胁等级的指标可以进行拦截。对于正常（ThreatLevel等于0）的结果可以放行。

 取值范围0-100：

 -   **\[90-100\)**：认为该情报是高可信的，可以作为拦截或者放行依据，如果ThreatLevel表示高危（ThreatLevel=3）则可拦截，如果ThreatLevel表示正常（ThreatLevel=0）。
-   **\[60-90\)**：认为情报有一定的可行，但是还不能达到拦截指标，通常是有一些恶意行为的IP。可作为安全分析运营的辅助依据。 |
|Context|String|""|暂空，保留字段 |
|Scenario|String|"攻击指标"|该 IP 所适用的攻击场景。

 取值：

 -   **攻击指标**：该 IP 会主动发起攻击流量，可以在防火墙、WAF 等安全设备进行匹配由外向内主动发起的源，并根据标签进行拦截。
-   **失陷指标**：攻击者植入的脚本或者恶意代码会回联该 IP 进行通讯和数据传输，如果在流量或者日志中发现该 IP 意味着当前主机已经被攻破。
-   **信息数据**：白名单等类型，该字段为信息数据，不具有风险场景 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeIpReport
&Ip=X.X.X.X
&Field=ThreatTypes%2CIntelligences%2CAttackPreferenceTop5%2CAttackCntByThreatType
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<Context/>
<Whois/>
<AttackCntByThreatType>
    <event_cnt>2536</event_cnt>
    <threat_type>应用层入侵</threat_type>
</AttackCntByThreatType>
<RequestId>A736BB54-4819-475E-813B-B466968B18B9</RequestId>
<ThreatLevel>3</ThreatLevel>
<Confidence>98</Confidence>
<Ip>
    <country>美国</country>
    <province>加利福尼亚州</province>
    <city>洛杉矶</city>
    <ip>X.X.X.X</ip>
    <isp>example.com</isp>
    <idc_name>*</idc_name>
    <asn>XXXXXX</asn>
    <asn_label>VNET</asn_label>
</Ip>
<ThreatTypes>
    <threat_type_desc>SQL注入</threat_type_desc>
    <last_find_time>2021-02-28 00:18:40</last_find_time>
    <risk_type>3</risk_type>
    <scenario>攻击指标</scenario>
    <threat_type>SQL Injection</threat_type>
    <first_find_time>2021-02-25 15:54:09</first_find_time>
    <attck_stage/>
</ThreatTypes>
<ThreatTypes>
    <threat_type_desc>网络服务扫描</threat_type_desc>
    <last_find_time>2021-03-17 23:52:39</last_find_time>
    <risk_type>2</risk_type>
    <scenario>攻击指标</scenario>
    <threat_type>Network Service Scanning</threat_type>
    <first_find_time>2020-11-09 02:04:25</first_find_time>
    <attck_stage>initial access</attck_stage>
</ThreatTypes>
<Intelligences>
    <last_find_time>2021-01-29 10:50:00</last_find_time>
    <threat_type_l2>一句话木马扫描</threat_type_l2>
    <first_find_time>2021-01-29 00:28:43</first_find_time>
    <source>aliyun</source>
</Intelligences>
<Intelligences>
    <last_find_time>2021-02-28 00:18:40</last_find_time>
    <threat_type_l2>SQL注入攻击</threat_type_l2>
    <first_find_time>2021-02-25 15:54:09</first_find_time>
    <source>aliyun</source>
</Intelligences>
<Intelligences>
    <last_find_time>2021-03-12 14:59:18</last_find_time>
    <threat_type_l2>请求etcpasswd</threat_type_l2>
    <first_find_time>2021-03-12 14:59:18</first_find_time>
    <source>aliyun</source>
</Intelligences>
<AttackPreferenceTop5>
    <event_cnt>4</event_cnt>
    <industry_name>互联网</industry_name>
    <gmt_last_attack>2021-02-23 08:01:11</gmt_last_attack>
</AttackPreferenceTop5>
<AttackPreferenceTop5>
    <event_cnt>42</event_cnt>
    <industry_name>零售</industry_name>
    <gmt_last_attack>2021-03-17 12:00:21</gmt_last_attack>
</AttackPreferenceTop5>
<Scenario>攻击指标</Scenario>
```

`JSON`格式

```
{
    "Context": "",
    "Whois": "",
    "AttackCntByThreatType": [
        {
            "event_cnt": 2536,
            "threat_type": "应用层入侵"
        }
    ],
    "RequestId": "A736BB54-4819-475E-813B-B466968B18B9",
    "ThreatLevel": "3",
    "Confidence": "98",
    "Ip": {
        "country": "美国",
        "province": "加利福尼亚州",
        "city": "洛杉矶",
        "ip": "X.X.X.X",
        "isp": "example.com",
        "idc_name": "*",
        "asn": "XXXXXX",
        "asn_label": "VNET"
    },
    "ThreatTypes": [
        {
            "threat_type_desc": "SQL注入",
            "last_find_time": "2021-02-28 00:18:40",
            "risk_type": 3,
            "scenario": "攻击指标",
            "threat_type": "SQL Injection",
            "first_find_time": "2021-02-25 15:54:09",
            "attck_stage": ""
        },
        {
            "threat_type_desc": "网络服务扫描",
            "last_find_time": "2021-03-17 23:52:39",
            "risk_type": 2,
            "scenario": "攻击指标",
            "threat_type": "Network Service Scanning",
            "first_find_time": "2020-11-09 02:04:25",
            "attck_stage": "initial access"
        }
    ],
    "Intelligences": [
        {
            "last_find_time": "2021-01-29 10:50:00",
            "threat_type_l2": "一句话木马扫描",
            "first_find_time": "2021-01-29 00:28:43",
            "source": "aliyun"
        },
        {
            "last_find_time": "2021-02-28 00:18:40",
            "threat_type_l2": "SQL注入攻击",
            "first_find_time": "2021-02-25 15:54:09",
            "source": "aliyun"
        },
        {
            "last_find_time": "2021-03-12 14:59:18",
            "threat_type_l2": "请求etcpasswd",
            "first_find_time": "2021-03-12 14:59:18",
            "source": "aliyun"
        }
    ],
    "AttackPreferenceTop5": [
        {
            "event_cnt": 4,
            "industry_name": "互联网",
            "gmt_last_attack": "2021-02-23 08:01:11"
        },
        {
            "event_cnt": 42,
            "industry_name": "零售",
            "gmt_last_attack": "2021-03-17 12:00:21"
        }
    ],
    "Scenario": "攻击指标"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Sasti)查看更多错误码。

