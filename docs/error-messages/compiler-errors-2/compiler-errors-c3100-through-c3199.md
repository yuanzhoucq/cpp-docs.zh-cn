---
title: "编译器错误 C3100 通过 C3199 |Microsoft 文档"
ms.custom: 
ms.date: 04/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
helpviewer_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
dev_langs:
- C++
ms.assetid: 7bc40c2f-6a8d-488a-b665-f39375afee77
caps.latest.revision: 1
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 7060d03845cf81aeaedc5eff48db3aec59716112
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-errors-c3100-through-c3199"></a>编译器错误 C3100 通过 C3199
文档的此部分中的文章包含有关 Visual C++ 编译器错误的子部分的信息。 可在此处访问信息，或者在 Visual Studio 中的“输出”  窗口中选择错误号，然后选择 F1 键。  
  
> [!NOTE]
>  不是每个[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]错误记录在 MSDN 中。 在许多情况下，诊断消息将提供的所有可用信息。 如果你认为某个错误消息需要更多说明，请通知我们。 你可以在此页上，使用反馈表单或转到 Visual Studio 中的菜单栏，然后选择**帮助**，**报告 Bug**，或可以在提交建议或 bug 报表[Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 错误和警告的 MSDN 公共论坛，可能会发现更多帮助。 [Visual c + + 语言](http://go.microsoft.com/fwlink/?LinkId=158195)论坛是有关问题和讨论有关[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]语言语法和编译器。 [Visual c + + 常规](http://go.microsoft.com/fwlink/?LinkId=158194)论坛的问题是有关[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]其他论坛中未涉及。 你还可能上查找有关错误和警告的帮助[堆栈溢出](http://stackoverflow.com/)。  
  
|错误|消息|  
|-----------|-------------|  
|[编译器错误 C3100](compiler-error-c3100.md)|*标识符*': 未知的属性限定符|  
|[编译器错误 C3101](compiler-error-c3101.md)|非法表达式命名的特性自变量*标识符*|  
|编译器错误 C3102|已过时。|  
|[编译器错误 C3103](compiler-error-c3103.md)|*标识符*： 重复的命名的参数|  
|[编译器错误 C3104](compiler-error-c3104.md)|非法特性自变量|  
|编译器错误 C3105|*符号*： 不能用作特性|  
|[编译器错误 C3106](compiler-error-c3106.md)|*属性*： 未命名自变量必须位于命名的参数之前|  
|编译器错误 C3107|*属性*： 不能定义的本机属性成员函数|  
|编译器错误 C3108|无法推导作为一种类型，因为初始值设定项列表不是表达式|  
|编译器错误 C3109|*标识符*： 接口方法必须使用 __stdcall 或 __cdecl 调用约定|  
|[编译器错误 C3110](compiler-error-c3110.md)|*函数*： 不能重载 COM 接口方法|  
|编译器错误 C3111|初始值设定项列表不能用作模板参数的默认自变量|  
|编译器错误 C3112|*接口*： 接口可以仅声明在全局或命名空间范围|  
|[编译器错误 C3113](compiler-error-c3113.md)|'接口/enum' 不能为模板/泛型|  
|[编译器错误 C3114](compiler-error-c3114.md)|*标识符*： 不是有效的命名特性自变量|  
|[编译器错误 C3115](compiler-error-c3115.md)|*属性*： 此属性不允许对*构造*|  
|[编译器错误 C3116](compiler-error-c3116.md)|*说明符*： 接口方法的无效的存储类|  
|[编译器错误 C3117](compiler-error-c3117.md)|*接口*： 接口可只具有一个基类|  
|[编译器错误 C3118](compiler-error-c3118.md)|*接口*： 接口不支持虚拟继承|  
|编译器错误 C3119|不允许 alignas(void)|  
|[编译器错误 C3120](compiler-error-c3120.md)|*标识符*： 接口方法不能接受变量自变量列表|  
|[编译器错误 C3121](compiler-error-c3121.md)|无法更改类的 GUID*类*|  
|编译器错误 C3122|*接口*: WinRT 泛型接口不能具有 GUID|  
|编译器错误 C3123|WinRT 泛型接口不能具有约束|  
|编译器错误 C3124|符号 char 不是有效的 WinRT 数据类型。 改为使用无符号的 char、 wchar_t 或签名的短。|  
|编译器错误 C3125|*类型*： 类型不能直接或间接派生自 platform:: exception|  
|[编译器错误 C3126](compiler-error-c3126.md)|不能定义联合*联合*内托管/WinRT 类型*类型*|  
|编译器错误 C3127|*类型*:*特征*WinRT ref 类可以只能用于特征|  
|编译器错误 C3128|*类型*不具有已引入的 vtable*类型*|  
|编译器错误 C3129|*类型*: __default_vptr_for_base 只能使用本地定义的多态类型和基|  
|[编译器错误 C3130](compiler-error-c3130.md)|内部编译器错误： 无法写入 PDB 插入的代码块|  
|[编译器错误 C3131](compiler-error-c3131.md)|项目必须具有 name 属性模块属性|  
|[编译器错误 C3132](compiler-error-c3132.md)|*参数*： 参数数组可以仅应用到类型一维托管/WinRT 数组的形参|  
|[编译器错误 C3133](compiler-error-c3133.md)|无法将属性应用到 c + + varargs|  
|[编译器错误 C3134](compiler-error-c3134.md)|*值*： 特性自变量的值*参数*不具有有效的类型*类型*|  
|[编译器错误 C3135](compiler-error-c3135.md)|*标识符*: 属性不能具有 const 或易失性键入|  
|[编译器错误 C3136](compiler-error-c3136.md)|*接口*： 只能继承自另一个 COM 接口，COM 接口*接口*不是一个 COM 接口|  
|[编译器错误 C3137](compiler-error-c3137.md)|*标识符*： 无法初始化属性|  
|[编译器错误 C3138](compiler-error-c3138.md)|*标识符*:*属性*接口必须继承从 IDispatch，或从 IDispatch 继承的接口|  
|[编译器错误 C3139](compiler-error-c3139.md)|*类型*： 无法导出无成员 UDT|  
|[编译器错误 C3140](compiler-error-c3140.md)|不能在同一编译单元中有多个模块属性|  
|[编译器错误 C3141](compiler-error-c3141.md)|*接口*： 接口只支持公共继承|  
|[编译器错误 C3142](compiler-error-c3142.md)|*属性*： 无法获取属性的地址|  
|编译器错误 C3143|*参数*： 特性自变量不能有多个值|  
|编译器错误 C3144|*属性*： 属性需要显式参数*参数*是未命名|  
|[编译器错误 C3145](compiler-error-c3145.md)|*标识符*： 全局或静态变量可能没有托管/WinRT 类型*类型*|  
|编译器错误 C3146|已过时。|  
|编译器错误 C3147|已过时。|  
|编译器错误 C3148|已过时。|  
|[编译器错误 C3149](compiler-error-c3149.md)|*类型*： 不能使用没有顶级此类型*令牌*|  
|[编译器错误 C3150](compiler-error-c3150.md)|*构造*:*属性*可以仅应用于类、 结构、 接口、 数组或指针|  
|编译器错误 C3151|已过时。|  
|[编译器错误 C3152](compiler-error-c3152.md)|*函数*:*关键字*可以仅应用于类、 结构或虚拟成员函数|  
|[编译器错误 C3153](compiler-error-c3153.md)|*接口*： 无法创建接口的实例|  
|[编译器错误 C3154](compiler-error-c3154.md)|预期 '，' 之前省略号。 非逗号分隔的参数数组函数上不支持的省略号。|  
|[编译器错误 C3155](compiler-error-c3155.md)|属性索引器中不允许属性|  
|[编译器错误 C3156](compiler-error-c3156.md)|*类*： 不能具有本地管理/WinRT 类型的定义|  
|[编译器错误 C3157](compiler-error-c3157.md)|ParamArray 属性只能应用到的最后一个参数|  
|编译器错误 C3158|*函数*:*关键字*只能应用到的虚拟成员函数|  
|[编译器错误 C3159](compiler-error-c3159.md)|*标识符*： 不能声明为指向值类型的指针的数组|  
|[编译器错误 C3160](compiler-error-c3160.md)|*类型*： 托管/WinRT 类的数据成员不能具有此类型|  
|[编译器错误 C3161](compiler-error-c3161.md)|*接口*： 嵌套类、 结构或接口中的接口是非法; 嵌套接口的类或结构中是非法|  
|[编译器错误 C3162](compiler-error-c3162.md)|*类型*： 具有析构函数的引用类型不能用作静态数据成员的类型*成员*|  
|[编译器错误 C3163](compiler-error-c3163.md)|*类*： 属性与以前的声明不一致|  
|编译器错误 C3164|已过时。|  
|编译器错误 C3165|*值*： 无法将转换为整型或浮点型值|  
|[编译器错误 C3166](compiler-error-c3166.md)|已过时。 *类型*： 托管/WinRT 类的数据成员不能有类型*pointer_type*到内部*managed_pointer_type*|  
|[编译器错误 C3167](compiler-error-c3167.md)|无法初始化.NET Framework： 请确保已安装|  
|[编译器错误 C3168](compiler-error-c3168.md)|*类型*： 非法枚举的基础类型|  
|编译器错误 C3169|*类型*： 无法从推导为 auto 的类型*类型*|  
|[编译器错误 C3170](compiler-error-c3170.md)|不能在项目中具有不同的模块标识符|  
|[编译器错误 C3171](compiler-error-c3171.md)|*模块*： 无法在项目中指定不同的模块属性|  
|[编译器错误 C3172](compiler-error-c3172.md)|*标识符*： 不能在项目中指定不同 idl_module 特性|  
|[编译器错误 C3173](compiler-error-c3173.md)|在 idl 合并的版本不匹配|  
|[编译器错误 C3174](compiler-error-c3174.md)|未指定模块特性|  
|[编译器错误 C3175](compiler-error-c3175.md)|*函数*： 无法从非托管函数调用的托管类型的一个方法*函数*|  
|[编译器错误 C3176](compiler-error-c3176.md)|*类型*： 不能声明本地值类型|  
|编译器错误 C3177|不能有到包含的类型的转换函数*类型*|  
|编译器错误 C3178|*类型*： 不能使用 ParamArray 带默认自变量的函数|  
|[编译器错误 C3179](compiler-error-c3179.md)|不允许未命名的托管/WinRT 类型|  
|[编译器错误 C3180](compiler-error-c3180.md)|*类型*： 名称超出的元数据限制*数*' 字符|  
|[编译器错误 C3181](compiler-error-c3181.md)|*类型*': 无效的操作数的*运算符*|  
|[编译器错误 C3182](compiler-error-c3182.md)|*类型*： 成员 using 声明或访问声明是在托管/WinRT 类型非法|  
|[编译器错误 C3183](compiler-error-c3183.md)|不能定义未命名的类、 结构或联合管理/WinRT 类型*类*|  
|编译器错误 C3184|已过时。|  
|[编译器错误 C3185](compiler-error-c3185.md)|typeid： 在托管/WinRT 类型上使用*类型*，使用*运算符*改为|  
|编译器错误 C3186|已过时。|  
|[编译器错误 C3187](compiler-error-c3187.md)|*标识符*： 才函数体内可用|  
|编译器错误 C3188|已过时。|  
|[编译器错误 C3189](compiler-error-c3189.md)|typeid <*声明符*>： 此语法不再支持，use::typeid 改为|  
|[编译器错误 C3190](compiler-error-c3190.md)|*声明符*与提供的模板自变量不是任何成员函数的显式实例化*类型*|  
|编译器错误 C3191|已过时。|  
|[编译器错误 C3192](compiler-error-c3192.md)|语法错误: ^ 不是一个前缀运算符 (您的意思 ' *'？)|  
|编译器错误 C3193|*构造*： 需要 / clr 或 / ZW 命令行选项|  
|[编译器错误 C3194](compiler-error-c3194.md)|*类型*： 值类型不能具有赋值运算符|  
|[编译器错误 C3195](compiler-error-c3195.md)|*关键字*： 已保留，不能用作 ref 类或值类型的成员。 必须使用 operator 关键字定义 CLR/WinRT 运算符|  
|[编译器错误 C3196](compiler-error-c3196.md)|*标识符*： 使用多个一次|  
|[编译器错误 C3197](compiler-error-c3197.md)|*关键字*： 仅可用于定义|  
|[编译器错误 C3198](compiler-error-c3198.md)|使用无效的浮点杂注： fenv_access 杂注仅在精确的模式下运行|  
|[编译器错误 C3199](compiler-error-c3199.md)|使用无效的浮点杂注： 非精确模式中不支持异常|  

