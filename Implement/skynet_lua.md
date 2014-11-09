#Skynet.lua

#Abstract
每个启动的lua服务(Service)中都会加载一份skynet的库，并且相互独立并不会出现冲突的情况。

## register_protocol
在skynet启动时，会加载skynet.lua作为lua的库，其中skynet.lua在被加载时会注册几个protocol  

1. "lua"
2. "response"
3. "error"

## skynet.start
调用skynet.start时，会做以下几件事

skynet每个service或者说是context的回调函数的格式如下:  
	
	int (*skynet_cb)(struct skynet_context* context, void* ud, int type, int session, uint32_t source, void* msg, size_t sz)
	
	

1. bind一个c.callback(dispatch_message)，为服务绑定一个回调函数
2. 将启动函数放入到timeout 0的事件中