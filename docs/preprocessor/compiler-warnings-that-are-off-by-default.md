---
title: "默认情况下处于关闭状态的编译器警告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 编译器, 设置选项"
  - "警告, 编译器"
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
caps.latest.revision: 39
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 37
---
# 默认情况下处于关闭状态的编译器警告
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

编译器包含默认关闭的警告，因为大多数用户不想看到它们。  但是，你可使用下列选项之一启用此类警告。  
  
 `#pragma warning(default :`  `warning_number` `)`  
 指定的警告 \(`warning_number`\) 在其默认级别启用。  该警告的文档包含该警告的默认级别。  
  
 `#pragma warning(` `warning_level`  `:`  `warning_number` `)`  
 指定的警告 \(`warning_number`\) 在其指定级别 \(`warning_level`\) 启用。  
  
 [\/Wall](../build/reference/compiler-option-warning-level.md)  
 **\/Wall** 将启用默认情况下禁用的所有警告。  
  
 默认情况下，下列警告是禁用的。  
  
|||  
|-|-|  
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md)（级别 4）|枚举器“identifier”在枚举“enumeration”的 switch 中没有被 case 标签显式处理|  
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md)（级别 3）|枚举器“identifier”在枚举“enumeration”的 switch 中没有被处理|  
|C4191（级别 3）|“operator\/operation”: 从“type of expression”到“type of expression”的不安全转换|  
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md)（级别 4）|“identifier”: 从“type1”转换到“type2”，可能丢失数据|  
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md)（级别 4）|“operator”: 从“type1”转换到“type2”，可能丢失数据|  
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md)（级别 4）|“function”: 未给出函数原型: 将“\(\)”转换为“\(void\)”|  
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md)（级别 4）|“function”: 成员函数不重写任何基类虚拟成员函数|  
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md)（级别 1）|“virtual\_function”: 不重写基“class”中的虚拟成员函数；函数被隐藏|  
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md)（级别 3）|“class”: 类具有虚函数，但析构函数不是虚拟的|  
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md)（级别 4）|“function”: 不重写基“type”中的虚拟成员函数；函数被隐藏|  
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md)（级别 3）|“operator”: 无符号\/负常量不匹配|  
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md)（级别 4）|使用了非标准扩展 :“var”: 在 for 循环中声明的循环控制变量用在了 for 循环范围外|  
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md)（级别 4）|“operator”: 表达式始终为 false|  
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md)（级别 2）|“conversion”: 从“type1”到“type2”截断|  
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md)（级别 1）|“variable”: 从“type”到“type”的指针截断|  
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md)（级别 1）|“operation”: 从“type1”转换到更大的“type2”|  
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md)（级别 4）|“type”: 在 CLR 元数据中检测到使用了未定义的类型 \- 使用此类型可能导致运行时异常|  
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md)（级别 1）|行为更改: 调用了“function”，但在以前版本中调用的是成员运算符|  
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md)（级别 1）|行为更改：调用“member1”而不是“member2”|  
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|“this”: 用于基成员初始值设定项列表|  
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md)（级别 4）|“action”: 从“type\_1”转换到“type\_2”，有符号\/无符号不匹配|  
|C4370（级别 3）|为了更好地封装，类的布局与早期版本的编译器已有所不同|  
|C4371（级别 3）|为了更好地封装成员“member”，类的布局可能与早期版本的编译器已有所不同|  
|C4388（级别 4）|有符号\/无符号不匹配|  
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)（级别 2）|“function”: 函数签名包含类型“type”；在纯代码与混合代码或本机代码之间传递 C\+\+ 对象是不安全的|  
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)（级别 4）|缺少类型说明符 \- 假定为 int。  注意: C 不再支持默认的 int|  
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)（级别 4）|“class1”: \/vd2 下的对象布局将因虚拟基“class2”而更改|  
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)（级别 4）|从虚拟基“class1”到“class2'”的 dynamic\_cast 在某些上下文中可能会失败|  
|C4444（级别 3）|顶级“\_\_unaligned”没有在该上下文中实现|  
|C4471（级别 4）|无范围枚举的前向声明必须有基础类型（假定为 int）|  
|C4472（级别 1）|“identifier”是本机枚举：添加访问说明符 \(private\/public\) 以声明托管枚举|  
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)（级别 4）|“function”: 未引用的内联函数已移除|  
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)（级别 4）|“type name”: 类型名超出了“limit”个字符的元数据限制|  
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)（级别 1）|逗号前的表达式计算为缺少参数列表的函数|  
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)（级别 1）|逗号前的函数调用缺少参数列表|  
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)（级别 1）|“operator”: 逗号前的运算符不起任何作用；应输入带副作用的运算符|  
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)（级别 1）|逗号前的表达式不起任何作用；应输入带副作用的表达式|  
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)（级别 1）|“operator”: 逗号前的运算符不起任何作用；是否是有意使用“operator”的？|  
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)（级别 1）|表达式无效；应输入带副作用的表达式|  
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)（级别 3）|“\_\_assume”包含效果“effect”|  
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)（级别 4）|信息: 自 Visual C\+\+ 7.1 之后，catch\(...\) 语义发生了变化；不再捕获结构化的异常\(SEH\)|  
|C4574（级别 4）|“identifier”被定义为“0”：你是否希望使用“\#if identifier”？|  
|C4608（级别 3）|“symbol1”已被初始值设定项列表中的另一个联合成员“symbol2”初始化|  
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)（级别 3）|\#pragma warning: 无警告编号“number”|  
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)（级别 4）|“derived class”: 未能生成默认构造函数，因为基类默认构造函数不可访问|  
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)（级别 4）|“derived class”: 未能生成复制构造函数，因为基类复制构造函数不可访问|  
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)（级别 4）|“derived class”: 未能生成赋值运算符，因为基类赋值运算符不可访问|  
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)（级别 1）|\-Ze 不支持二合字母。  字符序列“digraph”未解释为“char”的替换标记|  
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)（级别 3）|“instance”: 本地静态对象的结构是非线程安全的|  
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)（级别 4）|没有将“symbol”定义为预处理器宏，用“0”替换“directives”|  
|C4682（级别 4）|“symbol”：未指定方向参数特性，默认为 \[in\]|  
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)（级别 3）|“user\-defined type”: 行为可能有更改，UDT 中的更改返回调用约定|  
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)（级别 1）|“function”：非私有成员的签名包含程序集私有本机类型“native\_type”|  
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)（级别 4）|“function”: 函数未内联|  
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)（级别 3）|将 32 位浮点型结果存储在内存中，可能会降低性能|  
|C4767（级别 4）|节名称“symbol”的长度超过 8 个字符，并将由链接器截断|  
|C4786（级别 3）|“symbol”：对象名称在调试信息中被截断为“number”个字符|  
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md)（级别 4）|“bytes”字节填充添加在构造“member\_name”之后|  
|[C4826](../error-messages/compiler-warnings/compiler-warning-level-2-c4826.md)（级别 2）|从“type1”到“type2”的转换是带符号的扩展转换。  这可能导致意外的运行时行为|  
|[C4837](../error-messages/compiler-warnings/compiler-warning-level-4-c4837.md)（级别 4）|检测到三元祖:“??%c”已替换为“%c”|  
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md)（级别 1）|宽字符串强制转换为“LPSTR”|  
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md)（级别 1）|字符串强制转换为“LPWSTR”|  
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md)（级别 1）|“declarator”: GUID 只能与类、接口或命名空间关联|  
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md)（级别 1）|副本初始化非法；隐式应用了多个用户定义的转换|  
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md)（级别 4）|我们假定类型库是为 number 位指针生成的|  
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md)（级别 1）|reinterpret\_cast 在相关类之间使用:“class1”和“class2”|  
|C4962|“function”: 已禁用按配置文件优化，原因在于优化导致了配置数据文件不一致|  
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md)（级别 4）|“symbol”：异常规范与前面的声明不匹配|  
|C4987（级别 4）|使用了非标准扩展：“throw \(...\)”|  
|C4988（级别 4）|“symbol”：在类\/函数范围外声明了变量|  
  
## 请参阅  
 [警告](../preprocessor/warning.md)