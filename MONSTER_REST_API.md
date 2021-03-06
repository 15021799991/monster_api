# REST API

## API参考  

### 币币行情 API 

获取币币行情数据  

1.Post /monster/coin/v1/price   获取币币行情

URL `https://www.monster.one/monster/coin/v1/price`	

示例	

```
# Request
Post https://www.monster.one/monster/coin/v1/price
{
     "appId": "mst236153cd620g3fbb",
     "appSign": "D0F0165EF45E7FECA2A1A8C0DC246822",
     "nonceStr": "112ae6eb-986b-43b0-9a99-3be317b7ea2f", 
     "timestamp": "1537238390607",
     "symbol": "MR/ETH"
}
```

请求值说明	

```
appId: 认证id
appSign: 签名数据
nonceStr: 随机字符串
timestamp: 时间戳
symbol: 币对
```

```
# Response
{
    "volumn": 97.75397492
    "amount": 0.06209088,
    "begin": 0.00085,
    "buy": 0.00015,
    "sell": 0.00085,
    "end": 0.00015,
    "high": 0.00085,
    "low": 0.00015,
    "respCode": {
        "code": "00000",
        "desc": "成功"
    },
    "date": 1537239707143,
    "success": true,
}
```

返回值说明	

```
date: 返回数据时服务器时间
buy: 买一价
high: 最高价
last: 最新成交价
low: 最低价
sell: 卖一价
volumn: 成交量(最近的24小时)
amount: 交易额
begin: 开盘价
end: 收盘价
```


2.Post /monster/coin/v1/trade   币币交易下单

URL `https://www.monster.one/monster/coin/v1/trade`	

示例	

```
# Request
Post https://www.monster.one//monster/coin/v1/trade
{
     "appId": "mst233153cd620g3fbb",
     "appSign": "D0F0164EF45E7FECA2A1A8C0DC246822",
     "nonceStr": "112ae7eb-986b-43b0-9a99-3be317b7ea2f", 
     "timestamp": "1537238390607",
     "symbol": "MR/ETH",
     "type": "B",
     "amount": "1.0",
     "price": "1.0"
}
```

请求值说明	

```
appId: 认证id
appSign: 签名数据
nonceStr: 随机字符串
timestamp: 时间戳
symbol: 币对
type: 订单类型('B':买单, 'S': 卖单)
amount: 数量
price: 价格
```

```
# Response
{
    "orderId": "ORDER201809181423497609581548510",
    "respCode": {
        "code": "00000",
        "desc": "成功"
    },
    "success": true
}
```

返回值说明	

```
orderId: 订单编号
```


3.Post /monster/coin/v1/cancel_trade   币币交易撤单

URL `https://www.monster.one/monster/coin/v1/cancel_trade`

示例	

```
# Request
Post https://www.monster.one//monster/coin/v1/cancel_trade
{
     "appId": "mst233153cd620g3fbb",
     "appSign": "D0F0164EF45E7FECA2A1A8C0DC246822",
     "nonceStr": "112ae7eb-986b-43b0-9a99-3be317b7ea2f", 
     "timestamp": "1537238390607",
     "orderId:": "ORDER201809181145351326674380179"
}
```

请求值说明	

```
appId: 认证id
appSign: 签名数据
nonceStr: 随机字符串
timestamp: 时间戳
orderId: 订单编号
```

```
# Response
{
    "respCode": {
        "code": "00000",
        "desc": "成功"
    },
    "success": true
}
```

