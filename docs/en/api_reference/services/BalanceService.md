# BalanceService
Use this service to retrieve account balance
#### WSDL
| environment | url |
|---|---|
| production  | https://location.im.yahooapis.jp/services/Vx.x/BalanceService?wsdl |
| sandbox  | https://sandbox.im.yahooapis.jp/services/Vx.x/BalanceService?wsdl |
#### Namespace
http://im.yahooapis.jp/V6
#### Service Overview
Offers a budget acquisition function.
#### Operation
Describes operations provided by BalanceService.
## get
### Request
Defines a budget acquisition target.

| Parameter | Requirement | Data Type | Description | 
|---|---|---|---|
| selector | required | [BalanceSelector](../data/BalanceSelector.md) | Defines a target to acquire a budget.  | 

##### Request Sample
```xml
<?xml version="1.0" encoding="UTF-8"?> 
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://im.yahooapis.jp/V6"> 
  <SOAP-ENV:Header> 
    <ns1:RequestHeader> 
      <ns1:license>xxxxxxxxxxxxxxx</ns1:license> 
      <ns1:apiAccountId>xxxxxxxxxxxxxxx</ns1:apiAccountId> 
      <ns1:apiAccountPassword>password</ns1:apiAccountPassword> 
    </ns1:RequestHeader> 
  </SOAP-ENV:Header> 
  <SOAP-ENV:Body> 
    <ns1:get> 
      <ns1:selector> 
        <ns1:accountId>1111111111</ns1:accountId> 
      </ns1:selector> 
    </ns1:get> 
  </SOAP-ENV:Body> 
</SOAP-ENV:Envelope>
```

##### Request Sample (On-Behalf-Of Account) 
```xml
<?xml version="1.0" encoding="UTF-8"?> 
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://im.yahooapis.jp/V6"> 
  <SOAP-ENV:Header> 
    <ns1:RequestHeader> 
      <ns1:license>xxxxxxxxxxxxxxx</ns1:license> 
      <ns1:apiAccountId>xxxxxxxxxxxxxxx</ns1:apiAccountId> 
      <ns1:apiAccountPassword>password</ns1:apiAccountPassword> 
      <ns1:accountId>1111111111</ns1:accountId> 
      <ns1:onBehalfOfAccountId>xxxxxxxxxxxxxxx</ns1:onBehalfOfAccountId> 
      <ns1:onBehalfOfPassword>password2</ns1:onBehalfOfPassword> 
    </ns1:RequestHeader> 
  </SOAP-ENV:Header> 
  <SOAP-ENV:Body> 
    <ns1:get> 
      <ns1:selector> 
        <ns1:accountId>1111111111</ns1:accountId> 
      </ns1:selector> 
    </ns1:get> 
  </SOAP-ENV:Body> 
</SOAP-ENV:Envelope>
```

### Response
| Parameter | Data Type | Description | 
|---|---|---|
| rval | [BalancePage](../data/BalancePage.md) | A container that stores results. | 
<Request Sample>
```xml
<?xml version="1.0" encoding="UTF-8"?> 
<SOAP-ENV:Envelope
    xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
    xmlns:ns1="http://im.yahooapis.jp/V6"> 
    <SOAP-ENV:Header> 
        <ns1:ResponseHeader> 
            <ns1:service>BalanceService</ns1:service> 
            <ns1:remainingQuota>100</ns1:remainingQuota> 
            <ns1:quotaUsedForThisRequest>1</ns1:quotaUsedForThisRequest> 
            <ns1:timeTakenMillis>0.0173</ns1:timeTakenMillis> 
        </ns1:ResponseHeader> 
    </SOAP-ENV:Header> 
    <SOAP-ENV:Body> 
        <ns1:getResponse> 
            <ns1:rval> 
                <ns1:totalNumEntries>1</ns1:totalNumEntries> 
                <ns1:Page.Type>BalancePage</ns1:Page.Type> 
                <ns1:values> 
                    <ns1:operationSucceeded>true</ns1:operationSucceeded> 
                    <ns1:balance> 
                        <ns1:accountId>1000000000</ns1:accountId> 
                        <ns1:balance>1000000</ns1:balance> 
                    </ns1:balance> 
                </ns1:values> 
            </ns1:rval> 
        </ns1:getResponse> 
    </SOAP-ENV:Body> 
</SOAP-ENV:Envelope>
```
<a rel="license" href="http://creativecommons.org/licenses/by-nd/2.1/jp/"><img alt="クリエイティブ・コモンズ・ライセンス" style="border-width:0" src="https://i.creativecommons.org/l/by-nd/2.1/jp/88x31.png" /></a><br />この 作品 は <a rel="license" href="http://creativecommons.org/licenses/by-nd/2.1/jp/">クリエイティブ・コモンズ 表示 - 改変禁止 2.1 日本 ライセンスの下に提供されています。</a>
