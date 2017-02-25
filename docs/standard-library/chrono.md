---
title: "&lt;chrono&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "chrono/std::chrono::nanoseconds"
  - "chrono/std::chrono::minutes"
  - "chrono/std::chrono::seconds"
  - "<chrono>"
  - "chrono/std::chrono::hours"
  - "chrono/std::chrono::milliseconds"
  - "chrono/std::chrono::microseconds"
dev_langs: 
  - "C++"
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# &lt;chrono&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包括标准标头 \< chrono \> 来定义表示和操作持续时间及时刻的类和函数。  
  
 **（Visual Studio 2015：）**已更改 `steady_clock` 的实现，以便满足 C\+\+ 标准对稳定性和单一性的要求。  `steady_clock` 现在基于 QueryPerformanceCounter\(\)，且 `high_resolution_clock` 现在是 `steady_clock` 的 typedef。  因此，在 Visual C\+\+ 中，`steady_clock::time_point` 现在是 `chrono::time_point<steady_clock>` 的 typedef；但是，其他实现不一定是这种情况。  
  
## 语法  
  
```cpp  
#include <chrono>  
```  
  
### 文本  
 \<chrono\> 标头中的文本是 literals::chrono\_literals 内联命名空间的成员。  有关详细信息，请参阅 [chrono 文本](../standard-library/chrono-literals.md)。  
  
|||  
|-|-|  
|operator "" h\(unsigned long long Val\) operator "" h\(long double Val\)|指定值表示小时。|  
|operator "" min\(unsigned long long Val\)  operator "" min\(long double Val\)|指定值表示分钟。|  
|operator "" s\(unsigned long long Val\)operator "" s\(long double Val\)|指定值表示秒。|  
|operator "" ms\(unsigned long long Val\)operator "" ms\(long double Val\)|指定值表示毫秒。|  
|operator "" us\(unsigned long long Val\)operator "" us\(long double Val\)|指定值表示微秒。|  
|operator "" ns\(unsigned long long Val\)operator "" ns\(long double Val\)|指定值表示纳秒。|  
  
### 类  
  
|名称|描述|  
|--------|--------|  
|[duration 类](../standard-library/duration-class.md)|描述保持时间间隔的类型。|  
|[time\_point 类](../standard-library/time-point-class.md)|描述表示时间点的类型。|  
  
### 结构  
  
|名称|描述|  
|--------|--------|  
|[common\_type 结构](../standard-library/common-type-structure.md)|介绍有关 `duration` 和 `time_point` 实例化的 [common\_type](../standard-library/common-type-class.md) 模板类的专用化。|  
|[duration\_values 结构](../standard-library/duration-values-structure.md)|提供 `duration` 模板参数 `Rep` 的特定值。|  
|[steady\_clock 结构](../standard-library/steady-clock-struct.md)|表示 `steady` 时钟。|  
|[system\_clock 结构](../standard-library/system-clock-structure.md)|表示基于系统实时时钟的*时钟类型*。|  
|[treat\_as\_floating\_point 结构](../standard-library/treat-as-floating-point-structure.md)|指定是否可将一种类型视为浮点类型。|  
  
### 函数  
  
|名称|描述|  
|--------|--------|  
|[duration\_cast 函数](../Topic/duration_cast%20Function.md)|将 `duration` 对象转换为指定类型。|  
|[time\_point\_cast 函数](../Topic/time_point_cast%20Function.md)|将 `time_point` 对象转换为指定类型。|  
  
### 运算符  
  
|名称|描述|  
|--------|--------|  
|[operator\- 运算符 \(STL\)](../Topic/operator-%20Operator%20\(STL\)1.md)|用于对 `duration` 和 `time_point` 对象进行减法或求反运算的运算符。|  
|[operator\!\= 运算符 \(STL\)](../Topic/operator!=%20Operator%20\(STL\).md)|与 `duration` 或 `time_point` 对象一起使用的不等运算符。|  
|[运算符取模 \(STL\)](../Topic/operator%20modulo%20\(STL\).md)|用于对 `duration` 对象进行取模操作的运算符。|  
|[operator\* 运算符 \(STL\)](../Topic/operator*%20Operator%20\(STL\).md)|`duration` 对象的乘法运算符。|  
|[operator\/ 运算符 \(STL\)](../Topic/operator-%20Operator%20\(STL\)2.md)|`duration` 对象的除法运算符。|  
|[operator\+ 运算符 \(STL\)](../Topic/operator+%20Operator%20\(STL\).md)|将 `duration` 和 `time_point` 对象相加。|  
|[operator\< Operator \(STL\)](../Topic/operator%3C%20Operator%20\(STL\).md)|确定一个 `duration` 或 `time_point` 对象是否小于另一个 `duration` 或 `time_point` 对象。|  
|[operator\<\= 运算符 \(STL\)](../Topic/operator%3C=%20Operator%20\(STL\).md)|确定一个 `duration` 或 `time_point` 对象是否小于或等于另一个 `duration` 或 `time_point` 对象。|  
|[operator\=\= Operator \(STL\)](../Topic/operator==%20Operator%20\(STL\).md)|确定两个 `duration` 对象是否表示相同长度的时间间隔，或两个 `time_point` 对象是否表示相同的时间点。|  
|[operator\> 运算符 \(STL\)](../Topic/operator%3E%20Operator%20\(STL\).md)|确定一个 `duration` 或 `time_point` 对象是否大于另一个 `duration` 或 `time_point` 对象。|  
|[operator\>\= 运算符 \(STL\)](../Topic/operator%3E=%20Operator%20\(STL\).md)|确定一个 `duration` 或 `time_point` 对象是否大于或等于另一个 `duration` 或 `time_point` 对象。|  
  
### 预定义的持续时间类型  
 有关在以下 typedefs 中使用的比率类型的详细信息，请参阅 [\<ratio\>](../standard-library/ratio.md)。  
  
|Typedef|描述|  
|-------------|--------|  
|`typedef duration<long long, nano> nanoseconds;`|时钟周期为一纳秒的 `duration` 类型的同义词。|  
|`typedef duration<long long, micro> microseconds;`|时钟周期为一微秒的 `duration` 类型的同义词。|  
|`typedef duration<long long, milli> milliseconds;`|时钟周期为一毫秒的 `duration` 类型的同义词。|  
|`typedef duration<long long> seconds;`|时钟周期为一秒的 `duration` 类型的同义词。|  
|`typedef duration<int, ratio<60> > minutes;`|时钟周期为一分钟的 `duration` 类型的同义词。|  
|`typedef duration<int, ratio<3600> > hours;`|时钟周期为一小时的 `duration` 类型的同义词。|  
  
### 文本  
 **\(C\+\+11\)**\<chrono\> 标头定义了以下[用户定义的文本](../cpp/user-defined-literals-cpp.md)，利用这些文本，可更方便地使用代码、增大代码类型的安全性和提高代码的可维护性。  这些文本在 `literals::chrono_literals` 内联命名空间中定义，并且在 std::chrono 存在于作用域中时也存在于作用域中。  
  
|文本|描述|  
|--------|--------|  
|chrono::hours operator "" h\(unsigned long long Val\)|指定整数值形式的小时数。|  
|chrono::duration\<double, ratio\<3600\> \> operator "" h\(long double Val\)|指定浮点值形式的小时数。|  
|chrono::minutes \(operator "" min\)\(unsigned long long Val\)|指定整数值形式的分钟数。|  
|chrono::duration\<double, ratio\<60\> \> \(operator "" min\)\( long double Val\)|指定浮点值形式的分钟数。|  
|chrono::seconds operator "" s\(unsigned long long Val\)|指定整数值形式的分钟数。|  
|chrono::duration\<double\> operator "" s\(long double Val\)|指定浮点值形式的描述。|  
|chrono::milliseconds operator "" ms\(unsigned long long Val\)|指定整数值形式的毫秒数。|  
|chrono::duration\<double, milli\> operator "" ms\(long double Val\)|指定浮点值形式的毫秒数。|  
|chrono::microseconds operator "" us\(unsigned long long Val\)|指定整数值形式的微秒数。|  
|chrono::duration\<double, micro\> operator "" us\(long double Val\)|指定浮点值形式的微秒数。|  
|chrono::nanoseconds operator "" ns\(unsigned long long Val\)|指定整数值形式的纳秒数。|  
|chrono::duration\<double, nano\> operator "" ns\(long double Val\)|指定浮点值形式的纳秒数。|  
|||  
  
## 备注  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)