---
title: "moneypunct 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "moneypunct"
  - "std.moneypunct"
  - "xlocmon/std::moneypunct"
  - "std::moneypunct"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "moneypunct 类"
ms.assetid: cf2650da-3e6f-491c-95d5-23e57f582ee6
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# moneypunct 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述一个对象来充当区域设置 facet，以便描述用来表示货币输入字段或货币输出字段的 `CharType` 类序列。  如果模板参数 `Intl` 为 `true`，则遵守国际约定。  
  
## 语法  
  
```  
template<class CharType, bool Intl>   
   class moneypunct;  
```  
  
#### 参数  
 `CharType`  
 在程序中用于对字符进行编码的类型。  
  
 `Intl`  
 一种用于指定是否遵守国际约定的标志。  
  
## 备注  
 对于任何区域设置 facet，静态对象 ID 的初始存储值为零。  首次尝试访问其存储值后，将在 **id** 中存储唯一正值。  
  
 常量静态对象 intl 用于存储模板参数 **Intl** 的值。  
  
### 构造函数  
  
|||  
|-|-|  
|[moneypunct](../Topic/moneypunct::moneypunct.md)|`moneypunct` 类型对象的构造函数。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/moneypunct::char_type.md)|一种类型，此类型用于描述区域设置使用的字符。|  
|[string\_type](../Topic/moneypunct::string_type.md)|一种类型，此类型描述包含 `CharType` 类型字符的字符串。|  
  
### 成员函数  
  
|||  
|-|-|  
|[curr\_symbol](../Topic/moneypunct::curr_symbol.md)|返回要用作货币符号的区域设置特定元素序列。|  
|[decimal\_point](../Topic/moneypunct::decimal_point.md)|返回要用作小数点符号的区域设置特定元素序列。|  
|[do\_curr\_symbol](../Topic/moneypunct::do_curr_symbol.md)|一种受保护的虚拟成员函数，可返回要用作货币符号的区域设置特定元素序列。|  
|[do\_decimal\_point](../Topic/moneypunct::do_decimal_point.md)|一种受保护的虚拟成员函数，通过调用此函数可返回要用作小数点符号的区域设置特定元素序列。|  
|[do\_frac\_digits](../Topic/moneypunct::do_frac_digits.md)|此受保护的虚拟成员函数可返回一个在任何小数点右侧显示的位数计数。|  
|[do\_grouping](../Topic/moneypunct::do_grouping.md)|此受保护的虚拟成员函数可返回一个区域设置特定规则，用于确定如何对任何小数点左侧的数字进行分组。|  
|[do\_neg\_format](../Topic/moneypunct::do_neg_format.md)|一种受保护的虚拟成员函数，通过调用此函数可返回一个区域设置特定规则，用于对包含负数的输出结果进行格式化。|  
|[do\_negative\_sign](../Topic/moneypunct::do_negative_sign.md)|一种受保护的虚拟成员函数，通过调用此函数可返回要用作负号符号的区域设置特定元素序列。|  
|[do\_pos\_format](../Topic/moneypunct::do_pos_format.md)|一种受保护的虚拟成员函数，通过调用此函数可返回一个区域设置特定规则，用于对包含正数的输出结果进行格式化。|  
|[do\_positive\_sign](../Topic/moneypunct::do_positive_sign.md)|一种受保护的虚拟成员函数，通过调用此函数可返回要用作正号符号的区域设置特定元素序列。|  
|[do\_thousands\_sep](../Topic/moneypunct::do_thousands_sep.md)|一种受保护的虚拟成员函数，通过调用此函数可返回要用作千位分隔符号的区域设置特定元素序列。|  
|[frac\_digits](../Topic/moneypunct::frac_digits.md)|可返回一个在任何小数点右侧显示的位数计数。|  
|[分组](../Topic/moneypunct::grouping.md)|返回用于确定位数如何分组到任何小数点左边的区域设置特定规则。|  
|[neg\_format](../Topic/moneypunct::neg_format.md)|返回一个区域设置特定规则，用于对包含负数的输出结果进行格式化。|  
|[negative\_sign](../Topic/moneypunct::negative_sign.md)|返回要用作负号符号的区域设置特定元素序列。|  
|[pos\_format](../Topic/moneypunct::pos_format.md)|返回一个区域设置特定规则，用于对包含正数的输出结果进行格式化。|  
|[positive\_sign](../Topic/moneypunct::positive_sign.md)|返回要用作正号符号的区域设置特定元素序列。|  
|[thousands\_sep](../Topic/moneypunct::thousands_sep.md)|返回要用作千位分隔符号的区域设置特定元素序列。|  
  
## 要求  
 **标头：**\<locale\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<locale\>](../standard-library/locale.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)