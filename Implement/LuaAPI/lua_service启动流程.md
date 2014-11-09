#Lua Service的启动流程

本文从skynet示例的main.lua启动simpledb服务进行解释skynet的lua service是如何启动起来的。

	skynet.newservice("simpledb")

	function skynet.newservice(name, ...)
		skynet.call(".launcher", "lua", "LAUNCH", "snlua", name, ...)
	end
	
	function skynet.call(addr, typename, ...)
		local p = proto[typename]
		local session = c.send(addr, p.id, nil, p.pack(...))
		if session == nil then
			error("call to invalid address" .. skynet.address(addr))
		end
		return p.unpack(yield_call(addr, session))
	end
	
以上代码是向.launcher服务发送了一个msg任务，msg的内容为使用c.pack打包后的msg信息，简单起见我们可以任务其内容为："LAUNCH snlua simpledb ..."