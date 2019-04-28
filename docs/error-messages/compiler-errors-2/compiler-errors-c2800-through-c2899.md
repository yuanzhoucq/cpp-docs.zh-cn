---
title: 编译器错误 C2800 - C2899
ms.date: 04/21/2019
f1_keywords:
- C2816
- C2820
- C2822
- C2826
- C2832
- C2836
- C2837
- C2840
- C2841
- C2848
- C2851
- C2852
- C2853
- C2866
- C2880
- C2887
- C2889
- C2895
- C2899
helpviewer_keywords:
- C2816
- C2820
- C2822
- C2826
- C2832
- C2836
- C2837
- C2840
- C2841
- C2848
- C2851
- C2852
- C2853
- C2866
- C2880
- C2887
- C2889
- C2895
- C2899
ms.assetid: e5de1e92-746a-4315-a331-c5d9efb76dbb
ms.openlocfilehash: a0367d1d465d4460202f4d6d29468e59f6a74657
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62281763"
---
# <a name="compiler-errors-c2800-through-c2899"></a>编译器错误 C2800 - C2899

在本部分文档中的文章说明了由编译器生成的错误消息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>错误消息

|Error|消息|
|-----------|-------------|
|[编译器错误 C2800](compiler-error-c2800.md)|运算符*运算符*不能重载|
|[编译器错误 C2801](compiler-error-c2801.md)|'*成员*必须为非静态成员|
|[编译器错误 C2802](compiler-error-c2802.md)|静态成员运算符*运算符*没有形参|
|[编译器错误 C2803](compiler-error-c2803.md)|运算符*运算符*必须具有至少一个类类型的形参|
|[编译器错误 C2804](compiler-error-c2804.md)|二进制运算符*运算符*参数太多|
|[编译器错误 C2805](compiler-error-c2805.md)|二进制运算符*运算符*参数太少|
|[编译器错误 C2806](compiler-error-c2806.md)|运算符*运算符*形参太多|
|[编译器错误 C2807](compiler-error-c2807.md)|第二个形参以后缀运算符*运算符*必须为 int|
|[编译器错误 C2808](compiler-error-c2808.md)|一元运算符*运算符*形参太多|
|[编译器错误 C2809](compiler-error-c2809.md)|运算符*运算符*没有形参|
|[编译器错误 C2810](compiler-error-c2810.md)|'*接口*： 接口只能从另一个接口继承|
|[编译器错误 C2811](compiler-error-c2811.md)|'*type1*： 不能继承自*type2*，ref 类只能继承从 ref 类或接口类|
|[编译器错误 C2812](compiler-error-c2812.md)|#import 不支持 /clr: pure 和 /clr: safe|
|[编译器错误 C2813](compiler-error-c2813.md)|#import 不支持 /MP|
|[编译器错误 C2814](compiler-error-c2814.md)|'*成员*： 本机类型不能嵌套在托管/WinRT 类型*类*|
|[编译器错误 C2815](compiler-error-c2815.md)|operator delete： 第一个形参必须为 void \*，但*类型*已使用|
|编译器错误 C2816|已过时。|
|[编译器错误 C2817](compiler-error-c2817.md)|operator delete 的返回类型必须为 void|
|[编译器错误 C2818](compiler-error-c2818.md)|应用程序的重载 operator-> 通过类型进行递归 '*类*|
|[编译器错误 C2819](compiler-error-c2819.md)|类型*类*但没有重载的成员 operator->|
|编译器错误 C2820|已过时。|
|[编译器错误 C2821](compiler-error-c2821.md)|operator new 的第一个形参必须为 size_t|
|编译器错误 C2822|此平台上不支持局部回退|
|[编译器错误 C2823](compiler-error-c2823.md)|typedef 模板/泛型是非法的|
|[编译器错误 C2824](compiler-error-c2824.md)|operator new 必须是返回类型 void \*|
|[编译器错误 C2825](compiler-error-c2825.md)|'*标识符*： 必须是类或命名空间时后跟::|
|编译器错误 C2826|已过时。|
|[编译器错误 C2827](compiler-error-c2827.md)|运算符*运算符*不能由全局重写一元窗体|
|[编译器错误 C2828](compiler-error-c2828.md)|运算符*运算符*不能由全局重写二进制格式|
|[编译器错误 C2829](compiler-error-c2829.md)|运算符*运算符*不能包含变量参数列表|
|[编译器错误 C2830](compiler-error-c2830.md)|只有 operator new 的位置参数可以具有默认值|
|[编译器错误 C2831](compiler-error-c2831.md)|运算符*运算符*不能有默认参数|
|编译器错误 C2832|'*标识符*： 引用类型不能进行值初始化|
|[编译器错误 C2833](compiler-error-c2833.md)|运算符*令牌*不是可识别的运算符或类型|
|[编译器错误 C2834](compiler-error-c2834.md)|运算符*运算符*必须是全局限定|
|[编译器错误 C2835](compiler-error-c2835.md)|用户定义的转换*类型*不接受形参|
|编译器错误 C2836|'*标识符*： 一个联合只能有一个非静态数据成员可能会有默认成员初始值设定项|
|编译器错误 C2837|'*函数*： 不能在同一函数中使用 OpenMP 指令和 #pragma 循环 （hint_parallel）|
|[编译器错误 C2838](compiler-error-c2838.md)|'*标识符*： 成员声明中的非法限定的名|
|[编译器错误 C2839](compiler-error-c2839.md)|无效的返回类型*类型*的重载 operator->|
|编译器错误 C2840|指令字参数不是常量|
|编译器错误 C2841|寄存器参数不是常量|
|[编译器错误 C2842](compiler-error-c2842.md)|'*类*： 托管/WinRT 类型不能定义自己的 operator new 或 operator delete|
|[编译器错误 C2843](compiler-error-c2843.md)|'*成员*： 不能接受非静态数据成员的地址或托管/WinRT 类型的方法|
|[编译器错误 C2844](compiler-error-c2844.md)|'*标识符*： 不能为接口成员*接口*|
|[编译器错误 C2845](compiler-error-c2845.md)|'*类型*： 指针算法不允许对此类|
|[编译器错误 C2846](compiler-error-c2846.md)|'*接口*： 接口不能具有构造函数|
|[编译器错误 C2847](compiler-error-c2847.md)|无法将 sizeof 应用于托管/WinRT 类型*类*|
|编译器错误 C2848|'*类*： 托管/WinRT 类型不能是联合的成员|
|[编译器错误 C2849](compiler-error-c2849.md)|'*接口*： 接口不能有析构函数|
|[编译器错误 C2850](compiler-error-c2850.md)|'*构造*： 只允许在文件范围内; 可能不是在嵌套结构|
|编译器错误 C2851|'*枚举*:公共 WinRT 枚举只能使用 int 或 unsigned 的 int 作为基类型|
|编译器错误 C2852|'*标识符*： 只有数据成员可以在类中初始化|
|编译器错误 C2853|'*标识符*： 非静态数据成员不能具有包含 auto 的类型|
|[编译器错误 C2854](compiler-error-c2854.md)|#pragma hdrstop 中出现语法错误|
|[编译器错误 C2855](compiler-error-c2855.md)|命令行选项*选项*与预编译头不一致|
|[编译器错误 C2856](compiler-error-c2856.md)|#pragma hdrstop #if 块内不能为|
|[编译器错误 C2857](compiler-error-c2857.md)|#include 语句中指定用 /Yc*文件名*源代码文件中找不到命令行选项|
|[编译器错误 C2858](compiler-error-c2858.md)|命令行选项 /Yc (/Fd*文件名*) 不一致，预编译标头，使用 /Fd*filename*|
|[编译器错误 C2859](compiler-error-c2859.md)|*文件名*不是*filetype* ，创建此预编译标头时使用的文件重新创建预编译标头。|
|[编译器错误 C2860](compiler-error-c2860.md)|void 不能是参数类型，除了 (void)|
|[编译器错误 C2861](compiler-error-c2861.md)|'*声明*： 不能定义接口成员函数|
|[编译器错误 C2862](compiler-error-c2862.md)|'*接口*： 接口只能有公共成员|
|[编译器错误 C2863](compiler-error-c2863.md)|'*接口*： 接口不能有友元|
|[编译器错误 C2864](compiler-error-c2864.md)|'*标识符*： 带有类内初始值设定项的静态数据成员/模板变量必须具有非易失性常量整型类型|
|[编译器错误 C2865](compiler-error-c2865.md)|'*运算符*： 非法比较的对象指针/句柄|
|编译器错误 C2866|已过时。|
|[编译器错误 C2867](compiler-error-c2867.md)|'*标识符*： 不是命名空间|
|[编译器错误 C2868](compiler-error-c2868.md)|'*标识符*： 非法的 using 声明语法; 预期的限定名称|
|[编译器错误 C2869](compiler-error-c2869.md)|'*标识符*： 已定义为命名空间|
|[编译器错误 C2870](compiler-error-c2870.md)|'*标识符*： 命名空间定义必须出现在文件范围内或在另一个命名空间定义立即出现|
|[编译器错误 C2871](compiler-error-c2871.md)|'*标识符*： 具有此名称的命名空间不存在|
|[编译器错误 C2872](compiler-error-c2872.md)|'*标识符*： 不明确的符号|
|[编译器错误 C2873](compiler-error-c2873.md)|'*符号*： 不能在使用声明中使用符号|
|[编译器错误 C2874](compiler-error-c2874.md)|using 声明导致的多个声明 '*标识符*|
|[编译器错误 C2875](compiler-error-c2875.md)|using 声明导致的多个声明 '*类*::*标识符*|
|[编译器错误 C2876](compiler-error-c2876.md)|'*类*::*成员*： 并非所有重载都都可访问|
|[编译器错误 C2877](compiler-error-c2877.md)|'*成员*不能从访问*类*|
|[编译器错误 C2878](compiler-error-c2878.md)|'*标识符*： 命名空间或类的此名称不存在|
|[编译器错误 C2879](compiler-error-c2879.md)|'*标识符*： 只有现有命名空间可以由命名空间别名定义提供的替代名称|
|编译器错误 C2880|__swi 或 __hvc 需要一个有效常量作为第一个参数 （SWI 号）|
|[编译器错误 C2881](compiler-error-c2881.md)|'*标识符*： 已使用的别名为*类*|
|[编译器错误 C2882](compiler-error-c2882.md)|'*标识符*： 非法使用表达式中的命名空间标识符|
|[编译器错误 C2883](compiler-error-c2883.md)|'*函数*： 函数声明与冲突'*标识符*引入的 using 声明|
|[编译器错误 C2884](compiler-error-c2884.md)|'*标识符*： 引入使用声明本地函数与冲突的'*函数*|
|[编译器错误 C2885](compiler-error-c2885.md)|'*类*::*标识符*： 不是有效使用的声明在非类范围内|
|[编译器错误 C2886](compiler-error-c2886.md)|'*类*::*标识符*： 不能在成员 using 声明中使用符号|
|编译器错误 C2887|__swi 或 __hvc 的参数不能具有超过五个参数 （SWI 号，r0-r3）|
|[编译器错误 C2888](compiler-error-c2888.md)|'*标识符*： 不能在命名空间中定义符号*命名空间*|
|编译器错误 C2889|'*类*： 托管/WinRT 类类型不能是虚拟基类|
|[编译器错误 C2890](compiler-error-c2890.md)|'*类*: ref 类只能有一个非接口基类|
|[编译器错误 C2891](compiler-error-c2891.md)|'*参数*： 不能采用一个模板参数的地址|
|[编译器错误 C2892](compiler-error-c2892.md)|局部类不应有成员模板|
|[编译器错误 C2893](compiler-error-c2893.md)|未能特殊化函数模板*模板*|
|[编译器错误 C2894](compiler-error-c2894.md)|模板不能声明为具有 C 链接|
|编译器错误 C2895|'*声明*： 无法显式实例化已用 dllimport 声明的函数模板|
|[编译器错误 C2896](compiler-error-c2896.md)|'*function1*： 不能使用函数模板/泛型'*function2*作为函数参数|
|[编译器错误 C2897](compiler-error-c2897.md)|析构函数/终结器不能是函数模板|
|[编译器错误 C2898](compiler-error-c2898.md)|'*声明*： 不能是虚成员函数模板|
|编译器错误 C2899|已过时。|

## <a name="see-also"></a>请参阅

[C /C++编译器和生成工具错误和警告](../compiler-errors-1/c-cpp-build-errors.md) \
[编译器错误 C2000-C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
