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
ms.openlocfilehash: 7dd09e6f31592f6d4b62b94d8d3256fe1a432010
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280304"
---
# <a name="compiler-warnings-c4400-through-c4599"></a>编译器警告 C4400 - C4599

在本部分文档中的文章说明了由编译器生成警告消息的一个子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>警告消息

|警告|消息|
|-------------|-------------|
|[编译器警告 （等级 1） C4600](compiler-warning-level-1-c4600.md)|#pragma '*宏名称*： 应为有效的非空字符串|
|[编译器警告 （等级 C4400](../../error-messages/compiler-warnings/compiler-warning-level-4-c4400.md)|'*类型*： 不支持此类型上的 const/volatile 限定符|
|[编译器警告 （等级 1） C4401](../../error-messages/compiler-warnings/compiler-warning-level-1-c4401.md)|'*位域*： 成员是位域|
|[编译器警告 （等级 1） C4402](../../error-messages/compiler-warnings/compiler-warning-level-1-c4402.md)|必须使用 PTR 运算符|
|[编译器警告 （等级 1） C4403](../../error-messages/compiler-warnings/compiler-warning-level-1-c4403.md)|非法 PTR 运算符|
|[编译器警告 （等级 3） C4404](../../error-messages/compiler-warnings/compiler-warning-level-3-c4404.md)|忽略指令上的段|
|[编译器警告 （等级 1） C4405](../../error-messages/compiler-warnings/compiler-warning-level-1-c4405.md)|'*标识符*： 标识符是保留的字|
|[编译器警告 （等级 1） C4406](../../error-messages/compiler-warnings/compiler-warning-level-1-c4406.md)|忽略指令上的操作数|
|[编译器警告 （等级 1） C4407](../../error-messages/compiler-warnings/compiler-warning-level-1-c4407.md)|指向成员表示形式的不同指针之间强制转换，编译器可能生成不正确的代码|
|[编译器警告 （等级 C4408](../../error-messages/compiler-warnings/compiler-warning-level-4-c4408.md)|匿名结构&#124;联合未声明任何数据成员|
|[编译器警告 （等级 1） C4409](../../error-messages/compiler-warnings/compiler-warning-level-1-c4409.md)|非法指令大小|
|[编译器警告 （等级 1） C4410](../../error-messages/compiler-warnings/compiler-warning-level-1-c4410.md)|非法的操作数大小|
|[编译器警告 （等级 1） C4411](../../error-messages/compiler-warnings/compiler-warning-level-1-c4411.md)|'*标识符*： 符号解析为置换寄存器|
|[编译器警告 （等级 2） C4412](../../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)|'*函数*： 函数签名包含类型*类型*';C++对象是不安全纯代码之间传递与混合或本机。|
|编译器警告 C4413|classname::member： 引用成员被初始化为构造函数退出后不会持久保存临时|
|[编译器警告 （等级 3） C4414](../../error-messages/compiler-warnings/compiler-warning-level-3-c4414.md)|'*函数*： 短跳转到函数转换为附近|
|编译器警告 （等级 1） C4415|duplicate __declspec(code_seg('*name*'))|
|编译器警告 （等级 1） C4416|__declspec(code_seg(...)) 包含空字符串： 忽略|
|编译器警告 （等级 1） C4417|显式模板实例化不能具有 __declspec(code_seg(...))： 忽略|
|编译器警告 （等级 1） C4418|在枚举上忽略 __declspec(code_seg(...))|
|编译器警告 （等级 3） C4419|'*符号*不起作用时应用于私有 ref 类*类*。|
|[编译器警告 （等级 1） C4420](../../error-messages/compiler-warnings/compiler-warning-level-1-c4420.md)|'*checked_operator*： 操作员不可用，请使用'*运算符*改为; 运行时检查可能会危及|
|编译器警告 （等级 3） C4421|'*参数*： 可恢复函数的引用参数是潜在的不安全|
|编译器警告 （等级 3） C4423|std:: bad_alloc： 类将捕获 ('*类型*) 行上*数*|
|编译器警告 （等级 3） C4424|捕获为*type1*前面有*type2*行上*数*; 不可预测如果引发 std:: bad_alloc，可能会导致行为|
|编译器警告 （等级 1） C4425|SAL 批注不能应用于...|
|编译器警告 （等级 1） C4426|优化标志发生更改后包括标头，可能是由于 #pragma optimize （） 超出|
|编译器警告 （等级 1） C4427|'*运算符*： 除数，未定义的行为发生溢出|
|[编译器警告 （等级 C4429](../../error-messages/compiler-warnings/compiler-warning-level-4-c4429.md)|可能不完整或格式不正确通用字符名称|
|[编译器警告 C4430 （错误）](../../error-messages/compiler-warnings/compiler-warning-c4430.md)|缺少类型说明符 - 假定为 int。 注意:C++不支持默认 int|
|[编译器警告 （等级 C4431](../../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)|缺少类型说明符 - 假定为 int。 注意:C 不再支持默认 int|
|[编译器警告 （等级 C4434](../../error-messages/compiler-warnings/compiler-warning-level-4-c4434.md)|静态构造函数必须具有私有可访问性;更改为专用访问|
|[编译器警告 （等级 C4435](../../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)|'*derived_class*:/ Vd2 下的对象布局将因虚拟基而更改*base_class*|
|[编译器警告 （等级 1） C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)|动态\_从虚拟基的强制转换*base_class*到*derived_class*构造函数或析构函数可能会失败的部分构造的对象|
|[编译器警告 （等级 C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)|动态\_从虚拟基的强制转换*base_class*到*derived_class*在某些上下文中可能会失败|
|编译器警告 C4438|'*函数*： 不能安全地调用 /await: clrcompat 模式。 如果 '*函数*调入 CLR 则可能会导致 CLR 头损坏|
|[编译器警告 C4439 （错误）](../../error-messages/compiler-warnings/compiler-warning-c4439.md)|'*函数*： 函数签名中的托管类型的定义必须具有 __clrcall 调用约定|
|[编译器警告 （等级 1） C4440](../../error-messages/compiler-warnings/compiler-warning-level-1-c4440.md)|调用约定重定义从*calling_convention1*到*calling_convenction2*被忽略|
|[编译器警告 （等级 1） C4441](../../error-messages/compiler-warnings/compiler-warning-level-1-c4441.md)|调用约定的 '*calling_convention1*被忽略;'*calling_convention2*改为使用|
|编译器警告 （等级 1） C4442|__annotation 参数中嵌入了 null 结束符。  该值将被截断。|
|编译器警告 （等级 1） C4443|杂的注参数应为"0"、"1"或"2"|
|编译器警告 （等级 3） C4444|'*标识符*： 顶层 __unaligned 未在此上下文中实现|
|[编译器警告 （等级 1） C4445](../../error-messages/compiler-warnings/compiler-warning-level-1-c4445.md)|'*函数*： 在 WinRT&#124;托管类型的虚方法不能为私有|
|编译器警告 （等级 1） C4446|'*类型*： 不能将映射成员*name1*到这种类型，由于与类型名称冲突。 该方法已重命名为*name2*|
|编译器警告 （等级 1） C4447|main 签名找到不带线程模型。 请考虑使用 int main (platform:: array\<platform:: string ^ > ^ args)。|
|编译器警告 C4448|'*类型*1 不具有元数据中指定的默认接口。 选择:*type2*，这可能会在运行时失败。|
|编译器警告 C4449|'*类型*非密封的类型应标记为 [WebHostHidden]|
|编译器警告 C4450|'*type1*应将标记为 [WebHostHidden] 因为它派生'*type2*|
|编译器警告 （等级 C4451|classname1::member:使用 ref 类 classname2::member 在此上下文可能会导致无效的封送处理对象跨上下文|
|编译器警告 （等级 1） C4452|'*标识符*： 公共类型不能在全局范围内。 它必须是输出.winmd 文件的名称的子级的命名空间中。|
|编译器警告 （等级 1） C4453|'*类型*:不应使用不是公共类型的发布接口上的 [WebHostHidden] 类型 [WebHostHidden]|
|编译器警告 （等级 1） C4454|'*函数*[defaultoverload] 指定重载的多个输入参数的数目。 选取*声明*为默认重载|
|编译器警告 （等级 1） C4455|运算符*运算符*： 保留不以下划线开头的文本后缀标识符|
|[编译器警告（等级 4）C4456](compiler-warning-level-4-c4456.md)|声明*标识符*隐藏上一个本地声明|
|[编译器警告（等级 4）C4457](compiler-warning-level-4-c4457.md)|声明*标识符*隐藏了函数参数|
|[编译器警告（等级 4）C4458](compiler-warning-level-4-c4458.md)|声明*标识符*隐藏了类成员|
|[编译器警告 （等级 C4459](compiler-warning-level-4-c4459.md)|声明*标识符*隐藏了全局声明|
|[编译器警告 （等级 C4460](../../error-messages/compiler-warnings/compiler-warning-level-4-c4460.md)|WinRT&#124;管理运算符*运算符*，通过引用传递参数。 WinRT&#124;管理运算符*运算符*具有不同的语义从C++运算符*cpp_operator*，是否原本希望通过值传递？|
|[编译器警告 （等级 1） C4461](../../error-messages/compiler-warnings/compiler-warning-level-1-c4461.md)|'*classname*： 此类有一个终结器 ！*终结器*，但没有析构函数 ~*dtor*|
|[编译器警告 （等级 1，错误） C4462](../../error-messages/compiler-warnings/compiler-warning-level-1-c4462.md)|'*类型*： 无法确定的类型的 GUID。 程序可能在运行时失败。|
|[编译器警告 （等级 C4463](compiler-warning-level-4-c4463.md)|地址信息溢出;分配*值*到位域的只包含中的值*min_value*to*max_value*|
|[编译器警告（等级 4）C4464](../../error-messages/compiler-warnings/c4464.md)|相对包含路径包含..|
|[编译器警告 （等级 1） C4470](../../error-messages/compiler-warnings/compiler-warning-level-1-c4470.md)|在 /clr 下忽略了浮点控制 pragma|
|[编译器警告 （等级 C4471](compiler-warning-level-4-c4471.md)|'*枚举*： 无范围枚举的前向声明必须有基础类型 (假定为 int)|
|编译器警告 （等级 1） C4472|'*标识符*是本机枚举： 添加访问说明符 (private/public) 以声明 WinRT&#124;托管枚举|
|[编译器警告 （等级 1） C4473](c4473.md)|'*函数*： 没有足够自变量传递为格式字符串|
|编译器警告 （等级 3） C4474|'*函数*： 格式字符串中传递的参数太多|
|编译器警告 （等级 3） C4475|'*函数*： 长度修饰符*修饰符*不能与类型字段字符一起使用'*字符*格式说明符中|
|编译器警告 （等级 3） C4476|'*函数*： 未知的类型字段字符*字符*格式说明符中|
|[编译器警告 （等级 1） C4477](c4477.md)|'*函数*： 格式字符串*字符串*要求类型的自变量*类型*，但可变参数参数*数*具有类型*类型*|
|编译器警告 （等级 1） C4478|'*函数*： 不能在相同的格式字符串中混合位置和非位置占位符|
|编译器警告 （错误） C4480|使用了非标准扩展： 指定枚举的基础类型*枚举*|
|[编译器警告 （等级 C4481](../../error-messages/compiler-warnings/compiler-warning-level-4-c4481.md)|使用了非标准扩展： 重写说明符*关键字*|
|编译器警告 C4482|使用了非标准扩展： 枚举 '*枚举*限定名称中使用|
|编译器警告 （等级 1，错误） C4483|语法错误： 预期C++关键字|
|[编译器警告 C4484 （错误）](../../error-messages/compiler-warnings/compiler-warning-c4484.md)|'*override_function*： 匹配 ref 基类方法*base_class_function*，但未标记为 virtual 一步、 上一 new 或 override;假定 new （而不是 virtual）|
|[编译器警告 C4485 （错误）](../../error-messages/compiler-warnings/compiler-warning-c4485.md)|'*override_function*： 匹配 ref 基类方法*base_class_function*，但未标记为 new 或 override;假定 new （和 virtual）|
|[编译器警告 （等级 1） C4486](../../error-messages/compiler-warnings/compiler-warning-level-1-c4486.md)|'*函数*: ref 类或值类的私有虚方法应标记为 sealed|
|[编译器警告 （等级 C4487](../../error-messages/compiler-warnings/compiler-warning-level-4-c4487.md)|'*derived_class_function*： 匹配继承非虚方法*base_class_function*，但不是显式标记为 new|
|[编译器警告 （等级 1） C4488](../../error-messages/compiler-warnings/compiler-warning-level-1-c4488.md)|'*函数*： 需要*关键字*关键字才能实现的接口方法*interface_method*|
|[编译器警告 （等级 1） C4489](../../error-messages/compiler-warnings/compiler-warning-level-1-c4489.md)|'*说明符*： 接口方法上不允许'*方法*; 重写说明符只允许在 ref 类和值类方法|
|[编译器警告 （等级 1） C4490](../../error-messages/compiler-warnings/compiler-warning-level-1-c4490.md)|override： 重写说明符; 的使用不正确'*函数*不匹配 ref 基类方法|
|编译器警告 （等级 1） C4491|'*名称*： 具有非法的 IDL 版本格式|
|编译器警告 （等级 1，错误） C4492|'*function1*： 匹配 ref 基类方法*function2*，但未标记为 override|
|编译器警告 （等级 3，错误） C4493|删除表达式不起作用的析构函数作为 '*类型*没有 'public' 可访问性|
|编译器警告 （等级 1） C4494|'*函数*:忽略 __declspec （allocator），因为该函数返回类型不是指针或引用|
|编译器警告 C4495|使用了非标准扩展 __super： 替换为显示基类名|
|编译器警告 C4496|使用非标准扩展 for each： 替换为 ranged-for 语句|
|编译器警告 C4497|sealed 使用了非标准扩展： 替换为最终|
|编译器警告 C4498|使用了非标准扩展:*扩展*|
|编译器警告 （等级 C4499|"*函数*： 显式专用化不能具有存储类 （忽略）"|
|[编译器警告 （等级 1） C4502](../../error-messages/compiler-warnings/compiler-warning-level-1-c4502.md)|'*链接规范*需要使用关键字 extern，并且必须位于所有其他说明符之前|
|[编译器警告 （等级 1） C4503](../../error-messages/compiler-warnings/compiler-warning-level-1-c4503.md)|'*标识符*： 修饰名的长度超过，名称已被截断|
|[编译器警告 （等级 C4505](../../error-messages/compiler-warnings/compiler-warning-level-4-c4505.md)|'*函数*： 未引用本地函数已移除|
|[编译器警告 （等级 1） C4506](../../error-messages/compiler-warnings/compiler-warning-level-1-c4506.md)|内联函数没有定义*函数*|
|[编译器警告 （等级 1） C4508](../../error-messages/compiler-warnings/compiler-warning-level-1-c4508.md)|'*函数*： 函数应返回一个值;void 返回类型假定|
|编译器警告 C4509|使用了非标准扩展:*函数*使用 SEH 和 '*对象*具有析构函数|
|[编译器警告 （等级 C4510](../../error-messages/compiler-warnings/compiler-warning-level-4-c4510.md)|'*类*： 默认构造函数隐式定义为已删除|
|[编译器警告 （等级 3） C4511](../../error-messages/compiler-warnings/compiler-warning-level-3-c4511.md)|'*类*： 复制构造函数隐式定义为已删除|
|[编译器警告 （等级 C4512](../../error-messages/compiler-warnings/compiler-warning-level-4-c4512.md)|'*类*： 赋值运算符已隐式定义为已删除|
|[编译器警告 （等级 C4513](../../error-messages/compiler-warnings/compiler-warning-level-4-c4513.md)|'*类*： 析构函数隐式定义为已删除|
|[编译器警告 （等级 C4514](../../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)|'*函数*： 未引用的内联函数已移除|
|[编译器警告 （等级 C4515](../../error-messages/compiler-warnings/compiler-warning-level-4-c4515.md)|'*命名空间*： 命名空间使用本身|
|[编译器警告 （等级 C4516](../../error-messages/compiler-warnings/compiler-warning-level-4-c4516.md)|class::symbol： 否决访问声明;成员 using 声明提供更好的选择|
|[编译器警告 （等级 C4517](../../error-messages/compiler-warnings/compiler-warning-level-4-c4517.md)|否决访问声明;成员 using 声明提供更好的选择|
|[编译器警告 （等级 1） C4518](../../error-messages/compiler-warnings/compiler-warning-level-1-c4518.md)|'*说明符*： 意外的存储类或类型说明符; 被忽略|
|编译器警告 （错误） C4519|默认模板自变量只能在类模板|
|[编译器警告 （等级 3） C4521](../../error-messages/compiler-warnings/compiler-warning-level-3-c4521.md)|'*类*： 指定了多个复制构造函数|
|[编译器警告 （等级 3） C4522](../../error-messages/compiler-warnings/compiler-warning-level-3-c4522.md)|'*类*： 指定的多个赋值运算符|
|[编译器警告 （等级 3） C4523](../../error-messages/compiler-warnings/compiler-warning-level-3-c4523.md)|'*类*： 指定的多个析构函数|
|[编译器警告 （等级 1） C4526](../../error-messages/compiler-warnings/compiler-warning-level-1-c4526.md)|'*函数*： 静态成员函数不能重写虚函数*虚函数*重写将被忽略，将隐藏虚函数|
|[编译器警告 （等级 1） C4530](../../error-messages/compiler-warnings/compiler-warning-level-1-c4530.md)|C++异常处理程序使用，但展开语义未启用。 指定 /EHsc|
|编译器警告 （等级 1） C4531|C++异常处理在 Windows CE 上不可用。 使用结构化的异常处理|
|[编译器警告 （等级 1） C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|continue: __finally/finally 块中的跳转具有未定义的行为在终止处理期间|
|[编译器警告 （等级 1） C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|初始化*变量*跳过了'*goto 标签*|
|[编译器警告 （等级 3） C4534](../../error-messages/compiler-warnings/compiler-warning-level-3-c4534.md)|'*构造函数*'将不能类/结构的默认构造函数'*标识符*由于默认自变量|
|[编译器警告 （等级 3） C4535](../../error-messages/compiler-warnings/compiler-warning-level-3-c4535.md)|调用 _set_se_translator （） 需要 /EHa|
|[编译器警告 （等级 C4536](../../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)|'*typename*： 类型名超出了元数据限制，'*character_limit*字符|
|[编译器警告 （等级 1） C4537](../../error-messages/compiler-warnings/compiler-warning-level-1-c4537.md)|'*对象*': '。 应用于非 UDT 类型|
|[编译器警告 （等级 3） C4538](../../error-messages/compiler-warnings/compiler-warning-level-3-c4538.md)|'*类型*： 不支持此类型上的 const/volatile 限定符|
|[编译器警告 （等级 1） C4540](../../error-messages/compiler-warnings/compiler-warning-level-1-c4540.md)|dynamic_cast 用于转换为不可访问或不明确的基;运行时测试将失败 ('*type1*到*type2*)|
|[编译器警告 （等级 1） C4541](../../error-messages/compiler-warnings/compiler-warning-level-1-c4541.md)|'*标识符*多态类型上使用'*类型*与 /GR-; 可能会导致不可预知的行为|
|编译器警告 （等级 1） C4542|跳过生成合并的注入的文本文件，无法写入*filetype*文件: '*问题*:*消息*|
|[编译器警告 （等级 3） C4543](../../error-messages/compiler-warnings/compiler-warning-level-3-c4543.md)|插入文本特性禁止显示没有\_injected_text|
|[编译器警告 （等级 1） C4544](../../error-messages/compiler-warnings/compiler-warning-level-1-c4544.md)|'*声明*： 默认模板自变量将忽略此模板声明|
|[编译器警告 （等级 1） C4545](../../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)|逗号前的表达式计算为缺少自变量列表的函数|
|[编译器警告 （等级 1） C4546](../../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)|逗号前的函数调用缺少自变量列表|
|[编译器警告 （等级 1） C4547](../../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)|'*运算符*： 运算符之前逗号不起任何作用; 应输入带副作用的运算符|
|[编译器警告 （等级 1） C4548](../../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)|逗号前的表达式不起任何作用；应输入带副作用的表达式|
|[编译器警告 （等级 1） C4549](../../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)|'*运算符*： 逗号前的运算符不起作用; 是否打算'*运算符*？|
|[编译器警告 （等级 1） C4550](../../error-messages/compiler-warnings/compiler-warning-level-1-c4550.md)|表达式计算为缺少参数列表的函数|
|[编译器警告 （等级 1） C4551](../../error-messages/compiler-warnings/compiler-warning-level-1-c4551.md)|函数调用缺少参数列表|
|[编译器警告 （等级 1） C4552](../../error-messages/compiler-warnings/compiler-warning-level-1-c4552.md)|'*运算符*： 运算符不起任何作用; 应输入带副作用的运算符|
|[编译器警告 （等级 1） C4553](../../error-messages/compiler-warnings/compiler-warning-level-1-c4553.md)|'*运算符*： 运算符不起作用; 是否打算运算符？|
|[编译器警告 （等级 3） C4554](../../error-messages/compiler-warnings/compiler-warning-level-3-c4554.md) C4554|'*运算符*： 检查运算符优先级可能存在的错误; 使用括号阐明优先级|
|[编译器警告 （等级 1） C4555](../../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)|表达式无效；应输入带副作用的表达式|
|[编译器警告 （等级 1） C4556](../../error-messages/compiler-warnings/compiler-warning-level-1-c4556.md)|内部即时参数的值*值*不在范围内'*lower_bound* - *upper_bound*|
|[编译器警告 （等级 3） C4557](../../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)|__assume 包含效果*效果*|
|[编译器警告 （等级 1） C4558](../../error-messages/compiler-warnings/compiler-warning-level-1-c4558.md)|操作数的值*值*不在范围内'*lower_bound* - *upper_bound*|
|[编译器警告 （等级 C4559](../../error-messages/compiler-warnings/compiler-warning-level-4-c4559.md)|'*函数*： 重定义; 函数提升 __declspec(modifier)|
|[编译器警告 （等级 1） C4561](../../error-messages/compiler-warnings/compiler-warning-level-1-c4561.md)|__fastcall 与不兼容 / clr 选项： 将转换为 __stdcall|
|编译器警告 （等级 C4562|完全保持原型的函数所需使用 / clr 选项： 将转换为 (void)|
|[编译器警告 （等级 C4564](../../error-messages/compiler-warnings/compiler-warning-level-4-c4564.md)|方法*方法*的 class '*classname*定义了不受支持的默认参数'*参数*|
|[编译器警告 （等级 C4565](../../error-messages/compiler-warnings/compiler-warning-level-4-c4565.md)|'*函数*： 重定义; 与 __declspec(modifier) 以前声明符号|
|[编译器警告 （等级 1） C4566](../../error-messages/compiler-warnings/compiler-warning-level-1-c4566.md)|通用字符名称表示字符*char*不能出现在当前代码页 (*数*)|
|编译器警告 （等级 1） C4568|'*函数*： 没有成员的显式重写签名匹配|
|编译器警告 （等级 3） C4569|'*函数*： 没有成员的显式重写签名匹配|
|[编译器警告 （等级 3） C4570](../../error-messages/compiler-warnings/compiler-warning-level-3-c4570.md)|'*类型*： 没有显式声明为抽象的但具有抽象函数|
|[编译器警告 （等级 C4571](../../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)|信息性： 自 Visual 更改自语义C++7.1;不再捕获结构化的异常 (SEH)|
|[编译器警告 （等级 1） C4572](../../error-messages/compiler-warnings/compiler-warning-level-1-c4572.md)|[ParamArray] 特性已弃用，使用在 /clr 下...改为|
|编译器警告 （等级 1） C4573|使用情况*lambda 函数*要求编译器捕获 this，但当前默认捕获模式不允许|
|编译器警告 （等级 C4574|'*标识符*被定义为"0： 您是否希望使用 #if identifier？|
|编译器警告 （等级 1） C4575|__vectorcall 与不兼容 / clr 选项： 将转换为 __stdcall|
|编译器警告 （等级 1，错误） C4576|后跟初始值设定项列表的带圆括号类型是一种非标准的显式类型转换语法|
|编译器警告 （级别 1，Off） C4577|noexcept 与任何异常处理模式，以指定; 一起使用不能保证在异常终止。 指定 /EHsc|
|编译器警告 （等级 1，错误） C4578|abs： 从转换*type1*到*type2*，可能丢失数据 (您是否希望调用*函数*或 #include \<cmath >？)|
|[编译器警告 （等级 3） C4580](../../error-messages/compiler-warnings/compiler-warning-level-3-c4580.md)|[attribute] 已弃用；改为指定 System::Attribute 或 Platform::Metadata 作为基类|
|[编译器警告 （等级 1） C4581](../../error-messages/compiler-warnings/compiler-warning-level-1-c4581.md)|已否决的行为:"*字符串*"替换*字符串*进程属性|
|编译器警告 （等级 C4582|'*类型*： 构造函数未隐式调用|
|编译器警告 （等级 C4583|'*类型*： 析构函数未隐式调用|
|[编译器警告 （等级 1） C4584](../../error-messages/compiler-warnings/compiler-warning-level-1-c4584.md)|'*class1*： 基类'*class2*'已是基类的*class3 移*|
|编译器警告 （等级 1，错误） C4585|'*类*:WinRT public ref class 必须密封的或从现有未密封类派生|
|编译器警告 （等级 1，错误） C4586|'*类型*:在名为 Windows 的顶级命名空间中不能声明为公共类型|
|编译器警告 （等级 1） C4587|'*anonymous_structure*： 行为更改： 不再隐式调用构造函数|
|编译器警告 （等级 1） C4588|'*anonymous_structure*： 行为更改： 不再隐式调用析构函数|
|编译器警告 （等级 1） C4591|constexpr 调用深度限制*数量*超出 (/ constexpr:depth\<数 >)|
|编译器警告 （等级 3） C4592|'*函数*: constexpr 调用评估失败; 将在运行时调用的函数|
|编译器警告 （等级 1） C4593|'*函数*: constexpr 调用评估步骤限制的*限制*超过了; 请使用 /constexpr:\<数 > 以提高限制|
|编译器警告 （等级 3） C4594|'*类型*： 析构函数不会隐式调用如果引发异常|
|编译器警告 （等级 1） C4595|'*类型*： 行为更改： 析构函数将不再隐式调用如果引发异常|
|编译器警告 （等级 C4596|'*标识符*： 成员声明中的非法限定的名|
|编译器警告 （错误） C4597|未定义的行为： offsetof 应用于虚拟基的成员|
|编译器警告 （等级 1 和 3） C4598|#include"*标头*"： 标头数*数*预编译标头中不匹配当前编译中的该位置|
|编译器警告 （等级 3） C4599|'*标志**路径*： 命令行参数号*数*与预编译标头不匹配|

## <a name="see-also"></a>请参阅

[C /C++编译器和生成工具错误和警告](../compiler-errors-1/c-cpp-build-errors.md) \
[编译器警告 C4000-C5999](compiler-warnings-c4000-c5999.md)
