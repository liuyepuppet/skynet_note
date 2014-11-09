#Skynet Module

## Abstract
skynet的module是一个用c语言写的so库，其中必须提供xxx_create, xxx_init, xxx_release函数。每个模块加载到skynet中以后将会是唯一的，当创建新的service ctx的时候，会先查找Module存在与否，只有当不存在时才会在指定路径下进行查找加载。

## 与context的关系
ctx->mod变量指向了module，我们可以将一个module看做是一个service的工厂函数，用来生产service，并转换成ctx的。
