---
title: "wstring_convert 类 | Microsoft Docs"
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
  - "cvt.wstring_convert"
  - "wstring_convert"
  - "stdext::cvt::wstring_convert"
  - "cvt::wstring_convert"
  - "wstring/stdext::cvt::wstring_convert"
  - "stdext.cvt.wstring_convert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "wstring_convert 类"
ms.assetid: e34f5b65-d572-4bdc-ac69-20778712e376
caps.latest.revision: 25
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wstring_convert 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模板类 `wstring_convert` 在宽字符串和字节字符串之间执行转换。  
  
## 语法  
  
```  
template<  
    class Codecvt,  
    class Elem = wchar_t  
>  
class wstring_convert  
```  
  
#### 参数  
 Codecvt  
 表示转换对象的[区域设置](../standard-library/locale-class.md)方面。  
  
 Elem  
 宽字符元素类型。  
  
## 备注  
 模板类描述一个对象，该对象用于控制类 `std::basic_string<Elem>` 的宽字符串对象和类 `std::basic_string<char>`（也称为 `std::string`）的字节字符串对象之间的转换。 模板类将类型 `wide_string` 和 `byte_string` 定义为这两种类型的同义词。 一个 `Elem` 值序列（存储在 `wide_string` 对象中）和多字节序列（存储在 `byte_string` 对象中）之间的转换由类 `Codecvt<Elem, char, std::mbstate_t>` 的对象执行，这符合标准代码转换方面 `std::codecvt<Elem, char, std::mbstate_t>` 的要求。  
  
 此模板类的对象存储：  
  
-   发生错误时显示的字节字符串  
  
-   发生错误时显示的宽字符串  
  
-   指向分配的转换对象（在销毁 wbuffer\_convert 对象时释放）的指针  
  
-   [state\_type](../Topic/wstring_convert::state_type.md) 类型的转换状态对象  
  
-   转换计数  
  
### 构造函数  
  
|||  
|-|-|  
|[wstring\_convert](../Topic/wstring_convert::wstring_convert.md)|构造 `wstring_convert` 类型的对象。|  
  
### Typedef  
  
|||  
|-|-|  
|[byte\_string](../Topic/wstring_convert::byte_string.md)|表示字节字符串的类型。|  
|[wide\_string](../Topic/wstring_convert::wide_string.md)|表示宽字符串的类型。|  
|[state\_type](../Topic/wstring_convert::state_type.md)|表示转换状态的类型。|  
|[int\_type](../Topic/wstring_convert::int_type.md)|表示整数的类型。|  
  
### 成员函数  
  
|||  
|-|-|  
|[from\_bytes](../Topic/wstring_convert::from_bytes.md)|将字节字符串转换为宽字符串。|  
|[to\_bytes](../Topic/wstring_convert::to_bytes.md)|将宽字符串转换为字节字符串。|  
|[已转换](../Topic/wstring_convert::converted.md)|返回成功转换数。|  
|[状态](../Topic/wstring_convert::state.md)|返回表示转换状态的对象。|  
  
## 要求  
 **标头：**\<locale\>  
  
 **命名空间:** std