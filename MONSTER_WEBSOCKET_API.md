# WEBSOCKET API


## WEBSOCKET服务地址:

	WEBSOCKET服务连接地址: wss://www.monster.one/websocket


## WEBSOCKET SUBSCRIBE说明：
	
	客户端通过STOMP订阅服务器的TOPIC消息，目前开发接口是公共开放接口，无需任何请求参数


## WEBSOCKET JAVA EXAMPLE:
	
	//WEBSOCKET连接和订阅地址
	static final WEBSOCKET_CONNECT = "wss://www.monster.one/websocket"
	static final WEBSOCKET_TOPIC_PRICE= "/topic／all/price"

	//WEBSOCKET STOMP CLIENT问题
	WebSocketStompClient webSocketStompClient 
				= new WebSocketStompClient(new SockJsClient(
					Arrays.asList(new WebSocketTransport(new StandardWebSocketClient())));
	
	webSocketStompClient.setTaskScheduler(new DefaultManagedTaskScheduler());

	//WEBSOCKET连接和订阅
    ListenableFuture<StompSession> stompSessionFuture =
            webSocketStompClient.connect(WEBSOCKET_CONNECT, new StompSessionHandlerAdapter(){});

    stompSessionFuture.addCallback(new SimpleListenableFutureCallback());

    StompSession stompSession = stompSessionFuture.get(3, TimeUnit.SECONDS);


    说明：
    (1) WEBSOCKET会话和消息处理，由用户根据自身的业务需求进行编写。
    (2) MONSTER WEBSOCKET服务基于STOMP协议实现。
    (3) 以上为JAVA样例，用户需根据使用编程语言的不同，来编写具体的调用代码。



## WEBSOCKET API参考 

### 币币行情 API  

1.Subscribe /topic/all/price   所有币币行情

示例	

```
# Request

Subscribe /topic/all/price

```

请求值说明	

```
该接口为公共接口，无需请求参数，只需通过WEBSOCKET订阅即可，具体可参考WEBSOCKET JAVA EXAMPLE。
```

```
# Response
{
	"resultList": [
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
	}],
}

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
