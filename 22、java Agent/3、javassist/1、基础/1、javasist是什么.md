 ## 什么是javassist



javassist是一个开源的分析、编辑和创建java字节码的类库。其主要的优点在于简单，而且快速，直接使用java编码的形式，而不需要了解虚拟机指令，就能动态改变类的结构或者动态生成类。



主要用途：

1. 运行时监控插装埋点
2. AOP动态代理实现（比cgib的动态代理要慢）
3. 获取访问类结构信息：如获取参数名称等等