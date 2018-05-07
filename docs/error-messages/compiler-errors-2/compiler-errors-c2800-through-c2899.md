---
title: 编译器错误 C2800 到 C2899 |Microsoft 文档
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
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
dev_langs:
- C++
ms.assetid: e5de1e92-746a-4315-a331-c5d9efb76dbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc85ab15a262a5f4976fcdc7278401a0d9a128d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-errors-c2800-through-c2899"></a>编译器错误 C2800 到 C2899

本部分中的文档的文章说明由编译器生成的错误消息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>错误消息

|Error|消息|
|-----------|-------------|
|[编译器错误 C2800](compiler-error-c2800.md)|运算符*运算符*无法进行重载|
|[编译器错误 C2801](compiler-error-c2801.md)|*成员*必须为非静态成员|
|[编译器错误 C2802](compiler-error-c2802.md)|静态成员运算符*运算符*没有形参|
|[编译器错误 C2803](compiler-error-c2803.md)|运算符*运算符*必须具有至少一个类类型的正式参数|
|[编译器错误 C2804](compiler-error-c2804.md)|二进制运算符*运算符*的参数太多|
|[编译器错误 C2805](compiler-error-c2805.md)|二进制运算符*运算符*具有参数太少|
|[编译器错误 C2806](compiler-error-c2806.md)|运算符*运算符*具有过多的正式参数|
|[编译器错误 C2807](compiler-error-c2807.md)|第二个形参以后缀运算符*运算符*必须是 'int'|
|[编译器错误 C2808](compiler-error-c2808.md)|一元运算符*运算符*具有过多的正式参数|
|[编译器错误 C2809](compiler-error-c2809.md)|运算符*运算符*没有形参|
|[编译器错误 C2810](compiler-error-c2810.md)|*接口*： 接口只能从另一个接口继承|
|[编译器错误 C2811](compiler-error-c2811.md)|*type1*： 不能继承自*type2*，ref 类只能继承自 ref 类或接口类|
|[编译器错误 C2812](compiler-error-c2812.md)|#import 不支持使用 /clr: pure 和 /clr: safe|
|[编译器错误 C2813](compiler-error-c2813.md)|#import 不支持 /MP|
|[编译器错误 C2814](compiler-error-c2814.md)|*成员*： 本机类型不能嵌套在托管/WinRT 类型*类*|
|[编译器错误 C2815](compiler-error-c2815.md)|operator delete： 第一个形参必须是 void *，但*类型 * 已使用|
|编译器错误 C2816|已过时。|
|[编译器错误 C2817](compiler-error-c2817.md)|operator delete 的返回类型必须为 void|
|[编译器错误 C2818](compiler-error-c2818.md)|应用程序的重载 operator-> 是通过类型的递归*类*|
|[编译器错误 C2819](compiler-error-c2819.md)|类型*类*没有-> 重载的成员 operator|
|编译器错误 C2820|已过时。|
|[编译器错误 C2821](compiler-error-c2821.md)|operator new 的第一个正式参数必须是 size_t|
|编译器错误 C2822|此平台上不支持本地展开|
|[编译器错误 C2823](compiler-error-c2823.md)|typedef 模板/泛型是非法的|
|[编译器错误 C2824](compiler-error-c2824.md)|operator new 必须是返回类型 void *|
|[编译器错误 C2825](compiler-error-c2825.md)|*标识符*： 必须是类或命名空间在后面带有::|
|编译器错误 C2826|已过时。|
|[编译器错误 C2827](compiler-error-c2827.md)|运算符*运算符*不能全局重写与一元窗体|
|[编译器错误 C2828](compiler-error-c2828.md)|运算符*运算符*不能全局重写与二进制格式|
|[编译器错误 C2829](compiler-error-c2829.md)|运算符*运算符*不能具有变量参数列表|
|[编译器错误 C2830](compiler-error-c2830.md)|仅放置到 operator new 的参数可以具有默认值|
|[编译器错误 C2831](compiler-error-c2831.md)|运算符*运算符*不能具有默认参数|
|编译器错误 C2832|*标识符*： 引用类型不能为值初始化|
|[编译器错误 C2833](compiler-error-c2833.md)|运算符*令牌*不是可识别的运算符或类型|
|[编译器错误 C2834](compiler-error-c2834.md)|运算符*运算符*必须是全局限定|
|[编译器错误 C2835](compiler-error-c2835.md)|用户定义的转换*类型*不接受形参|
|编译器错误 C2836|*标识符*： 一个联合只能有一个非静态数据成员可能有默认成员初始值设定项|
|编译器错误 C2837|*函数*： 不能在同一函数中使用 OpenMP 指令和 #pragma loop(hint_parallel)|
|[编译器错误 C2838](compiler-error-c2838.md)|*标识符*： 非法的限定的名称，在成员声明|
|[编译器错误 C2839](compiler-error-c2839.md)|无效的返回类型*类型*的重载 operator->|
|编译器错误 C2840|指令字参数不是常量|
|编译器错误 C2841|注册自变量不是常量|
|[编译器错误 C2842](compiler-error-c2842.md)|*类*： 托管/WinRT 类型不能定义自己 operator new 或运算符删除|
|[编译器错误 C2843](compiler-error-c2843.md)|*成员*： 不能获取非静态数据成员的地址或托管/WinRT 类型的方法|
|[编译器错误 C2844](compiler-error-c2844.md)|*标识符*： 不能为接口成员*接口*|
|[编译器错误 C2845](compiler-error-c2845.md)|*类型*： 不允许对此类型的指针算术|
|[编译器错误 C2846](compiler-error-c2846.md)|*接口*： 接口不能有一个构造函数|
|[编译器错误 C2847](compiler-error-c2847.md)|无法将 sizeof 应用到托管/WinRT 类型*类*|
|编译器错误 C2848|*类*： 托管/WinRT 类型不能为联合的成员|
|[编译器错误 C2849](compiler-error-c2849.md)|*接口*： 接口不能具有析构函数|
|[编译器错误 C2850](compiler-error-c2850.md)|*构造*： 仅允许在文件范围内; 可能不在的嵌套构造|
|编译器错误 C2851|*枚举*： 公共 WinRT 枚举可以仅使用 int 或 unsigned 的 int 类型的基类型|
|编译器错误 C2852|*标识符*： 可以在类中初始化只有数据成员|
|编译器错误 C2853|*标识符*： 非静态数据成员不能具有包含 auto 的类型|
|[编译器错误 C2854](compiler-error-c2854.md)|#pragma hdrstop 中存在语法错误|
|[编译器错误 C2855](compiler-error-c2855.md)|命令行选项*选项*不一致，出现预编译标头|
|[编译器错误 C2856](compiler-error-c2856.md)|在一个 #if 块内不能为 #pragma hdrstop|
|[编译器错误 C2857](compiler-error-c2857.md)|#include 语句指定用 /Yc*filename*源文件中找不到命令行选项|
|[编译器错误 C2858](compiler-error-c2858.md)|命令行选项 /Yc (/Fd*filename*) 不一致，出现预编译标头，使用 /Fd*filename*|
|[编译器错误 C2859](compiler-error-c2859.md)|*filename*不*filetype*时创建此预编译标头，使用的文件重新创建预编译标头。|
|[编译器错误 C2860](compiler-error-c2860.md)|void 不能是自变量类型，除外 (void)|
|[编译器错误 C2861](compiler-error-c2861.md)|*声明*： 接口成员函数不能定义|
|[编译器错误 C2862](compiler-error-c2862.md)|*接口*： 接口仅可具有公共成员|
|[编译器错误 C2863](compiler-error-c2863.md)|*接口*： 接口不能具有友元|
|[编译器错误 C2864](compiler-error-c2864.md)|*标识符*： 在类初始值设定项的静态数据成员/模板变量必须具有非易失性常量整型|
|[编译器错误 C2865](compiler-error-c2865.md)|*运算符*： 非法的对象指针/句柄的比较|
|编译器错误 C2866|已过时。|
|[编译器错误 C2867](compiler-error-c2867.md)|*标识符*： 不是命名空间|
|[编译器错误 C2868](compiler-error-c2868.md)|*标识符*： 非法使用声明语法; 预期的限定名称|
|[编译器错误 C2869](compiler-error-c2869.md)|*标识符*： 已定义为命名空间|
|[编译器错误 C2870](compiler-error-c2870.md)|*标识符*： 命名空间定义必须出现在文件范围内或在另一个命名空间定义立即|
|[编译器错误 C2871](compiler-error-c2871.md)|*标识符*： 具有此名称的命名空间不存在|
|[编译器错误 C2872](compiler-error-c2872.md)|*标识符*： 不明确的符号|
|[编译器错误 C2873](compiler-error-c2873.md)|*符号*： 符号不能在 using 声明|
|[编译器错误 C2874](compiler-error-c2874.md)|使用声明会导致出现的多个声明*标识符*|
|[编译器错误 C2875](compiler-error-c2875.md)|使用声明会导致出现的多个声明*类*::*标识符*|
|[编译器错误 C2876](compiler-error-c2876.md)|*类*::*成员*： 并非所有重载都都可访问|
|[编译器错误 C2877](compiler-error-c2877.md)|*成员*不能从访问*类*|
|[编译器错误 C2878](compiler-error-c2878.md)|*标识符*： 命名空间或类的此名称不存在|
|[编译器错误 C2879](compiler-error-c2879.md)|*标识符*： 只有现有命名空间可以由命名空间别名定义提供备用名称|
|编译器错误 C2880|__swi 或 __hvc 需要有效的常量的作为第一个参数 （SWI 数）|
|[编译器错误 C2881](compiler-error-c2881.md)|*标识符*： 已使用的别名为*类*|
|[编译器错误 C2882](compiler-error-c2882.md)|*标识符*： 非法使用表达式中的命名空间标识符|
|[编译器错误 C2883](compiler-error-c2883.md)|*函数*： 函数声明与冲突*标识符*引入的 using 声明|
|[编译器错误 C2884](compiler-error-c2884.md)|*标识符*： 引起与局部函数使用声明冲突*函数*|
|[编译器错误 C2885](compiler-error-c2885.md)|*类*::*标识符*： 不使用的声明无效非类范围内|
|[编译器错误 C2886](compiler-error-c2886.md)|*类*::*标识符*： 符号不能在成员 using 声明|
|编译器错误 C2887|__swi 或 __hvc 不能具有五个以上的自变量 （SWI 数字，r0-r3）|
|[编译器错误 C2888](compiler-error-c2888.md)|*标识符*： 无法在命名空间中定义符号*命名空间*|
|编译器错误 C2889|*类*： 托管/WinRT 类类型不能为虚拟基类|
|[编译器错误 C2890](compiler-error-c2890.md)|*类*: ref 类只能有一个非接口基类|
|[编译器错误 C2891](compiler-error-c2891.md)|*参数*： 不能采用一个模板参数的地址|
|[编译器错误 C2892](compiler-error-c2892.md)|局部类不应具有成员模板|
|[编译器错误 C2893](compiler-error-c2893.md)|未能特殊化函数模板*模板*|
|[编译器错误 C2894](compiler-error-c2894.md)|模板不能声明为具有 C 链接|
|编译器错误 C2895|*声明*： 不能显式实例化已通过 dllimport 声明的函数模板|
|[编译器错误 C2896](compiler-error-c2896.md)|*function1*： 不能使用函数模板/泛型*function2*作为函数参数|
|[编译器错误 C2897](compiler-error-c2897.md)|析构函数/终结器不能为函数模板|
|[编译器错误 C2898](compiler-error-c2898.md)|*声明*： 不能是虚拟成员函数模板|
|编译器错误 C2899|已过时。|
