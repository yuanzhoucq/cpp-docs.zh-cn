---
title: "numeric_limits 类 | Microsoft Docs"
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
  - "std::numeric_limits"
  - "std.numeric_limits"
  - "numeric_limits"
  - "limits/std::numeric_limits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "numeric_limits 类"
ms.assetid: 9e817177-0e91-48e6-b680-0531c4b26625
caps.latest.revision: 26
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# numeric_limits 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

该模板类描述内置数字类型的算术属性。  
  
## 语法  
  
```  
template<classType> class numeric_limits  
```  
  
#### 参数  
 `Type`  
 正在测试、查询或设置其属性的基础元素数据类型。  
  
## 备注  
 标头为类型 `wchar_t`、`bool`、`char`、`signed char`、`unsigned char`、`short`、`unsigned short`、`int`、`unsigned int`、`long`、`unsigned long`、`float`、`double`、`long double`**、**`long long`、`unsigned long long`、`char16_t` 和 `char32_t` 定义显式专用化。 对于这些显式专用化，成员 [numeric\_limits::is\_specialized](../Topic/numeric_limits::is_specialized.md) 为 `true`，所有相关成员都具有有意义的值。 程序可提供额外的显式专用化。 该类的大多数成员函数描述或测试 `float` 的可能的实现。  
  
 对于任意专用化，所有成员均无有意义的值。 不具有有意义的值的成员对象将存储零（或 `false`），不返回有意义的值的成员函数将返回 `Type(0)`。  
  
### 静态函数和常数  
  
|||  
|-|-|  
|[denorm\_min](../Topic/numeric_limits::denorm_min.md)|返回最小的非规范化非零值。|  
|[digits](../Topic/numeric_limits::digits.md)|返回类型可以表示而不会降低精度的基数数字的位数。|  
|[digits10](../Topic/numeric_limits::digits10.md)|返回类型可以表示而不会降低精度的十进制数字的位数。|  
|[epsilon](../Topic/numeric_limits::epsilon.md)|返回数据类型可以表示的 1 与大于 1 的最小值之间的差值。|  
|[has\_denorm](../Topic/numeric_limits::has_denorm.md)|测试类型是否允许非规范化值。|  
|[has\_denorm\_loss](../Topic/numeric_limits::has_denorm_loss.md)|测试是否将准确度降低检测为非规范化损失，而不是不准确结果。|  
|[has\_infinity](../Topic/numeric_limits::has_infinity.md)|测试某一类型是否能够表示正无穷。|  
|[has\_quiet\_NaN](../Topic/numeric_limits::has_quiet_NaN.md)|测试某一类型是否能表示非信号性沉寂非数值 \(NAN\)。|  
|[has\_signaling\_NaN](../Topic/numeric_limits::has_signaling_NaN.md)|测试某一类型是否能表示信号性沉寂非数值 \(NAN\)。|  
|[infinity](../Topic/numeric_limits::infinity.md)|某一类型用于表示正无穷的值（若适用）。|  
|[is\_bounded](../Topic/numeric_limits::is_bounded.md)|测试某一类型可表示的值设置是否为有限。|  
|[is\_exact](../Topic/numeric_limits::is_exact.md)|测试针对某一类型进行的计算是否不产生舍入错误。|  
|[is\_iec559](../Topic/numeric_limits::is_iec559.md)|测试某一类型是否符合 IEC 559 标准。|  
|[is\_integer](../Topic/numeric_limits::is_integer.md)|测试某一类型是否具有具有整数表示形式。|  
|[is\_modulo](../Topic/numeric_limits::is_modulo.md)|测试某一类型是否具有具有取模表示形式。|  
|[is\_signed](../Topic/numeric_limits::is_signed.md)|测试某一类型是否具有带符号的表示形式。|  
|[is\_specialized](../Topic/numeric_limits::is_specialized.md)|测试某一类型是否具有在模板类 `numeric_limits` 中定义的显式专用化。|  
|[lowest](../Topic/numeric_limits::lowest.md)|返回最小的负有限值。|  
|[max](../Topic/numeric_limits::max.md)|返回某个类型的最大有限值。|  
|[max\_digits10](../Topic/numeric_limits::max_digits10.md)|返回确保类型的两个非重复值具有不同的十进制表示形式所需的十进制数字的位数。|  
|[max\_exponent](../Topic/numeric_limits::max_exponent.md)|返回最大正整数指数，当计算基数的该指数次幂时，浮点类型可将其表示为有限值。|  
|[max\_exponent10](../Topic/numeric_limits::max_exponent10.md)|返回最大正整数指数，当计算 10 的该指数次幂时，浮点类型可将其表示为有限值。|  
|[min](../Topic/numeric_limits::min.md)|返回某个类型的最小规范化值。|  
|[min\_exponent](../Topic/numeric_limits::min_exponent.md)|返回最大负整数指数，当计算基数的该指数次幂时，浮点类型可将其表示为有限值。|  
|[min\_exponent10](../Topic/numeric_limits::min_exponent10.md)|返回最大负整数指数，当计算 10 的该指数次幂时，浮点类型可将其表示为有限值。|  
|[quiet\_NaN](../Topic/numeric_limits::quiet_NaN.md)|返回类型的静默非数值 \(NAN\) 表示形式。|  
|[radix](../Topic/numeric_limits::radix.md)|返回用于表示类型的整数底数（称为基数）。|  
|[round\_error](../Topic/numeric_limits::round_error.md)|返回类型的最大舍入误差值。|  
|[round\_style](../Topic/numeric_limits::round_style.md)|返回一个值，该值描述可供实现选择用于将浮点值舍入为整数值的各种方法。|  
|[signaling\_NaN](../Topic/numeric_limits::signaling_NaN.md)|返回类型的信令非数值 \(NAN\) 表示形式。|  
|[tinyness\_before](../Topic/numeric_limits::tinyness_before.md)|测试某个类型是否可在舍入某个值之前确定该值太小而无法表示为规范化值。|  
|[traps](../Topic/numeric_limits::traps.md)|测试是否为某个类型实现了报告算术异常的捕获。|  
  
## 要求  
 **标头：**\<limits\>  
  
 **命名空间：**std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)