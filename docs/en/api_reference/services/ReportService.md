# ReportService
ReportService acquires, creates, and deletes reports. <br>
It also includes an operation that acquires report download URLs.

#### WSDL
| environment | url |
|---|---|
| production  | https://location.im.yahooapis.jp/services/Vx.x/ReportService?wsdl |
| sandbox  | https://sandbox.im.yahooapis.jp/services/Vx.x/ReportService?wsdl |

#### Namespace
http://im.yahooapis.jp/V6

#### Service Overview
The following operations are provided:
- Get reports
- Add reports
- Delete reports
- Get the date of report completion

[Maximum number of report download job]
- Up to 30 report download jobs can be added for regular and proxy authentications combined.<br>
Example：<br>
If you have already saved 20 report download jobs for regular authentication, you can add a maximum of 10 jobs for proxy authentication.<br>
*If you wish to add more jobs though the upper saving limit is reached, delete some of the download jobs you already saved.<br>

[Notes]<br>
- Reports can be downloaded from the URL created with 'get' method.<br>
The URL is valid in the first 5 minutes after the status becomes COMPLETED.
- Any ad data without actual performance is not output for all report types.
- Report download jobs will be automatically deleted after a week (7 days) from requested.

#### Operation
Describes operations provided by ReportService.
## get
### Request
Acquires report related information. Download URL of reports can also be acquired by get method.

| Parameter | Requirement | Data Type | Description |
|---|---|---|---|
| selector | required | [ReportSelector](../data/ReportSelector.md) | Operation target report. |

##### Request Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="http://im.yahooapis.jp/V6">
    <SOAP-ENV:Header>
        <ns1:RequestHeader>
            <ns1:license>1111-1111-1111-1111</ns1:license>
            <ns1:apiAccountId>2222-2222-2222-2222</ns1:apiAccountId>
            <ns1:apiAccountPassword>password</ns1:apiAccountPassword>
        </ns1:RequestHeader>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <ns1:get>
            <ns1:selector>
                <ns1:accountId>1000000001</ns1:accountId>
                <ns1:reportIds>9000000001</ns1:reportIds>
                <ns1:reportIds>9000000002</ns1:reportIds>
                <ns1:reportIds>9000000003</ns1:reportIds>
                <ns1:reportJobIds>8000000001</ns1:reportJobIds>
                <ns1:reportJobIds>8000000002</ns1:reportJobIds>
                <ns1:reportJobIds>8000000003</ns1:reportJobIds>
                <ns1:reportJobStatuses>COMPLETED</ns1:reportJobStatuses>
                <ns1:reportJobStatuses>FAILED</ns1:reportJobStatuses>
                <ns1:paging>
                    <ns1:startIndex>1</ns1:startIndex>
                    <ns1:numberResults>20</ns1:numberResults>
                </ns1:paging>
            </ns1:selector>
        </ns1:get>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response
| Parameter | Data Type | Description |
|---|---|---|
| rval | [ReportPage](../data/ReportPage.md) | Container of report definitions to be acquired. | error | [Error](../data/Error.md) | An error. |

##### Response Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="http://im.yahooapis.jp/V6"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <SOAP-ENV:Header>
        <ns1:ResponseHeader>
            <ns1:service>ReportService</ns1:service>
            <ns1:remainingQuota>100</ns1:remainingQuota>
            <ns1:quotaUsedForThisRequest>1</ns1:quotaUsedForThisRequest>
            <ns1:timeTakenMillis>0.0173</ns1:timeTakenMillis>
        </ns1:ResponseHeader>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <ns1:getResponse>
            <ns1:rval>
                <ns1:totalNumEntries>3</ns1:totalNumEntries>
                <ns1:Page.Type>ReportPage</ns1:Page.Type>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:reportRecord>
                        <ns1:accountId>1000000001</ns1:accountId>
                        <ns1:reportJobId>8000000001</ns1:reportJobId>
                        <ns1:reportId>9000000001</ns1:reportId>
                        <ns1:reportName>SandboxAccountReport_csv</ns1:reportName>
                        <ns1:requestTime>20120403175909</ns1:requestTime>
                        <ns1:completeTime>20120403175910</ns1:completeTime>
                        <ns1:dateRangeType>CUSTOM_DATE</ns1:dateRangeType>
                        <ns1:dateRange>
                            <ns1:startDate>20120303</ns1:startDate>
                            <ns1:endDate>20120402</ns1:endDate>
                        </ns1:dateRange>
                        <ns1:status>COMPLETED</ns1:status>
                        <ns1:reportDownloadUrl>https: //sample.api.yahooapis.jp/report/V6.1/download/dqy0_L5Oa9vS5z2BzN9dBOrL.f.4oSOB1O81JI_UmMa98_SXxeo8eQ21TfimDDSuizf990IRIVDf3YPqW8u5Jw--</ns1:reportDownloadUrl>
                    </ns1:reportRecord>
                </ns1:values>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:reportRecord>
                        <ns1:accountId>1000000001</ns1:accountId>
                        <ns1:reportJobId>8000000002</ns1:reportJobId>
                        <ns1:reportId>9000000002</ns1:reportId>
                        <ns1:reportName>SandboxCampaignReport_csv</ns1:reportName>
                        <ns1:requestTime>20120403175908</ns1:requestTime>
                        <ns1:completeTime>20120403175909</ns1:completeTime>
                        <ns1:dateRangeType>YESTERDAY</ns1:dateRangeType>
                        <ns1:status>COMPLETED</ns1:status>
                        <ns1:reportDownloadUrl>https: //sample.api.yahooapis.jp/report/V6.1/download/dqy0_L5Oa9vS5z2BzN9dBOrL.f.4oSOB1O81JI_UmMa98_SXxeo8eQ21TfimDDSuizf990IRIVDf3YPqW8u5Jw--</ns1:reportDownloadUrl>                       
                     </ns1:reportRecord>
                </ns1:values>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:reportRecord>
                        <ns1:accountId>1000000001</ns1:accountId>
                        <ns1:reportJobId>8000000003</ns1:reportJobId>
                        <ns1:reportId>9000000003</ns1:reportId>
                        <ns1:reportName>SandboxAdgroupReport_csv</ns1:reportName>
                        <ns1:requestTime>20120403175911</ns1:requestTime>
                        <ns1:completeTime>20120403175912</ns1:completeTime>
                        <ns1:dateRangeType>YESTERDAY</ns1:dateRangeType>
                        <ns1:status>FAILED</ns1:status>
                        <ns1:jobErrorDetail>Over limit of file size.</ns1:jobErrorDetail>
                    </ns1:reportRecord>
                </ns1:values>
            </ns1:rval>
        </ns1:getResponse>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## mutate(ADD)
### Request
Creates a report.

| Parameter | Requirement | Value | Description |
|---|---|---|---|
| operations | required | [ReportOperation](../data/ReportOperation.md) | Displays operation target reports and operation content. |

##### Request Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="http://im.yahooapis.jp/V6">
    <SOAP-ENV:Header>
        <ns1:RequestHeader>
            <ns1:license>xxxx-xxxx-xxxx-xxxx</ns1:license>
            <ns1:apiAccountId>xxxx-xxxx-xxxx-xxxx</ns1:apiAccountId>
            <ns1:apiAccountPassword>password</ns1:apiAccountPassword>
        </ns1:RequestHeader>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <ns1:mutate>
            <ns1:operations>
                <ns1:operator>ADD</ns1:operator>
                <ns1:accountId>1000000001</ns1:accountId>
                <ns1:operand>
                    <ns1:reportId>9000000001</ns1:reportId>
                </ns1:operand>
                <ns1:operand>
                    <ns1:reportId>9000000002</ns1:reportId>
                </ns1:operand>
            </ns1:operations>
         </ns1:mutate>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response
| Field | Data Type | Description |
|---|---|---|
| rval | [ReportReturnValue](../data/ReportReturnValue.md) | Container of reports, including operation results. | error | [Error](../data/Error.md) | An error. |

##### Response Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="http://im.yahooapis.jp/V6"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <SOAP-ENV:Header>
        <ns1:ResponseHeader>
            <ns1:service>ReportService</ns1:service>
            <ns1:remainingQuota>100</ns1:remainingQuota>
            <ns1:quotaUsedForThisRequest>2</ns1:quotaUsedForThisRequest>
            <ns1:timeTakenMillis>0.0173</ns1:timeTakenMillis>
        </ns1:ResponseHeader>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <ns1:mutateResponse>
            <ns1:rval>
                <ns1:ListReturnValue.Type>ReportReturnValue</ns1:ListReturnValue.Type>
                <ns1:Operation.Type>ADD</ns1:Operation.Type>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:reportRecord>
                        <ns1:accountId>1000000001</ns1:accountId>
                        <ns1:reportJobId>8000000001</ns1:reportJobId>
                        <ns1:reportId>9000000001</ns1:reportId>
                        <ns1:reportName>SandboxAccountReport_csv</ns1:reportName>
                        <ns1:requestTime>20120403175909</ns1:requestTime>
                        <ns1:completeTime />
                        <ns1:dateRangeType>CUSTOM_DATE</ns1:dateRangeType>
                        <ns1:dateRange>
                            <ns1:startDate>20120303</ns1:startDate>
                            <ns1:endDate>20120402</ns1:endDate>
                        </ns1:dateRange>
                        <ns1:status>IN_PROGRESS</ns1:status>
                     </ns1:reportRecord>
                     <ns1:reportRecord>
                         <ns1:accountId>1000000001</ns1:accountId>
                         <ns1:reportJobId>8000000002</ns1:reportJobId>
                         <ns1:reportId>9000000002</ns1:reportId>
                         <ns1:reportName>SandboxCampaignReport_csv</ns1:reportName>
                         <ns1:requestTime>20120403175908</ns1:requestTime>
                         <ns1:completeTime />
                         <ns1:dateRangeType>YESTERDAY</ns1:dateRangeType>
                         <ns1:status>IN_PROGRESS</ns1:status>
                    </ns1:reportRecord>
                </ns1:values>
            </ns1:rval>
        </ns1:mutateResponse>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## mutate(REMOVE)
### Request
Deletes a report

| Parameter | Requirement | Value | Description |
|---|---|---|---|
| operations | required | [ReportOperation](../data/ReportOperation.md) | Displays operation target reports and operation content. |

##### Request Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
xmlns:ns1="http://im.yahooapis.jp/V6">
    <SOAP-ENV:Header>
        <ns1:RequestHeader>
            <ns1:license>xxxx-xxxx-xxxx-xxxx</ns1:license>
            <ns1:apiAccountId>xxxx-xxxx-xxxx-xxxx</ns1:apiAccountId>
            <ns1:apiAccountPassword>password</ns1:apiAccountPassword>
        </ns1:RequestHeader>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <ns1:mutate>
            <ns1:operations>
                <ns1:operator>REMOVE</ns1:operator>
                <ns1:accountId>1000000001</ns1:accountId>                
                <ns1:operand>
                    <ns1:reportJobId>8000000001</ns1:reportJobId>                     
                </ns1:operand>
                <ns1:operand>
                    <ns1:reportJobId>8000000002</ns1:reportJobId>                     
                </ns1:operand>
            </ns1:operations>
        </ns1:mutate>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response
| Field | Data Type | Description |
|---|---|---|
| rval | [ReportReturnValue](../data/ReportReturnValue.md) | Container of reports, including operation results. | error | [Error](../data/Error.md) | An error. |

##### Response Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="http://im.yahooapis.jp/V6"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <SOAP-ENV:Header>
        <ns1:ResponseHeader>
            <ns1:service>ReportService</ns1:service>
            <ns1:remainingQuota>100</ns1:remainingQuota>
            <ns1:quotaUsedForThisRequest>2</ns1:quotaUsedForThisRequest>
            <ns1:timeTakenMillis>0.0173</ns1:timeTakenMillis>
        </ns1:ResponseHeader>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <ns1:mutateResponse>
            <ns1:rval>
                <ns1:ListReturnValue.Type>ReportReturnValue</ns1:ListReturnValue.Type>
                <ns1:Operation.Type>REMOVE</ns1:Operation.Type>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:reportRecord>
                        <ns1:reportJobId>8000000001</ns1:reportJobId>
                    </ns1:reportRecord>
                </ns1:values>
                <ns1:values>
                    <ns1:operationSucceeded>true</ns1:operationSucceeded>
                    <ns1:reportRecord>
                        <ns1:reportJobId>8000000002</ns1:reportJobId>
                    </ns1:reportRecord>
                </ns1:values>
            </ns1:rval>
        </ns1:mutateResponse>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## getClosedDate
### Request
Acquires date of report completion.

| Parameter | Requirement | Data Type | Description |
|---|---|---|---|
| selector | required | [ReportClosedDateSelector](../data/ReportClosedDateSelector.md) | Assigns operation target reports. |

##### Request Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="http://im.yahooapis.jp/V6">
    <SOAP-ENV:Header>
        <ns1:RequestHeader>
            <ns1:license>xxxx-xxxx-xxxx-xxxx</ns1:license>
            <ns1:apiAccountId>xxxx-xxxx-xxxx-xxxx</ns1:apiAccountId>
            <ns1:apiAccountPassword>password</ns1:apiAccountPassword>
        </ns1:RequestHeader>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <ns1:getClosedDate>
            <ns1:selector>
                <ns1:accountId>1000000001</ns1:accountId>
            </ns1:selector>
        </ns1:getClosedDate>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response
| Parameter | Data Type | Description |
|---|---|---|
| rval | [ReportClosedDateValue](../data/ReportClosedDateValue.md) | Container of information to be acquired. |

##### Response Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="http://im.yahooapis.jp/V6"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <SOAP-ENV:Header>
        <ns1:ResponseHeader>
            <ns1:service>ReportService</ns1:service>
            <ns1:remainingQuota>100</ns1:remainingQuota>
            <ns1:quotaUsedForThisRequest>1</ns1:quotaUsedForThisRequest>
            <ns1:timeTakenMillis>0.0173</ns1:timeTakenMillis>
        </ns1:ResponseHeader>
    </SOAP-ENV:Header>
    <SOAP-ENV:Body>
        <ns1:getClosedDateResponse>
            <ns1:rval>
                <ns1:operationSucceeded>true</ns1:operationSucceeded>
                <ns1:closedDate>20120303</ns1:closedDate>
            </ns1:rval>
        </ns1:getClosedDateResponse>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
<a rel="license" href="http://creativecommons.org/licenses/by-nd/2.1/jp/"><img alt="クリエイティブ・コモンズ・ライセンス" style="border-width:0" src="https://i.creativecommons.org/l/by-nd/2.1/jp/88x31.png" /></a><br />この 作品 は <a rel="license" href="http://creativecommons.org/licenses/by-nd/2.1/jp/">クリエイティブ・コモンズ 表示 - 改変禁止 2.1 日本 ライセンスの下に提供されています。</a>
