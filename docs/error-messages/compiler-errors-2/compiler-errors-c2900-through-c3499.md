---
title: "编译器错误 C2900 C2999 到 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2900
- C2901
- C2905
- C2907
- C2915
- C2916
- C2922
- C2924
- C2925
- C2926
- C2938
- C2949
- C2950
- C2954
- C2956
- C2960
- C2961
- C2963
- C2964
- C2965
- C2966
- C2967
- C2968
- C2972
- C2980
- C2981
- C2982
- C2983
- C2984
- C2985
- C2986
- C2987
- C2997
- C2999
helpviewer_keywords:
- C2900
- C2901
- C2905
- C2907
- C2915
- C2916
- C2922
- C2924
- C2925
- C2926
- C2938
- C2949
- C2950
- C2954
- C2956
- C2960
- C2961
- C2963
- C2964
- C2965
- C2966
- C2967
- C2968
- C2972
- C2980
- C2981
- C2982
- C2983
- C2984
- C2985
- C2986
- C2987
- C2997
- C2999
dev_langs:
- C++
ms.assetid: e3440738-e11b-4878-9ae3-6bc6c53ba461
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: 6ef55aa655692e6ecbd1550bb1ace2eca01bdbad
ms.lasthandoff: 04/24/2017

---
# <a name="compiler-errors-c2900-through-c2999"></a>编译器错误 C2900 到 C2999
文档的此部分中的文章包含有关 Visual C++ 编译器错误的子部分的信息。 可在此处访问信息，或者在 Visual Studio 中的“输出”  窗口中选择错误号，然后选择 F1 键。  
  
> [!NOTE]
>  不是每个[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]错误记录在 MSDN 中。 在许多情况下，诊断消息将提供的所有可用信息。 如果你认为某个错误消息需要更多说明，请通知我们。 你可以在此页上，使用反馈表单或转到 Visual Studio 中的菜单栏，然后选择**帮助**，**报告 Bug**，或可以在提交建议或 bug 报表[Microsoft Connect](http://connect.microsoft.com/VisualStudio)。  
  
 错误和警告的 MSDN 公共论坛，可能会发现更多帮助。 [Visual c + + 语言](http://go.microsoft.com/fwlink/?LinkId=158195)论坛是有关问题和讨论有关[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]语言语法和编译器。 [Visual c + + 常规](http://go.microsoft.com/fwlink/?LinkId=158194)论坛的问题是有关[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]其他论坛中未涉及。 你还可能上查找有关错误和警告的帮助[堆栈溢出](http://stackoverflow.com/)。  
  
|错误|消息|  
|-----------|-------------|  
|编译器错误 C2900|*声明符*: WinRT 类中的成员函数模板必须为 private、 内部或 protected private|  
|编译器错误 C2901|*标识符*︰ 泛型接口或委托不能为公共|  
|[编译器错误 C2902](compiler-error-c2902.md)|*令牌*︰ 意外令牌以下模板/泛型，应为标识符|  
|[编译器错误 C2903](compiler-error-c2903.md)|*标识符*︰ 符号既既不类模板/泛型函数模板/泛型|  
|[编译器错误 C2904](compiler-error-c2904.md)|*标识符*︰ 名称已经用于当前范围中的模板|  
|编译器错误 C2905|已过时。|  
|[编译器错误 C2906](compiler-error-c2906.md)|*模板*︰ 显式专用化需要模板 <>|  
|编译器错误 C2907|注册自变量*数*未指定有效的注册数|  
|[编译器错误 C2908](compiler-error-c2908.md)|显式专用化;*模板*未实例化|  
|[编译器错误 C2909](compiler-error-c2909.md)|*标识符*︰ 函数模板的显式实例化需要返回类型|  
|[编译器错误 C2910](compiler-error-c2910.md)|*函数*︰ 不能显式专用化|  
|[编译器错误 C2911](compiler-error-c2911.md)|*成员*︰ 不能声明或在当前范围内定义|  
|[编译器错误 C2912](compiler-error-c2912.md)|显式专用化*声明*不是函数模板的专用化|  
|[编译器错误 C2913](compiler-error-c2913.md)|显式专用化;*声明*不是类模板的专用化|  
|[编译器错误 C2914](compiler-error-c2914.md)|*标识符*︰ 无法推导出模板/泛型自变量，如函数自变量是不明确|  
|编译器错误 C2915|*标识符*:*类型*不能在 WinRT 类型的已发布图面上直接使用。 使用 platform:: object ^ 改为将传递此类型|  
|编译器错误 C2916|*标识符*: [FlagsAttribute] 必须 （仅限） 上指定公共枚举具有基础类型未签名的 int|  
|[编译器错误 C2917](compiler-error-c2917.md)|*标识符*': 无效的模板参数|  
|[编译器错误 C2918](compiler-error-c2918.md)|*标识符*︰ 不能在 WinRT 类型的已发布图面上使用索引的属性|  
|[编译器错误 C2919](compiler-error-c2919.md)|*类型*︰ 不能在 WinRT 类型的已发布图面上使用运算符|  
|[编译器错误 C2920](compiler-error-c2920.md)|重定义:*类型*︰ 类模板/泛型已声明为*声明*|  
|[编译器错误 C2921](compiler-error-c2921.md)|重定义:*类型*︰ 类模板/泛型正被重新声明为*声明*|  
|编译器错误 C2922|*接口*: WinRT 接口不能包含静态成员|  
|[编译器错误 C2923](compiler-error-c2923.md)|*类型*:*标识符*不是参数的有效模板/泛型类型参数*参数*|  
|编译器错误 C2924|__declspec(interrupt) 例程参数不在 R2 中|  
|编译器错误 C2925|__declspec(interrupt) 例程不能使用浮点型数值|  
|编译器错误 C2926|*标识符*: 匿名结构中联合的成员不允许的默认成员初始值设定项|  
|[编译器错误 C2927](compiler-error-c2927.md)|*标识符*︰ 必须具有至少一个自变量调用函数模板|  
|[编译器错误 C2928](compiler-error-c2928.md)|显式实例化;*标识符*不是函数或静态数据成员的模板类*类*|  
|[编译器错误 C2929](compiler-error-c2929.md)|*声明符*︰ 显式实例化; 无法显式强制和取消模板类成员的实例化|  
|[编译器错误 C2930](compiler-error-c2930.md)|*类*︰ 模板 id 泛型 id 重新定义的枚举数为枚举*标识符*|  
|[编译器错误 C2931](compiler-error-c2931.md)|*class1*︰ 模板 id 泛型 id 重新定义的成员函数为*class2*|  
|[编译器错误 C2932](compiler-error-c2932.md)|*类型*︰ 模板 id 泛型 id 重新定义的数据成员为*标识符*|  
|[编译器错误 C2933](compiler-error-c2933.md)|*类型*︰ 模板 id 泛型 id 重新定义的 typedef 成员为*标识符*|  
|[编译器错误 C2934](compiler-error-c2934.md)|*类型*︰ 模板 id 泛型 id 重新定义为嵌套*项*of*标识符*|  
|[编译器错误 C2935](compiler-error-c2935.md)|*类型*︰ 模板 id 泛型 id 重新定义为全局函数|  
|[编译器错误 C2936](compiler-error-c2936.md)|*类型*︰ 模板 id 泛型 id 重新定义为全局数据变量|  
|[编译器错误 C2937](compiler-error-c2937.md)|*类型*︰ 模板 id 泛型 id 重新定义为全局 typedef|  
|编译器错误 C2938|*标识符*︰ 未能特殊化别名模板|  
|[编译器错误 C2939](compiler-error-c2939.md)|*类型*︰ 模板 id 泛型 id 重新定义为局部数据变量|  
|[编译器错误 C2940](compiler-error-c2940.md)|*类型*︰ 模板 id 泛型 id 重新定义为局部 typedef|  
|[编译器错误 C2941](compiler-error-c2941.md)|*类型*︰ 模板 id 泛型 id 重新定义为本地*项*|  
|[编译器错误 C2942](compiler-error-c2942.md)|*类型*︰ 模板 id 泛型 id 重新定义为函数的形参|  
|[编译器错误 C2943](compiler-error-c2943.md)|*类型*︰ 模板 id 泛型 id 重新定义为模板的类型参数|  
|[编译器错误 C2944](compiler-error-c2944.md)|*类型*︰ 模板 id 泛型 id 重新定义为模板值自变量|  
|[编译器错误 C2945](compiler-error-c2945.md)|显式实例化不引用模板类专用化|  
|[编译器错误 C2946](compiler-error-c2946.md)|显式实例化;*类型*不是模板类专用化|  
|[编译器错误 C2947](compiler-error-c2947.md)|应为 > 若要终止模板自变量，找到*令牌*|  
|[编译器错误 C2948](compiler-error-c2948.md)|显式实例化;存储类说明符*说明符*专用化中不允许|  
|编译器错误 C2949|/kernel 不支持 thread_local|  
|编译器错误 C2950|已过时。|  
|[编译器错误 C2951](compiler-error-c2951.md)|模板/泛型声明只能在全局命名空间或类范围内|  
|[编译器错误 C2952](compiler-error-c2952.md)|*声明*︰ 模板/泛型声明缺少模板/泛型参数列表|  
|[编译器错误 C2953](compiler-error-c2953.md)|*类型*︰ 类模板已经定义|  
|编译器错误 C2954|指令字参数不在范围中|  
|[编译器错误 C2955](compiler-error-c2955.md)|*类型*︰ 类模板/泛型的使用需要模板/泛型自变量列表|  
|编译器错误 C2956|调整了大小的释放函数 operator delete （void *，size_t） 将被选择作为放置释放函数。|  
|[编译器错误 C2957](compiler-error-c2957.md)|*令牌*': 无效的左侧分隔符︰ 预期 <|  
|[编译器错误 C2958](compiler-error-c2958.md)|左侧*分隔符*位于*文件*(*line_number*) 不正确匹配|  
|[编译器错误 C2959](compiler-error-c2959.md)|泛型类或函数不能是模板的成员|  
|编译器错误 C2960|已过时。|  
|编译器错误 C2961|*函数*︰ 显式实例化不一致，以前的显式实例化未指定*参数*|  
|[编译器错误 C2962](compiler-error-c2962.md)|语法错误:*令牌*︰ 模板类成员函数定义要作为结束颜色应}|  
|编译器错误 C2963|已过时。|  
|编译器错误 C2964|已过时。|  
|编译器错误 C2965|__declspec (*说明符*) 不支持 /kernel|  
|编译器错误 C2966|*identifier1*︰ 必须具有为其基类的相同 __declspec(code_seg(...))*identifier2*|  
|编译器错误 C2967|*标识符*︰ 重写的虚函数必须具有相同 __declspec(code_seg(...)) 用作重写虚拟函数|  
|编译器错误 C2968|*标识符*︰ 递归别名声明|  
|[编译器错误 C2969](compiler-error-c2969.md)|语法错误:*令牌*︰ 成员函数定义要作为结束颜色应}|  
|[编译器错误 C2970](compiler-error-c2970.md)|*类型*︰ 模板参数*参数*:*参数*︰ 涉及带内部链接的对象的表达式不能用作非类型参数|  
|[编译器错误 C2971](compiler-error-c2971.md)|*类型*︰ 模板参数*参数*:*参数*︰ 非静态存储持续时间的变量不能用作非类型参数|  
|编译器错误 C2972|*类型*︰ 模板参数*参数*︰ 非类型参数的类型无效|  
|[编译器错误 C2973](compiler-error-c2973.md)|*模板*': 无效的模板自变量*数*|  
|[编译器错误 C2974](compiler-error-c2974.md)|*类型*': 无效的模板/泛型自变量*参数*，预期的类型|  
|[编译器错误 C2975](compiler-error-c2975.md)|*类型*︰ 模板参数无效*参数*，应输入编译时常量表达式|  
|[编译器错误 C2976](compiler-error-c2976.md)|*类型*︰ 模板/泛型参数太少|  
|[编译器错误 C2977](compiler-error-c2977.md)|*类型*︰ 模板/泛型参数太多|  
|[编译器错误 C2978](compiler-error-c2978.md)|语法错误︰ 预期*keyword1*'*keyword2*; 却发现类型*类型*; 非类型泛型中不支持参数|  
|[编译器错误 C2979](compiler-error-c2979.md)|泛型中不支持显式专用化|  
|编译器错误 C2980|C++ 异常处理不受 /kernel 支持|  
|编译器错误 C2981|动态形式*关键字*/kernel 不支持|  
|编译器错误 C2982|*声明*︰ 使用不同 __declspec(code_seg(...))︰ 已*identifier1*立即*identifier2*|  
|编译器错误 C2983|*声明*︰ 所有声明必须都具有相同 __declspec(code_seg(...))|  
|编译器错误 C2984|已过时。|  
|编译器错误 C2985|*参数*: __declspec(code_seg(...)) 的自变量必须是文本部分|  
|编译器错误 C2986|*标识符*: __declspec(code_seg(...)) 只能应用于类或函数|  
|编译器错误 C2987|声明不能有两个 __declspec (code_seg (*标识符*')) 和 __declspec (code_seg (*值*'))|  
|[编译器错误 C2988](compiler-error-c2988.md)|不可识别的模板声明/定义|  
|[编译器错误 C2989](compiler-error-c2989.md)|*类*︰ 已作为非类模板/泛型声明类模板/泛型|  
|[编译器错误 C2990](compiler-error-c2990.md)|*类*︰ 已作为类模板/泛型声明非类模板/泛型|  
|[编译器错误 C2991](compiler-error-c2991.md)|重定义的模板/泛型参数*参数*|  
|[编译器错误 C2992](compiler-error-c2992.md)|*类*': 无效或缺少模板/泛型参数列表|  
|[编译器错误 C2993](compiler-error-c2993.md)|*类型*︰ 非法类型为非类型模板参数*标识符*|  
|[编译器错误 C2994](compiler-error-c2994.md)|模板参数列表中未命名的类|  
|[编译器错误 C2995](compiler-error-c2995.md)|*声明*︰ 函数模板已经定义|  
|[编译器错误 C2996](compiler-error-c2996.md)|*函数*︰ 递归函数模板定义|  
|编译器错误 C2997|*函数*︰ 数组界限不能从默认成员初始值设定项中推导|  
|[编译器错误 C2998](compiler-error-c2998.md)|*声明符*︰ 不能为模板定义|  
|编译器错误 C2999|请未知错误，选择技术支持命令的 Visual c + + 帮助菜单上，或打开技术支持帮助文件了解详细信息|  

