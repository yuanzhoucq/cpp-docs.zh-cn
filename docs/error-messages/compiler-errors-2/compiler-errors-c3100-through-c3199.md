---
title: 编译器错误 C3100 - C3199
ms.date: 04/21/2019
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
ms.assetid: 7bc40c2f-6a8d-488a-b665-f39375afee77
ms.openlocfilehash: efa3207a9fdfb81a52bf319a1cbc2da84084b6cd
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64856814"
---
# <a name="compiler-errors-c3100-through-c3199"></a>编译器错误 C3100 - C3199

在本部分文档中的文章说明了由编译器生成的错误消息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>错误消息

|Error|消息|
|-----------|-------------|
|[编译器错误 C3100](compiler-error-c3100.md)|'*标识符*： 未知的特性限定符|
|[编译器错误 C3101](compiler-error-c3101.md)|命名的特性参数非法表达式*标识符*|
|编译器错误 C3102|已过时。|
|[编译器错误 C3103](compiler-error-c3103.md)|'*标识符*： 重复的命名的参数|
|[编译器错误 C3104](compiler-error-c3104.md)|特性参数非法|
|编译器错误 C3105|'*符号*： 不能用作特性|
|[编译器错误 C3106](compiler-error-c3106.md)|'*特性*： 未命名的参数必须位于命名的参数之前|
|编译器错误 C3107|'*特性*： 不能定义本机特性的成员函数|
|编译器错误 C3108|无法推导出类型，因为初始值设定项列表不是表达式|
|编译器错误 C3109|'*标识符*： 接口方法必须使用 __stdcall 或 __cdecl 调用约定|
|[编译器错误 C3110](compiler-error-c3110.md)|'*函数*： 不能重载 COM 接口方法|
|编译器错误 C3111|初始值设定项列表不能用作模板参数的默认参数|
|编译器错误 C3112|'*接口*： 接口只能声明在全局或命名空间范围|
|[编译器错误 C3113](compiler-error-c3113.md)|接口/枚举不能为模板/泛型|
|[编译器错误 C3114](compiler-error-c3114.md)|'*标识符*： 不是有效的命名特性参数|
|[编译器错误 C3115](compiler-error-c3115.md)|'*特性*： 此属性不允许在'*构造*|
|[编译器错误 C3116](compiler-error-c3116.md)|'*说明符*： 接口方法的存储类无效|
|[编译器错误 C3117](compiler-error-c3117.md)|'*接口*： 接口只能有一个基类|
|[编译器错误 C3118](compiler-error-c3118.md)|'*接口*： 接口不支持虚拟继承|
|编译器错误 C3119|不允许 alignas （void）|
|[编译器错误 C3120](compiler-error-c3120.md)|'*标识符*： 接口方法不能接受变量参数列表|
|[编译器错误 C3121](compiler-error-c3121.md)|无法更改的类的 GUID*类*|
|编译器错误 C3122|'*接口*: WinRT 泛型接口不能有 GUID|
|编译器错误 C3123|WinRT 泛型接口不能有约束|
|编译器错误 C3124|有符号字符不是有效的 WinRT 数据类型。 改为使用无符号的 char、 wchar_t 或有符号短整数。|
|编译器错误 C3125|'*类型*： 类型不能直接或间接派生自 platform:: exception|
|[编译器错误 C3126](compiler-error-c3126.md)|不能定义联合*union*内托管/WinRT 类型*类型*|
|编译器错误 C3127|'*类型*':'*特征*特征只能在 WinRT ref 类上|
|编译器错误 C3128|'*类型*不具有已引入的 vtable*类型*|
|编译器错误 C3129|'*类型*: __default_vptr_for_base 只能在本地定义的多态类型和基类|
|[编译器错误 C3130](compiler-error-c3130.md)|内部编译器错误： 未能插入的代码块写入 PDB|
|[编译器错误 C3131](compiler-error-c3131.md)|项目必须有一个具有 name 属性 module 特性|
|[编译器错误 C3132](compiler-error-c3132.md)|'*参数*： 参数数组只能应用到一维托管/WinRT 数组类型的形式自变量|
|[编译器错误 C3133](compiler-error-c3133.md)|属性不能应用于C++varargs|
|[编译器错误 C3134](compiler-error-c3134.md)|'*值*： 特性参数的值*自变量*不具有有效的类型*类型*|
|[编译器错误 C3135](compiler-error-c3135.md)|'*标识符*: 属性不能具有 const 或 volatile 类型|
|[编译器错误 C3136](compiler-error-c3136.md)|'*接口*: COM 接口只能从另一个 COM 接口，继承'*接口*不是 COM 接口|
|[编译器错误 C3137](compiler-error-c3137.md)|'*标识符*： 无法初始化属性|
|[编译器错误 C3138](compiler-error-c3138.md)|'*标识符*':'*属性*接口必须从 IDispatch，或继承自 IDispatch 的接口继承|
|[编译器错误 C3139](compiler-error-c3139.md)|'*类型*： 不能导出没有成员的 UDT|
|[编译器错误 C3140](compiler-error-c3140.md)|不能在同一编译单元中具有多个 module 特性|
|[编译器错误 C3141](compiler-error-c3141.md)|'*接口*： 接口只支持公共继承|
|[编译器错误 C3142](compiler-error-c3142.md)|'*属性*： 无法获取属性的地址|
|编译器错误 C3143|'*自变量*： 特性参数不能有多个值|
|编译器错误 C3144|'*特性*： 特性需要显式参数，'*自变量*未命名|
|[编译器错误 C3145](compiler-error-c3145.md)|'*标识符*： 全局或静态变量可能没有托管/WinRT 类型*类型*|
|编译器错误 C3146|已过时。|
|编译器错误 C3147|已过时。|
|编译器错误 C3148|已过时。|
|[编译器错误 C3149](compiler-error-c3149.md)|'*类型*： 不能使用没有顶级此类型*令牌*|
|[编译器错误 C3150](compiler-error-c3150.md)|'*构造*':'*属性*仅应用于类、 结构、 接口、 数组或指针|
|编译器错误 C3151|已过时。|
|[编译器错误 C3152](compiler-error-c3152.md)|'*函数*':'*关键字*仅应用于类、 结构或虚拟成员函数|
|[编译器错误 C3153](compiler-error-c3153.md)|'*接口*： 无法创建接口的实例|
|[编译器错误 C3154](compiler-error-c3154.md)|应、 前省略号。 非逗号分隔的省略号参数数组函数上不受支持。|
|[编译器错误 C3155](compiler-error-c3155.md)|属性索引器中不允许使用属性|
|[编译器错误 C3156](compiler-error-c3156.md)|'*类*： 不能局部定义托管/WinRT 类型|
|[编译器错误 C3157](compiler-error-c3157.md)|ParamArray 特性只能应用到的最后一个参数|
|编译器错误 C3158|'*函数*':'*关键字*只能应用到的虚拟成员函数|
|[编译器错误 C3159](compiler-error-c3159.md)|'*标识符*： 不能声明为指向值类型的指针的数组|
|[编译器错误 C3160](compiler-error-c3160.md)|'*类型*： 托管/WinRT 类的数据成员不能具有此类型|
|[编译器错误 C3161](compiler-error-c3161.md)|'*接口*： 嵌套类、 结构或接口中的接口是非法的; 类或结构中的嵌套接口是非法的|
|[编译器错误 C3162](compiler-error-c3162.md)|'*类型*： 具有析构函数的引用类型不能用作静态数据成员的类型*成员*|
|[编译器错误 C3163](compiler-error-c3163.md)|'*类*： 属性与前面的声明不一致|
|编译器错误 C3164|已过时。|
|编译器错误 C3165|'*值*： 不能转换为整型或浮点型值|
|[编译器错误 C3166](compiler-error-c3166.md)|已过时。 '*类型*： 托管/WinRT 类的数据成员不能具有类型*pointer_type*个内部*managed_pointer_type*|
|[编译器错误 C3167](compiler-error-c3167.md)|无法初始化.NET Framework： 确保已安装|
|[编译器错误 C3168](compiler-error-c3168.md)|'*类型*： 枚举的基础类型非法|
|编译器错误 C3169|'*类型*： 不能从推导类型为 'auto''*类型*|
|[编译器错误 C3170](compiler-error-c3170.md)|不能在项目中具有不同的模块标识符|
|[编译器错误 C3171](compiler-error-c3171.md)|'*模块*： 不能在项目中指定不同的模块属性|
|[编译器错误 C3172](compiler-error-c3172.md)|'*标识符*： 不能在项目中指定不同的 idl_module 特性|
|[编译器错误 C3173](compiler-error-c3173.md)|idl 合并中的版本不匹配|
|[编译器错误 C3174](compiler-error-c3174.md)|未指定模块特性|
|[编译器错误 C3175](compiler-error-c3175.md)|'*函数*： 不能从非托管函数中调用托管类型的方法'*函数*|
|[编译器错误 C3176](compiler-error-c3176.md)|'*类型*： 不能声明局部值类型|
|编译器错误 C3177|不能有包含的类型的转换函数*类型*|
|编译器错误 C3178|'*类型*： 不能具有默认自变量的函数中使用参数数组|
|[编译器错误 C3179](compiler-error-c3179.md)|不允许使用未命名的托管 WinRT 类型|
|[编译器错误 C3180](compiler-error-c3180.md)|'*类型*： 名称超出了元数据限制'*数*字符|
|[编译器错误 C3181](compiler-error-c3181.md)|'*类型*： 的操作数无效*运算符*|
|[编译器错误 C3182](compiler-error-c3182.md)|'*类型*： 成员 using 声明或访问声明是非法的托管 WinRT 类型中|
|[编译器错误 C3183](compiler-error-c3183.md)|不能定义未命名的类、 结构或联合内托管/WinRT 类型*类*|
|编译器错误 C3184|已过时。|
|[编译器错误 C3185](compiler-error-c3185.md)|typeid： 托管/WinRT 类型上使用 '*类型*，使用'*运算符*改为|
|编译器错误 C3186|已过时。|
|[编译器错误 C3187](compiler-error-c3187.md)|'*标识符*： 只是一个函数体内可用|
|编译器错误 C3188|已过时。|
|[编译器错误 C3189](compiler-error-c3189.md)|typeid <*声明符*>： 此语法已不再受支持，use::typeid 改为|
|[编译器错误 C3190](compiler-error-c3190.md)|'*声明符*使用提供的模板参数不是任何成员函数的显式实例化*类型*|
|编译器错误 C3191|已过时。|
|[编译器错误 C3192](compiler-error-c3192.md)|语法错误: ^ 不是前缀运算符 (您是否希望使用 *？)|
|编译器错误 C3193|'*构造*： 需要 / clr 或 / ZW 命令行选项|
|[编译器错误 C3194](compiler-error-c3194.md)|'*类型*： 值类型不能具有赋值运算符|
|[编译器错误 C3195](compiler-error-c3195.md)|'*关键字*： 被保留，不能用作 ref 类或值类型的成员。 必须使用 operator 关键字定义 CLR/WinRT 运算符|
|[编译器错误 C3196](compiler-error-c3196.md)|'*标识符*： 使用了多次|
|[编译器错误 C3197](compiler-error-c3197.md)|'*关键字*： 只能在定义中|
|[编译器错误 C3198](compiler-error-c3198.md)|使用浮点 pragma 无效： fenv_access 杂注仅在精确模式下运行|
|[编译器错误 C3199](compiler-error-c3199.md)|使用浮点 pragma 无效： 在非精确模式下不支持异常|

## <a name="see-also"></a>请参阅

[C /C++编译器和生成工具错误和警告](../compiler-errors-1/c-cpp-build-errors.md) \
[编译器错误 C2000-C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
