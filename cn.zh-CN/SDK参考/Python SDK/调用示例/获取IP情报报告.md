# 获取IP情报报告

本文档介绍如何使用Python SDK获取全球范围内IP情报相关的报告。

IP情报报告内容包含了IP地址相关地理位置信息、域名解析信息、威胁类型、相关攻击团伙或安全事件信息等。详细内容请参见[DescribeIpReport](/cn.zh-CN/API参考/DescribeIpReport.md)接口的返回数据。

## 前提条件

开始运行示例脚本前，请确保您已完成以下准备工作：

-   已开通阿里云官网账号。
-   已生成AccessKey（用于使用SDK时进行身份验证）。

    确保您当前账号下已创建了AccessKey ID和AccessKey Secret。

-   已开通阿里云威胁情报服务。

## 操作步骤

1.  [安装Python SDK](/cn.zh-CN/SDK参考/Python SDK/安装Python SDK.md)。更多详细内容请参见[快速开始]()。
2.  运行以下示例脚本，调用IP情报接口。

    ```
    from aliyunsdkcore.client import AcsClient
    from aliyunsdkcore.request import CommonRequest
    client = AcsClient('{your_access_key_id}', '{your_access_key_secret}', 'cn-zhangjiakou')
    request = CommonRequest()
    request.set_domain('sasti.aliyuncs.com')
    request.set_version('2020-05-12')
    request.set_action_name('DescribeIpReport')
    # or:
    # request = CommonRequest(domain='sasti.aliyuncs.com'', version='2020-05-12', action_name='DescribeIpReport')
    request.add_query_param('Ip', '8.8.8.8')
    request.add_query_param('Field', 'Tags,Whois,ThreatTypes,Intelligences,AttackPreferenceTop5,AttackCntByThreatType')
    response = client.do_action_with_exception(request)
    ```

    返回示例如下：

    ```
    {
        "code":200,
        "message":"success",
        "data":{
            "Whois": "",
            "AttackCntByThreatType": [
                {
                    "event_cnt": 60383,
                    "threat_type": "主机层入侵"
                }
            ],
            "RequestId": "FBC41D8F-F62E-432E-A1F4-C7C1EB85BFA8",
            "ThreatLevel": 2,
            "Ip": {
                "country": "拉脱维亚",
                "province": "里加",
                "city": "",
                "ip": "195.1.3.3",
                "isp": "",
                "asn": "41390",
                "asn_label": "RN-Data-LV - RN Data SIA, LV"
            },
            "ThreatTypes": [
                {
                    "threat_type_desc": "恶意下载源",
                    "last_find_time": "2020-08-26 02:42:58",
                    "threat_type": "Malicious Source"
                }
            ],
            "Intelligences": [
                {
                    "ip": "195.1.2.3",
                    "gmt_last": "2020-08-26 02:42:58",
                    "threat_type_l3": "恶意下载源",
                    "source": "Aliyun"
                }
            ],
            "AttackPreferenceTop5": ""
       }
    }
    ```


