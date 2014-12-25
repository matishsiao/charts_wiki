**The Charting Library does NOT include market data.** You must provide your own data in the required format. A sample data engine integrates Yahoo Finance API historical data. The charts can receive data in two ways:

1. Update in real-time with a PUSH type connection, for example through WebSocket. This way your charts will autoupdate with new prices when they arrive. To achieve this, you have to use the [[JavaScript API|JS-Api]] and have your own transport method ready.

2. Update on a PULL/pulse/refresh basis (like most web-based charts today), where the chart data is updating every X number of seconds (the chart client will ask the server emulating PUSH updates), or only get reloaded manually by the user. For this, use the [[UDF protocol|UDF]] and write your own datafeed wrapper. 

###JavaScript API or UDF?

![](https://www.dropbox.com/s/dedg3tzlp7jj0v6/api_structure.png?dl=1)
The picture above illustrates the relationships between the [[default package|Package-Content]] components. Mandatory Charting Library parts are colored red. Green parts (default data transport) are included in default package (having non-minimized source code) and may be replaced. You may see the default data transport implements JS API. Also, default transport implements UDF protocol.

![](https://www.dropbox.com/s/nwzexm0k10541th/api_usage.png?dl=1)

1. **If you already have a data transport ready** (websocket streaming, polling, or any other transport), or if you don’t but need streaming data - use our [[JavaScript API|JS-Api]], which is extremely compact and simple to implement. You will have to create a small **client-side data adapter** between your data transport and our charts using JavaScript.

2. **If you don’t have any transports** and do not need streaming data (e.g., data pulsing is all you need), then you will have to create (or use) at least a thin server-side datafeed wrapper. You may use any language and technology for this purpose: it’s just necessary for your wrapper to support our data exchange protocol (we call it [[UDF|UDF]]) to be able to feed your Charting Library with data. You will have to create a small **server-side data adapter** between your back-end and our charts using you favorite language.

###Want Examples ?

A sample implementation of **UDF-compatible** (case #2 described below) server-side wrapper is available [on github](https://github.com/drbeep/yahoo_datafeed). It uses Yahoo! data.

A sample of **JS API** implementation (and UDF client-side at the same time) is a part of Charting Library package (see *datafeed.js* file).