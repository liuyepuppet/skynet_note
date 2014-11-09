#Skynet_server实现解析之skynet_command
##命令简介
1. TimeOut
2. Reg
3. Query
4. Name
5. Now
6. Exit
7. Kill
8. [Lanuch](#Lanuch)
9. SetEnv
10. GetEnv
11. StartTime
12. Endless
13. Abort
14. Monitor
15. MqLen
16. LogOn
17. LogOff

## <span id="Lanuch">Lanuch命令</span>
### 函数原型

	const char* cmd_lanuch(struct skynet_context* context, const char* param)
	
参数说明:  
1. context调用命令的service的上下文环境  
2. param 包含了加载模块和加载的参数具体格式如下:  
　　