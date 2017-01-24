---
title: "&lt;valarray&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.<valarray>"
  - "valarray/std::<valarray>"
  - "std::<valarray>"
  - "<valarray>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "valarray 标头"
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
caps.latest.revision: 19
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;valarray&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义模板类 valarray 和大量支持模板类和函数。  
  
## 语法  
  
```  
  
#include <valarray>  
  
```  
  
## 备注  
 为了提高性能，允许这些模板类和函数有异常的纬度。  具体而言，任何返回类型 **valarray\<**T1**\>** 的函数可能会返回某个其他类型 T2 的对象。  在这种情况下，任何接受类型 **valarray\<**T2**\>** 的一个或多个参数的函数必须具有接受这些参数（每个替换为类型 T2 的参数）的任意组合的重载。  
  
### Functions  
  
|||  
|-|-|  
|[abs](../Topic/abs%20\(%3Cvalarray%3E\).md)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的绝对值。|  
|[acos](../Topic/acos%20\(%3Cvalarray%3E\).md)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的反余弦值。|  
|[asin](../Topic/asin%20\(%3Cvalarray%3E\).md)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的反正弦值。|  
|[atan](../Topic/atan%20\(%3Cvalarray%3E\).md)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的反正切主值。|  
|[atan2](../Topic/atan2%20\(%3Cvalarray%3E\).md)|返回的 valarrays 的元素等于由 valarray 常量和元素的组合指定的笛卡尔组件的反正切值。|  
|[cos](../Topic/cos%20\(%3Cvalarray%3E\).md)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的余弦值。|  
|[cosh](../Topic/cosh%20\(%3Cvalarray%3E\).md)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的双曲余弦值。|  
|[exp](../Topic/exp%20\(%3Cvalarray%3E\).md)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的自然指数。|  
|[log](../Topic/log%20\(%3Cvalarray%3E\).md)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的自然对数。|  
|[log10](../Topic/log10%20\(%3Cvalarray%3E\).md)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的以 10 为底的对数或常用对数。|  
|[pow](../Topic/pow%20\(%3Cvalarray%3E\).md)|对输入 valarray 的元素和常数进行操作，返回的 valarray 的元素等于由输入 valarray 的元素所指定的基数，或者等于具有一定指数的常数所指定的基数，该指数由输入 valarray 的元素或常数指定。|  
|[sin](../Topic/sin%20\(%3Cvalarray%3E\).md)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的正弦值。|  
|[sinh](../Topic/sinh%20\(%3Cvalarray%3E\).md)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的双曲正弦值。|  
|[sqrt](../Topic/sqrt%20\(%3Cvalarray%3E\).md)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的平方根。|  
|[swap](../Topic/swap%20\(%3Cvalarray%3E\).md)||  
|[tan](../Topic/tan%20\(%3Cvalarray%3E\).md)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的正切值。|  
|[tanh](../Topic/tanh%20\(%3Cvalarray%3E\).md)|对输入 valarray 的元素进行操作，返回的 valarray 的元素等于输入 valarray 的元素的双曲正切值。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Cvalarray%3E\).md)|测试两个相同大小的 valarray 的对应元素是否不相等或者 valarray 的所有元素是否都不等于 valarray 元素类型的指定值。|  
|[operator%](../Topic/operator%25.md)|获取 valarray 的元素类型的指定值除以两个大小相同的 valarray 的对应元素所得的余数或除以 valarray 所得的余数，或 valarray 除以指定值所得的余数。|  
|[operator&](../Topic/operator&.md)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和元素类型的指定值之间的按位 **AND**。|  
|[operator&&](../Topic/operator&&.md)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的逻辑 **AND**。|  
|[运算符 \>](../Topic/operator%3E%20\(%3Cvalarray%3E\).md)|测试某个 valarray 的元素是否大于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于或小于 valarray 元素类型的指定值。|  
|[运算符 \>\=](../Topic/operator%3E=%20\(%3Cvalarray%3E\).md)|测试某个 valarray 的元素是否大于或等于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于等于或小于等于某个指定值。|  
|[运算符 \>\>](../Topic/operator%3E%3E%20\(%3Cvalarray%3E\).md)|将 valarray 的每个元素的位以指定数位向右移位，或按由第二个 valarray 指定的元素指向值向右移位。|  
|[运算符 \<](../Topic/operator%3C%20\(%3Cvalarray%3E\).md)|测试某个 valarray 的元素是否小于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于或小于某个指定值。|  
|[运算符 \<\=](../Topic/operator%3C=%20\(%3Cvalarray%3E\).md)|测试某个 valarray 的元素是否小于或等于某个与其大小相等的 valarray 的元素，或者 valarray 的所有元素都是否都大于等于或小于等于某个指定值。|  
|[运算符 \<\<](../Topic/operator%3C%3C%20\(%3Cvalarray%3E\).md)|将 valarray 的每个元素的位以指定数位向左移位，或按由第二个 valarray 指定的元素指向值向左移位。|  
|[operator\*](../Topic/operator*%20\(%3Cvalarray%3E\).md)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的元素指向乘积。|  
|[运算符 \+](../Topic/operator+%20\(%3Cvalarray%3E\).md)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的元素指向总和。|  
|[operator\-](../Topic/operator-%20\(%3Cvalarray%3E\)2.md)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的元素指向差值。|  
|[运算符 \/](../Topic/operator-%20\(%3Cvalarray%3E\)1.md)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的元素指向商。|  
|[operator\=\=](../Topic/operator==%20\(%3Cvalarray%3E\).md)|测试两个相同大小的 valarray 的对应元素是否相等或者 valarray 的所有元素是否都等于 valarray 元素类型的指定值。|  
|[operator^](../Topic/operator%5E.md)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和元素类型的指定值之间的按位异 `OR`。|  
|[operator&#124;](../Topic/operator%7C.md)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和元素类型的指定值之间的按位 `OR`。|  
|[operator&#124;&#124;](../Topic/operator%7C%7C.md)|获取两个大小相等的 valarray 的对应元素之间的或 valarray 和 valarray 元素类型的指定值之间的逻辑 `OR`。|  
  
### 类  
  
|||  
|-|-|  
|[gslice 类](../standard-library/gslice-class.md)|用于定义 valarray 多维切分的 valarray 实用程序类。|  
|[gslice\_array 类](../standard-library/gslice-array-class.md)|一个内部的辅助模板类，该类通过提供由 valarray 的泛切分定义的子集阵列之间的操作来支持泛切分对象。|  
|[indirect\_array 类](../standard-library/indirect-array-class.md)|一个内部的辅助模板类，该类通过提供子集阵列（通过指定父级 valarray 的索引子集进行定义）之间的操作来支持作为 valarray 的子集的对象。|  
|[mask\_array 类](../standard-library/mask-array-class.md)|一个内部的辅助模板类，该类通过提供子集阵列之间的操作来支持作为父级 valarray（使用布尔表达式指定）的子集的对象。|  
|[slice 类](../standard-library/slice-class.md)|一个用于定义 valarray 的一维矢量型子集的 valarray 实用程序类。|  
|[slice\_array 类](../standard-library/slice-array-class.md)|一个内部的辅助模板类，该类通过提供由 valarray 的切分定义的子集阵列之间的操作来支持切分对象。|  
|[valarray 类](../standard-library/valarray-class.md)|该模板类描述了一个对象，该对象控制类型 **Type** 的元素的序列，这些元素存储为数组并用于执行高速数学运算，且针对计算性能进行了优化。|  
  
### 专用化  
  
|||  
|-|-|  
|[valarray\<bool\> 类](../standard-library/valarray-bool-class.md)|类型 `bool` 的元素的模板类 valarray \<**Type**\> 的专用版本。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)