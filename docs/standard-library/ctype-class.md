---
title: "ctype 类 | Microsoft Docs"
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
  - "ctype"
  - "std::ctype"
  - "std.ctype"
  - "CType"
  - "xlocale/std::ctype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ctype 类"
ms.assetid: 3627154c-49d9-47b5-b28f-5bbedee38e3b
caps.latest.revision: 19
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ctype 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一种提供一个 facet 的类，此 facet 用于对字符进行分类、转换大写和小写以及在本机字符集与区域设置使用的字符集之间进行转换。  
  
## 语法  
  
```  
template <class CharType>  
   class ctype : public ctype_base;  
```  
  
#### 参数  
 `CharType`  
 在程序中用于对字符进行编码的类型。  
  
## 备注  
 对于任何区域设置 facet，静态对象 ID 的初始存储值为零。  首次尝试访问其存储值后，将在 **id** 中存储唯一正值。对基类 ctype\_base 中的嵌套位掩码类型提供了分类条件。  
  
 标准 C\+\+ 库定义了此模板类的两个显式专用化：  
  
-   [ctype](#vclrf_locale_ctype_class)\<`char`\>，此显式专用化的不同之处将单独说明。  
  
-   **ctype**\<`wchar_t`\>，将元素视为宽字符。  
  
 模板类 **ctype**\<**CharType**\> 的其他专用化：  
  
-   使用表达式 \(`char`\)**ch** 将 **CharType** 类型的值 ***ch*** 转换为 `char` 类型的值。  
  
-   使用表达式 **CharType** \(**byte**\) 将 `char` 类型的值 ***byte*** 转换为 **CharType** 类型的值。  
  
 对 `char` 值执行所有其他操作的方式与显式专用化 **ctype**\<`char`\> 相同。  
  
### 构造函数  
  
|||  
|-|-|  
|[ctype](../Topic/ctype::ctype.md)|`ctype` 类对象的构造函数，该类可用作字符的区域设置 facet。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/ctype::char_type.md)|一种类型，此类型描述区域设置使用的字符。|  
  
### 成员函数  
  
|||  
|-|-|  
|[do\_is](../Topic/ctype::do_is.md)|一种虚拟函数，通过调用此函数可测试单个字符是否具有特定属性，或者为某个范围内的每个字符的属性进行分类并将属性存储在数组中。|  
|[do\_narrow](../Topic/ctype::do_narrow.md)|一种虚拟函数，通过调用此函数可将区域设置使用的 `CharType` 类型的字符转换为本机字符集中 `char` 类型的相应字符。|  
|[do\_scan\_is](../Topic/ctype::do_scan_is.md)|一种虚拟函数，通过调用此函数可查找某个范围内与指定掩码匹配的第一个字符。|  
|[do\_scan\_not](../Topic/ctype::do_scan_not.md)|一种虚拟函数，通过调用此函数可查找某个范围内与指定掩码不匹配的第一个字符。|  
|[do\_tolower](../Topic/ctype::do_tolower.md)|一种虚拟函数，通过调用此函数可将一个字符或一系列字符转换为小写。|  
|[do\_toupper](../Topic/ctype::do_toupper.md)|一种虚拟函数，通过调用此函数可将一个字符或一系列字符转换为大写。|  
|[do\_widen](../Topic/ctype::do_widen.md)|一种虚拟函数，通过调用此函数可将本机字符集中 `char` 类型的字符转换为区域设置使用的 `CharType` 类型的相应字符。|  
|[is](../Topic/ctype::is.md)|测试单个字符是否具有特定属性，或者对某个范围内的每个字符的属性进行分类并将属性存储在数组中。|  
|[narrow](../Topic/ctype::narrow.md)|将区域设置使用的 `CharType` 类型的字符转换为本机字符集中 char 类型的相应字符。|  
|[scan\_is](../Topic/ctype::scan_is.md)|查找某个范围内与指定掩码匹配的第一个字符。|  
|[scan\_not](../Topic/ctype::scan_not.md)|查找某个范围内与指定掩码不匹配的第一个字符。|  
|[tolower](../Topic/ctype::tolower.md)|将一个或一些列字符转换为小写。|  
|[toupper](../Topic/ctype::toupper.md)|将一个或一些列字符转换为大写。|  
|[widen](../Topic/ctype::widen.md)|将本机字符集中 `char` 类型的字符转换为区域设置使用的 `CharType` 类型的相应字符。|  
  
## 要求  
 **标头：**\<locale\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<locale\>](../standard-library/locale.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)