---
title: 编译器警告 C4400 - C4599
ms.date: 04/21/2019
f1_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4452
- C4453
- C4454
- C4455
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
helpviewer_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4451
- C4452
- C4453
- C4454
- C4455
- C4456
- C4457
- C4459
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
ms.assetid: b07850a5-ae89-48ea-bf9a-f0e30939f9b9
ms.openlocfilehash: 9f7886a88ebd98d5d7ab1848ea7a788967362ad7
ms.sourcegitcommit: d3829ae0c3db909f96057755a80665f5ea4896ea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550442"
---
# <a name="compiler-warnings-c4400-through-c4599"></a>编译器警告 C4400 - C4599

文档的本节中的文章介绍了编译器生成的一小部分警告消息。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>警告消息

|警告|消息|
|-------------|-------------|
|[编译器警告 (等级 1) C4600](compiler-warning-level-1-c4600.md)|#pragma "*macro name*": 应输入有效的非空字符串|
|[编译器警告 (等级 4) C4400](../../error-messages/compiler-warnings/compiler-warning-level-4-c4400.md)|"*type*": 不支持此类型上的 const/volatile 限定符|
|[编译器警告 (等级 1) C4401](../../error-messages/compiler-warnings/compiler-warning-level-1-c4401.md)|"位域": 成员是位域|
|[编译器警告 (等级 1) C4402](../../error-messages/compiler-warnings/compiler-warning-level-1-c4402.md)|必须使用 PTR 运算符|
|[编译器警告 (等级 1) C4403](../../error-messages/compiler-warnings/compiler-warning-level-1-c4403.md)|非法 PTR 运算符|
|[编译器警告 (等级 3) C4404](../../error-messages/compiler-warnings/compiler-warning-level-3-c4404.md)|忽略指令上的时间段|
|[编译器警告 (等级 1) C4405](../../error-messages/compiler-warnings/compiler-warning-level-1-c4405.md)|"*identifier*": 标识符是保留字|
|[编译器警告 (等级 1) C4406](../../error-messages/compiler-warnings/compiler-warning-level-1-c4406.md)|已忽略指令上的操作数|
|[编译器警告 (等级 1) C4407](../../error-messages/compiler-warnings/compiler-warning-level-1-c4407.md)|在不同指针到成员表示形式之间强制转换, 编译器可能生成不正确的代码|
|[编译器警告 (等级 4) C4408](../../error-messages/compiler-warnings/compiler-warning-level-4-c4408.md)|匿名 "struct&#124;union" 未声明任何数据成员|
|[编译器警告 (等级 1) C4409](../../error-messages/compiler-warnings/compiler-warning-level-1-c4409.md)|非法的指令大小|
|[编译器警告 (等级 1) C4410](../../error-messages/compiler-warnings/compiler-warning-level-1-c4410.md)|非法的操作数大小|
|[编译器警告 (等级 1) C4411](../../error-messages/compiler-warnings/compiler-warning-level-1-c4411.md)|"*identifier*": 符号解析为置换寄存器|
|[编译器警告 (等级 2) C4412](../../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)|"*function*": 函数签名包含类型 "*type*";C++对象在纯代码与混合或本机之间传递是不安全的。|
|编译器警告 C4413|"classname:: member": 引用成员被初始化为临时, 在构造函数退出后不会持久保存|
|[编译器警告 (等级 3) C4414](../../error-messages/compiler-warnings/compiler-warning-level-3-c4414.md)|"*function*": 短跳转到转换为附近的函数|
|编译器警告 (等级 1) C4415|duplicate __declspec(code_seg('*name*'))|
|编译器警告 (等级 1) C4416|__declspec (code_seg (...)) 包含空字符串: 已忽略|
|编译器警告 (等级 1) C4417|显式模板实例化不能具有 __declspec (code_seg (...)): 已忽略|
|编译器警告 (等级 1) C4418|在枚举上忽略了 __declspec (code_seg (...))|
|编译器警告 (等级 3) C4419|"*symbol*" 在应用于私有 ref 类 "*class*" 时不起作用。|
|[编译器警告 (等级 1) C4420](../../error-messages/compiler-warnings/compiler-warning-level-1-c4420.md)|"*checked_operator*": 运算符不可用, 请改用 "*operator*";可能会危及运行时检查|
|编译器警告 (等级 3) C4421|"*parameter*": 可恢复函数上的引用参数可能不安全|
|编译器警告 (等级 3) C4423|"std:: bad_alloc": 将由类 ("*type*") 在行*号*上捕获|
|编译器警告 (等级 3) C4424|对于行*号*上的 "*type2*" 前面带有 "*type1*" 的 catch;如果引发 "std:: bad_alloc", 则可能会导致不可预知的行为|
|编译器警告 (等级 1) C4425|SAL 批注不能应用于 "..."|
|编译器警告 (等级 1) C4426|包含标头后更改了优化标志, 原因可能是 #pragma optimize ()|
|编译器警告 (等级 1) C4427|"*operator*": 恒定除法溢出, 不确定的行为|
|[编译器警告 (等级 4) C4429](../../error-messages/compiler-warnings/compiler-warning-level-4-c4429.md)|通用字符名称可能不完整或格式不正确|
|[编译器警告 (错误) C4430](../../error-messages/compiler-warnings/compiler-warning-c4430.md)|缺少类型说明符 - 假定为 int。 注意:C++不支持默认值-int|
|[编译器警告 (等级 4) C4431](../../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)|缺少类型说明符 - 假定为 int。 注意:C 不再支持默认值-int|
|[编译器警告 (等级 4) C4434](../../error-messages/compiler-warnings/compiler-warning-level-4-c4434.md)|静态构造函数必须具有专用可访问性;更改为专用访问|
|[编译器警告 (等级 4) C4435](../../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)|"*derived_class*":/Vd2 下的对象布局将因虚拟基 "*base_class*" 而更改|
|[编译器警告 (等级 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)|构造\_函数或析构函数中从虚拟基 "*base_class*" 到 "*derived_class*" 的动态强制转换可能会因部分构造的对象而失败|
|[编译器警告 (等级 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)|在\_某些上下文中, 从虚拟基 "*base_class*" 到 "*derived_class*" 的动态强制转换可能会失败|
|编译器警告 C4438|"*function*": 不能在/await: clrcompat 模式中安全地调用。 如果 "*function*" 调用 clr, 则可能会导致 CLR 头损坏|
|[编译器警告 (错误) C4439](../../error-messages/compiler-warnings/compiler-warning-c4439.md)|"*function*": 签名中具有托管类型的函数定义必须具有 __clrcall 调用约定|
|[编译器警告 (等级 1) C4440](../../error-messages/compiler-warnings/compiler-warning-level-1-c4440.md)|忽略从 "*calling_convention1*" 到 "*calling_convenction2*" 的调用约定重定义|
|[编译器警告 (等级 1) C4441](../../error-messages/compiler-warnings/compiler-warning-level-1-c4441.md)|忽略了 "*calling_convention1*" 的调用约定;改为使用 "*calling_convention2*"|
|编译器警告 (等级 1) C4442|__annotation 参数中嵌入的 null 终止符。  值将被截断。|
|编译器警告 (等级 1) C4443|杂注参数应为 "0"、"1" 或 "2"|
|编译器警告 (等级 3) C4444|"*identifier*": 顶层 "__unaligned" 未在此上下文中实现|
|[编译器警告 (等级 1) C4445](../../error-messages/compiler-warnings/compiler-warning-level-1-c4445.md)|"*function*": 在 "WinRT&#124;托管" 类型中, 虚方法不能是私有的|
|编译器警告 (等级 1) C4446|"*type*": 由于与类型名称冲突, 无法将成员 "*name1*" 映射到此类型。 方法已重命名为 "*name2*"|
|编译器警告 (等级 1) C4447|找到 "main" 签名, 但未找到线程模型。 请考虑使用 "int main (Platform::\<Array platform:: String ^ > ^ args)"。|
|编译器警告 C4448|"*类型*1" 没有在元数据中指定的默认接口。 选取: "*type2*", 这可能会在运行时失败。|
|编译器警告 C4449|"*type*" 不密封的类型应标记为 "[WebHostHidden]"|
|编译器警告 C4450|"*type1*" 应标记为 "[WebHostHidden]", 因为它派生自 "*type2*"|
|编译器警告 (等级 4) C4451|"1:: member":在此上下文中使用 ref 类 "classname2:: member" 可能导致跨上下文的对象封送处理无效|
|编译器警告 (等级 1) C4452|"*identifier*": 公共类型不能在全局范围内。 它必须位于作为输出 winmd 文件名称的子命名空间中。|
|编译器警告 (等级 1) C4453|"*type*":不应在不是 "[WebHostHidden]" 的公共类型的发布接口上使用 "[WebHostHidden]" 类型|
|编译器警告 (等级 1) C4454|在未指定 [DefaultOverload] 的情况下, "*function*" 的重载次数超过了输入参数的数目。 选取 "*声明*" 作为默认重载|
|编译器警告 (等级 1) C4455|"operator *operator*": 保留不以下划线开头的文本后缀标识符|
|[编译器警告（等级 4）C4456](compiler-warning-level-4-c4456.md)|"*identifier*" 的声明隐藏了上一个本地声明|
|[编译器警告（等级 4）C4457](compiler-warning-level-4-c4457.md)|"*identifier*" 的声明隐藏了函数参数|
|[编译器警告（等级 4）C4458](compiler-warning-level-4-c4458.md)|"*identifier*" 的声明隐藏了类成员|
|[编译器警告 (等级 4) C4459](compiler-warning-level-4-c4459.md)|"*identifier*" 的声明隐藏了全局声明|
|[编译器警告 (等级 4) C4460](../../error-messages/compiler-warnings/compiler-warning-level-4-c4460.md)|"WinRT&#124;托管的" 运算符 "*operator*" 具有通过引用传递的参数。 "WinRT&#124;托管" 运算符 "*operator*" 的语义与C++运算符 "*cpp_operator*" 不同, 是否打算通过值传递？|
|[编译器警告 (等级 1) C4461](../../error-messages/compiler-warnings/compiler-warning-level-1-c4461.md)|"*classname*": 此类具有终结器 "!*finalizer*", 但没有析构函数" ~*dtor*"|
|[编译器警告 (等级 1, 错误) C4462](../../error-messages/compiler-warnings/compiler-warning-level-1-c4462.md)|"*type*": 无法确定类型的 GUID。 程序可能在运行时失败。|
|[编译器警告 (等级 4) C4463](compiler-warning-level-4-c4463.md)|超出将 "*value*" 分配给只包含 "*min_value*" 到 "*max_value*" 的值的位字段|
|[编译器警告（等级 4）C4464](../../error-messages/compiler-warnings/c4464.md)|相对包含路径包含 ".."|
|[编译器警告 (等级 1) C4470](../../error-messages/compiler-warnings/compiler-warning-level-1-c4470.md)|在/clr 下忽略了浮点控制杂注|
|[编译器警告 (等级 4) C4471](compiler-warning-level-4-c4471.md)|"*enumeration*": 未区分范围的枚举的前向声明必须有基础类型 (假定为 int)|
|编译器警告 (等级 1) C4472|"*identifier*" 是本机枚举: 添加访问说明符 (private/public) 以声明 "WinRT&#124;托管" 枚举|
|[编译器警告 (等级 1) C4473](c4473.md)|"*function*": 没有为格式字符串传递足够的参数|
|编译器警告 (等级 3) C4474|"*function*": 为格式字符串传递的参数太多|
|编译器警告 (等级 3) C4475|"*function*": 不能在格式说明符中将长度修饰符 "*修饰符*" 与类型字段字符 "*character*" 一起使用|
|编译器警告 (等级 3) C4476|"*function*": 格式说明符中的类型字段字符 "*character*" 未知|
|[编译器警告 (等级 1) C4477](c4477.md)|"*function*": 格式字符串 "*string*" 需要类型为 "*type*" 的参数, 但可变参数参数*号*的类型为 "*type*"|
|编译器警告 (等级 1) C4478|"*function*": 不能在同一格式字符串中混用位置占位符和非位置占位符|
|编译器警告 (错误) C4480|使用了非标准扩展: 请为枚举 "*enumeration*" 指定基础类型|
|[编译器警告 (等级 4) C4481](../../error-messages/compiler-warnings/compiler-warning-level-4-c4481.md)|使用了非标准扩展: 重写说明符 "*关键字*"|
|编译器警告 C4482|使用了非标准扩展: 限定名中使用了枚举 "*enumeration*"|
|编译器警告 (等级 1, 错误) C4483|语法错误: 应C++为关键字|
|[编译器警告 (错误) C4484](../../error-messages/compiler-warnings/compiler-warning-c4484.md)|"*override_function*": 匹配 ref 基类方法 "*base_class_function*", 但未标记为 "virtual"、"new" 或 "override";假定为 "new" (而不是 "virtual")|
|[编译器警告 (错误) C4485](../../error-messages/compiler-warnings/compiler-warning-c4485.md)|"*override_function*": 匹配 ref 基类方法 "*base_class_function*", 但未标记为 "new" 或 "override";假定为 "new" (和 "virtual")|
|[编译器警告 (等级 1) C4486](../../error-messages/compiler-warnings/compiler-warning-level-1-c4486.md)|"*function*": ref 类或值类的私有虚方法应该标记为 "sealed"|
|[编译器警告 (等级 4) C4487](../../error-messages/compiler-warnings/compiler-warning-level-4-c4487.md)|"*derived_class_function*": 匹配继承的非虚方法 "*base_class_function*", 但未显式标记为 "new"|
|[编译器警告 (等级 1) C4488](../../error-messages/compiler-warnings/compiler-warning-level-1-c4488.md)|"*function*": 需要 "*关键字*" 关键字才能实现接口方法 "*interface_method*"|
|[编译器警告 (等级 1) C4489](../../error-messages/compiler-warnings/compiler-warning-level-1-c4489.md)|"*说明符*": 不允许在接口方法 "*method*" 上使用;重写说明符只允许在 ref 类和值类方法上使用|
|[编译器警告 (等级 1) C4490](../../error-messages/compiler-warnings/compiler-warning-level-1-c4490.md)|"override": 重写说明符的用法不正确;"*function*" 与 ref 基类方法不匹配|
|编译器警告 (等级 1) C4491|"*name*": 具有非法的 IDL 版本格式|
|编译器警告 (等级 1, 错误) C4492|"*function1*": 匹配 ref 基类方法 "*function2*", 但未标记为 "override"|
|编译器警告 (等级3、错误) C4493|删除表达式没有影响, 因为 "*type*" 的析构函数没有 "public" 可访问性|
|编译器警告 (等级 1) C4494|"*function*":忽略 __declspec (分配器), 因为函数返回类型不是指针或引用|
|编译器警告 C4495|使用了非标准扩展 "__super": 替换为显式基类名|
|编译器警告 C4496|使用了非标准扩展 "for each": 替换为范围-for 语句|
|编译器警告 C4497|使用了非标准扩展 "sealed": 替换为 "final"|
|编译器警告 C4498|使用了非标准扩展: "*extension*"|
|编译器警告 (等级 4) C4499|"*function*": 显式专用化不能具有存储类 (忽略)|
|[编译器警告 (等级 1) C4502](../../error-messages/compiler-warnings/compiler-warning-level-1-c4502.md)|"*链接规范*" 要求使用关键字 "extern", 并且必须在所有其他说明符之前|
|[编译器警告 (等级 1) C4503](../../error-messages/compiler-warnings/compiler-warning-level-1-c4503.md)|"*identifier*": 超出修饰名的长度, 名称被截断|
|[编译器警告 (等级 4) C4505](../../error-messages/compiler-warnings/compiler-warning-level-4-c4505.md)|"*function*": 未引用的本地函数已移除|
|[编译器警告 (等级 1) C4506](../../error-messages/compiler-warnings/compiler-warning-level-1-c4506.md)|内联函数 "*function*" 没有定义|
|[编译器警告 (等级 1) C4508](../../error-messages/compiler-warnings/compiler-warning-level-1-c4508.md)|"*function*": 函数应返回值;假定为 "void" 返回类型|
|编译器警告 C4509|使用了非标准扩展: "*function*" 使用 SEH, 而 "*object*" 具有析构函数|
|[编译器警告 (等级 4) C4510](../../error-messages/compiler-warnings/compiler-warning-level-4-c4510.md)|"*class*": 默认构造函数隐式定义为已删除|
|[编译器警告 (等级 3) C4511](../../error-messages/compiler-warnings/compiler-warning-level-3-c4511.md)|"*class*": 复制构造函数被隐式定义为已删除|
|[编译器警告 (等级 4) C4512](../../error-messages/compiler-warnings/compiler-warning-level-4-c4512.md)|"*class*": 赋值运算符隐式定义为已删除|
|[编译器警告 (等级 4) C4513](../../error-messages/compiler-warnings/compiler-warning-level-4-c4513.md)|"*class*": 已将析构函数隐式定义为已删除|
|[编译器警告 (等级 4) C4514](../../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)|"*function*": 未引用的内联函数已移除|
|[编译器警告 (等级 4) C4515](../../error-messages/compiler-warnings/compiler-warning-level-4-c4515.md)|"*namespace*": 命名空间使用自身|
|[编译器警告 (等级 4) C4516](../../error-messages/compiler-warnings/compiler-warning-level-4-c4516.md)|"class:: symbol": 已弃用访问声明;成员 using 声明提供更好的替代方法|
|[编译器警告 (等级 4) C4517](../../error-messages/compiler-warnings/compiler-warning-level-4-c4517.md)|不推荐使用访问声明;成员 using 声明提供更好的替代方法|
|[编译器警告 (等级 1) C4518](../../error-messages/compiler-warnings/compiler-warning-level-1-c4518.md)|"*说明符*": 此处意外的存储类或类型说明符;掉|
|编译器警告 (错误) C4519|仅对类模板允许默认模板参数|
|[编译器警告 (等级 3) C4521](../../error-messages/compiler-warnings/compiler-warning-level-3-c4521.md)|"*class*": 指定了多个复制构造函数|
|[编译器警告 (等级 3) C4522](../../error-messages/compiler-warnings/compiler-warning-level-3-c4522.md)|"*class*": 指定了多个赋值运算符|
|[编译器警告 (等级 3) C4523](../../error-messages/compiler-warnings/compiler-warning-level-3-c4523.md)|"*class*": 指定了多个析构函数|
|[编译器警告 (等级 1) C4526](../../error-messages/compiler-warnings/compiler-warning-level-1-c4526.md)|"*function*": 静态成员函数不能重写虚函数 "*虚函数*" override, 将隐藏虚函数|
|[编译器警告 (等级 1) C4530](../../error-messages/compiler-warnings/compiler-warning-level-1-c4530.md)|C++使用了异常处理程序, 但未启用展开语义。 指定/EHsc|
|编译器警告 (等级 1) C4531|C++Windows CE 上的异常处理不可用。 使用结构化异常处理|
|[编译器警告 (等级 1) C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|"continue": 在终止处理期间跳出 "__finally/finally" 块的行为未定义|
|[编译器警告 (等级 1) C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|"*goto label*" 跳过了 "*variable*" 的初始化|
|[编译器警告 (等级 3) C4534](../../error-messages/compiler-warnings/compiler-warning-level-3-c4534.md)|由于默认参数, "*构造函数*" 将不是 "class/struct"*标识符*的默认构造函数|
|[编译器警告 (等级 3) C4535](../../error-messages/compiler-warnings/compiler-warning-level-3-c4535.md)|调用 _set_se_translator () 需要/EHa|
|[编译器警告 (等级 4) C4536](../../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)|"*typename*": 类型名称超出了 "*character_limit*" 字符的元数据限制|
|[编译器警告 (等级 1) C4537](../../error-messages/compiler-warnings/compiler-warning-level-1-c4537.md)|"*object*": "." 应用于非 UDT 类型|
|[编译器警告 (等级 3) C4538](../../error-messages/compiler-warnings/compiler-warning-level-3-c4538.md)|"*type*": 不支持此类型上的 const/volatile 限定符|
|[编译器警告 (等级 1) C4540](../../error-messages/compiler-warnings/compiler-warning-level-1-c4540.md)|dynamic_cast 用于转换为不可访问或不明确的基;运行时测试将失败 ("*type1*" 到 "*type2*")|
|[编译器警告 (等级 1) C4541](../../error-messages/compiler-warnings/compiler-warning-level-1-c4541.md)|使用/GR-的多态类型 "*type*" 中使用的 "*identifier*";可能导致不可预知的行为|
|编译器警告 (等级 1) C4542|跳过生成合并的注入文本文件, 无法写入文件*类型*文件: "*issue*":*消息*|
|[编译器警告 (等级 3) C4543](../../error-messages/compiler-warnings/compiler-warning-level-3-c4543.md)|特性 "no\_injected_text" 抑制的注入文本|
|[编译器警告 (等级 1) C4544](../../error-messages/compiler-warnings/compiler-warning-level-1-c4544.md)|"*声明*": 已忽略此模板声明中的默认模板参数|
|[编译器警告 (等级 1) C4545](../../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)|逗号前的表达式计算为缺少自变量列表的函数|
|[编译器警告 (等级 1) C4546](../../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)|逗号前的函数调用缺少自变量列表|
|[编译器警告 (等级 1) C4547](../../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)|"*operator*": 逗号前的运算符不起任何作用;应有副作用的运算符|
|[编译器警告 (等级 1) C4548](../../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)|逗号前的表达式不起任何作用；应输入带副作用的表达式|
|[编译器警告 (等级 1) C4549](../../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)|"*operator*": 逗号前的运算符不起任何作用;您是否打算 "*operator*"？|
|[编译器警告 (等级 1) C4550](../../error-messages/compiler-warnings/compiler-warning-level-1-c4550.md)|表达式计算结果为缺少参数列表的函数|
|[编译器警告 (等级 1) C4551](../../error-messages/compiler-warnings/compiler-warning-level-1-c4551.md)|缺少参数列表的函数调用|
|[编译器警告 (等级 1) C4552](../../error-messages/compiler-warnings/compiler-warning-level-1-c4552.md)|"*operator*": 运算符不起任何作用;应有副作用的运算符|
|[编译器警告 (等级 1) C4553](../../error-messages/compiler-warnings/compiler-warning-level-1-c4553.md)|"*operator*": 运算符不起任何作用;你是否打算 "运算符？|
|[编译器警告 (等级 3) C4554](../../error-messages/compiler-warnings/compiler-warning-level-3-c4554.md)C4554|"*operator*": 检查运算符优先级是否有可能的错误;使用括号阐明优先级|
|[编译器警告 (等级 1) C4555](../../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)|表达式无效；应输入带副作用的表达式|
|[编译器警告 (等级 1) C4556](../../error-messages/compiler-warnings/compiler-warning-level-1-c4556.md)|内部即时参数 "*value*" 的值超出了范围 "*lower_bound* - *upper_bound*"|
|[编译器警告 (等级 3) C4557](../../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)|"__assume" 包含效果 "*效果*"|
|[编译器警告 (等级 1) C4558](../../error-messages/compiler-warnings/compiler-warning-level-1-c4558.md)|操作数 "*value*" 的值超出了范围 "*lower_bound* - *upper_bound*"|
|[编译器警告 (等级 4) C4559](../../error-messages/compiler-warnings/compiler-warning-level-4-c4559.md)|"*function*": 重定义;函数获取 __declspec (修饰符)|
|[编译器警告 (等级 1) C4561](../../error-messages/compiler-warnings/compiler-warning-level-1-c4561.md)|"__fastcall" 与 "/clr" 选项不兼容: 转换为 "__stdcall"|
|编译器警告 (等级 4) C4562|"/clr" 选项要求完全原型的函数: 将 "()" 转换为 "(void)"|
|[编译器警告 (等级 4) C4564](../../error-messages/compiler-warnings/compiler-warning-level-4-c4564.md)|"class" "*classname*" 的方法 "*method*" 定义了不受支持的默认参数 "*parameter*"|
|[编译器警告 (等级 4) C4565](../../error-messages/compiler-warnings/compiler-warning-level-4-c4565.md)|"*function*": 重定义;符号以前是用 __declspec (修饰符) 声明的|
|[编译器警告 (等级 1) C4566](../../error-messages/compiler-warnings/compiler-warning-level-1-c4566.md)|由通用字符名称 "*char*" 表示的字符不能在当前代码页中表示 (*number*)|
|编译器警告 (等级 1) C4568|"*function*": 没有与显式重写的签名匹配的成员|
|编译器警告 (等级 3) C4569|"*function*": 没有与显式重写的签名匹配的成员|
|[编译器警告 (等级 3) C4570](../../error-messages/compiler-warnings/compiler-warning-level-3-c4570.md)|"*type*": 没有显式声明为抽象的, 但具有抽象函数|
|[编译器警告 (等级 4) C4571](../../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)|信息: 自 Visual C++ 7.1 以来, catch (...) 语义发生了变化;不再捕获结构化的异常 (SEH)|
|[编译器警告 (等级 1) C4572](../../error-messages/compiler-warnings/compiler-warning-level-1-c4572.md)|[ParamArray] 特性已在/clr 下弃用, 请使用 "..."是|
|编译器警告 (等级 1) C4573|"*lambda 函数*" 的用法要求编译器捕获 "this", 但当前默认捕获模式不允许使用|
|编译器警告 (等级 4) C4574|"*Identifier*" 被定义为 "0": 您是否希望使用 "#if 标识符"？|
|编译器警告 (等级 1) C4575|"__vectorcall" 与 "/clr" 选项不兼容: 转换为 "__stdcall"|
|编译器警告 (等级 1, 错误) C4576|后跟初始值设定项列表的带圆括号类型是一个非标准的显式类型转换语法|
|编译器警告 (等级 1, Off) C4577|在未指定异常处理模式的情况下使用 "noexcept";不保证异常终止。 指定/EHsc|
|编译器警告 (等级 1, 错误) C4578|"abs": 从 "*type1*" 转换到 "*type2*", 可能丢失数据 (你是指调用 "*function*" 还是要 #include \<h >？)|
|[编译器警告 (等级 3) C4580](../../error-messages/compiler-warnings/compiler-warning-level-3-c4580.md)|[attribute] 已弃用；改为指定 System::Attribute 或 Platform::Metadata 作为基类|
|[编译器警告 (等级 1) C4581](../../error-messages/compiler-warnings/compiler-warning-level-1-c4581.md)|弃用的行为: ""*字符串*"" 已替换为 "*string*" 以处理特性|
|编译器警告 (等级 4) C4582|"*type*": 构造函数未隐式调用|
|编译器警告 (等级 4) C4583|"*type*": 析构函数未隐式调用|
|[编译器警告 (等级 1) C4584](../../error-messages/compiler-warnings/compiler-warning-level-1-c4584.md)|"*class1*": 基类 "*class2*" 已是 "*a.class3*" 的基类|
|编译器警告 (等级 1, 错误) C4585|"*class*":WinRT "public ref class" 必须是密封的或派生自现有的非密封类|
|编译器警告 (等级 1, 错误) C4586|"*type*":不能在名为 "Windows" 的顶级命名空间中声明公共类型|
|编译器警告 (等级 1) C4587|"*anonymous_structure*": 行为更改: 不再隐式调用构造函数|
|编译器警告 (等级 1) C4588|"*anonymous_structure*": 行为更改: 不再隐式调用析构函数|
|编译器警告 (等级 1) C4591|"constexpr" 调用深度值超出*数量*上限 (/constexpr: 深度\<编号 >)|
|编译器警告 (等级 3) C4592|"*function*": "constexpr" 调用评估失败;函数将在运行时调用|
|编译器警告 (等级 1) C4593|"*function*": 已超过 "constexpr" 调用评估步骤限制;使用/constexpr: 步骤\<号 > 提高限制|
|编译器警告 (等级 3) C4594|"*type*": 如果引发了异常, 则不会隐式调用析构函数|
|编译器警告 (等级 1) C4595|"*type*": 行为更改: 如果引发了异常, 将不再隐式调用析构函数|
|[编译器警告 (等级 4) C4596](../../error-messages/compiler-warnings/c4596.md)|"*identifier*": 成员声明中的非法限定名|
|编译器警告 (错误) C4597|未定义的行为: offsetof 应用于虚拟基的成员|
|编译器警告 (等级1和等级 3) C4598|"#include"*标头*"": 预编译标头中的标头编号*号*与该位置的当前编译不匹配|
|编译器警告 (等级 3) C4599|'*标志* *路径* ： 命令行参数号 *数* 与预编译标头不匹配|

## <a name="see-also"></a>请参阅

[C/C++编译器和生成工具错误和警告](../compiler-errors-1/c-cpp-build-errors.md) \
[编译器警告 C4000-C5999](compiler-warnings-c4000-c5999.md)
