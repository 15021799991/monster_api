# WEBSOCKET API


## WEBSOCKET服务地址:

	WEBSOCKET服务连接地址: wss://www.monster.one/websocket(暂未开放)


## WEBSOCKET SUBSCRIBE说明：
	
	客户端通过STOMP订阅服务器的TOPIC消息，目前开发接口是公共开放接口，只需要保证订阅路径正确


## WEBSOCKET JAVA EXAMPLE:
	
	//WEBSOCKET连接和订阅地址
	static final WEBSOCKET_CONNECT = "wss://www.monster.one/websocket"
	static final WEBSOCKET_TOPIC_PRICE = "/topic/allPrice"

	//WEBSOCKET STOMP CLIENT问题
	WebSocketStompClient webSocketStompClient 
				= new WebSocketStompClient(new SockJsClient(
					Arrays.asList(new WebSocketTransport(new StandardWebSocketClient())));
	webSocketStompClient.setTaskScheduler(new DefaultManagedTaskScheduler());

	//WEBSOCKET连接和订阅
    StompSession stompSession =
        webSocketStompClient.connect(WEBSOCKET_CONNECT,
            new StompSessionHandlerAdapter(){}).get(3, TimeUnit.SECONDS);
    stompSession.subscribe(WEBSOCKET_TOPIC_ALL_Price, new SimpleStompFrameHandler());

    说明：
    (1) WEBSOCKET会话和消息处理，由用户根据自身的业务需求进行编写。
    (2) MONSTER WEBSOCKET服务基于STOMP协议实现。
    (3) 以上为JAVA样例，用户需根据使用编程语言的不同，来编写具体的调用代码。
    


## WEBSOCKET API参考 

### 单币行情 API  

1.Subscribe /topic/price/{coinPair} 单币行情

示例	

```
# Request

Subscribe /topic/price/{coinPair}

```

请求值说明	

```
coinPair: MON/ETH(可以使用怪兽市场中存在的各类币对)
```

```
# Response
[
	{
		"amount": "143.41094458",
		"begin": "0.00017988",
		"buy": "0.00017980",
		"date": 1539314358946,
		"end": "0.00017990",
		"high": "0.00017991",
		"low": "0.00017981",
		"sell": "0.00017992",
		"symbol": "MR/ETH",
		"volumn": "797350.48359411"
	}
]

```

返回值说明	

```
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


### 全币种行情 API  

2.Subscribe /topic/allPrice   所有币币行情

示例	

```
# Request

Subscribe /topic/allPrice

```

请求值说明	

```
该接口为公共接口，无需请求参数，只需通过WEBSOCKET订阅即可，具体可参考WEBSOCKET JAVA EXAMPLE。
```

```
# Response
[
	{
		"amount": "143.41094458",
		"begin": "0.00017988",
		"buy": "0.00017980",
		"date": 1539314358946,
		"end": "0.00017990",
		"high": "0.00017991",
		"low": "0.00017981",
		"sell": "0.00017992",
		"symbol": "MR/ETH",
		"volumn": "797350.48359411"
	}, {
		"amount": "6623.21863139",
		"begin": "0.00146819",
		"buy": "0.00100000",
		"date": 1539314358959,
		"end": "0.00190553",
		"high": "0.00199981",
		"low": "0.00100012",
		"sell": "0.00200000",
		"symbol": "MON/ETH",
		"volumn": "4314114.10881028"
	}, {
		"amount": "104.23230972",
		"begin": "29.20888889",
		"buy": "29.04440000",
		"date": 1539314358974,
		"end": "29.19026549",
		"high": "29.47982063",
		"low": "28.98684211",
		"sell": "29.46429203",
		"symbol": "BTC/ETH",
		"volumn": "3.57031718"
	}
]

```

返回值说明	

```
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


### 币对K线 API  

3.Subscribe /topic/kline/{coinPair}  币对K线

示例	

```
# Request

Subscribe /topic/kline/{coinPair}

```

请求值说明	

```
coinPair: MON/ETH(可以使用怪兽市场中存在的各类币对)
```

```
# Response
[
	{
		"coinPairId": "30003",
		"klineType": "4",
		"barTime": "20181120100000",
		"barTimeLong": 1542679200000,
		"beginPrice": 0.02000000,
		"endPrice": 0.02000000,
		"maxPrice": 0.02000000,
		"minPrice": 0.02000000,
		"totalVolume": 0,
		"totalAmount": 0
	}, {
		"coinPairId": "30003",
		"klineType": "5",
		"barTime": "20181120000000",
		"barTimeLong": 1542643200000,
		"beginPrice": 0.02000000,
		"endPrice": 0.02000000,
		"maxPrice": 0.02000000,
		"minPrice": 0.02000000,
		"totalVolume": 0,
		"totalAmount": 0
	}, {
		"coinPairId": "30003",
		"klineType": "1",
		"barTime": "20181120102000",
		"barTimeLong": 1542680400000,
		"beginPrice": 0.02000000,
		"endPrice": 0.02000000,
		"maxPrice": 0.02000000,
		"minPrice": 0.02000000,
		"totalVolume": 0,
		"totalAmount": 0
	}, {
		"coinPairId": "30003",
		"klineType": "3",
		"barTime": "20181120100000",
		"barTimeLong": 1542679200000,
		"beginPrice": 0.02000000,
		"endPrice": 0.02000000,
		"maxPrice": 0.02000000,
		"minPrice": 0.02000000,
		"totalVolume": 0,
		"totalAmount": 0
	}, {
		"coinPairId": "30003",
		"klineType": "0",
		"barTime": "20181120102000",
		"barTimeLong": 1542680400000,
		"beginPrice": 0.02000000,
		"endPrice": 0.02000000,
		"maxPrice": 0.02000000,
		"minPrice": 0.02000000,
		"totalVolume": 0,
		"totalAmount": 0
	}, {
		"coinPairId": "30003",
		"klineType": "2",
		"barTime": "20181120101500",
		"barTimeLong": 1542680100000,
		"beginPrice": 0.02000000,
		"endPrice": 0.02000000,
		"maxPrice": 0.02000000,
		"minPrice": 0.02000000,
		"totalVolume": 0,
		"totalAmount": 0
	}, {
		"coinPairId": "30003",
		"klineType": "6",
		"barTime": "20181118000000",
		"barTimeLong": 1542470400000,
		"beginPrice": 0.02000000,
		"endPrice": 0.02000000,
		"maxPrice": 0.02000000,
		"minPrice": 0.02000000,
		"totalVolume": 0,
		"totalAmount": 0
	}, {
		"coinPairId": "30003",
		"klineType": "7",
		"barTime": "20181101000000",
		"barTimeLong": 1541001600000,
		"beginPrice": 0.00200000,
		"endPrice": 0.02000000,
		"maxPrice": 0.02000000,
		"minPrice": 0.00200000,
		"totalVolume": 900.00000000,
		"totalAmount": 3.60000000
	}
]

```

返回值说明	

```
coinPairId: 币对ID
klineType: K线类型("0":"1分钟", "1":"5分钟", "2":"15分钟", "3":"30分钟", "4":"1小时", "5":"1天", "6":"1周", "7":"1月")
barTime: K线时间
barTimeLong: K线时长
beginPrice: 开盘价
endPrice: 收盘价
maxPrice: 最高价
minPrice: 最低价
totalVolume: 成交量
totalAmount: 交易额
dealTime: 处理时间
beginTime: 开始时间
endTime: 结束时间
createTime: 创建时间
modifyTime: 修改时间

```


4.Subscribe /topic/depth/{coinPair}  币对深度

示例	

```
# Request

Subscribe /topic/depth/{coinPair}

```

请求值说明	

```
coinPair: MON/ETH(可以使用怪兽市场中存在的各类币对)
```

```
# Response
[
	{
		"coinPairId": "30003",
		"buySellType": "B",
		"orderPrice": 10.0,
		"orderVolume": 100.0,
		"createTime": 1542107383000
	}
]

```

返回值说明	

```
coinPairId: 币对ID
buySellType: 买卖类型("B":买, "S":卖)
orderPrice: 成交价
orderVolume: 成交量
createTime: 创建时间

```
