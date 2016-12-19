---
title: "CComBSTR 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComBSTR"
  - "CComBSTR"
  - "ATL.CComBSTR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BSTR, 包装"
  - "CComBSTR"
  - "CComBSTR 类"
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComBSTR 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类是 `BSTR`的s.包装。  
  
## 语法  
  
```  
  
class CComBSTR  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComBSTR::CComBSTR](../Topic/CComBSTR::CComBSTR.md)|构造函数。|  
|[CComBSTR::~CComBSTR](../Topic/CComBSTR::~CComBSTR.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComBSTR::Append](../Topic/CComBSTR::Append.md)|追加字符串。`m_str`。|  
|[CComBSTR::AppendBSTR](../Topic/CComBSTR::AppendBSTR.md)|追加 `BSTR` 到 `m_str`。|  
|[CComBSTR::AppendBytes](../Topic/CComBSTR::AppendBytes.md)|追加指定的字节数。`m_str`。|  
|[CComBSTR::ArrayToBSTR](../Topic/CComBSTR::ArrayToBSTR.md)|在safearray创建从每个元素第一个字符的 `BSTR` 并将它附加到 `CComBSTR` 对象。|  
|[CComBSTR::AssignBSTR](../Topic/CComBSTR::AssignBSTR.md)|分配 `BSTR` 到 `m_str`。|  
|[CComBSTR::Attach](../Topic/CComBSTR::Attach.md)|附加 `BSTR` 到 `CComBSTR` 对象。|  
|[CComBSTR::BSTRToArray](../Topic/CComBSTR::BSTRToArray.md)|创建一个从零开始的一维safearray，其中数组的每个元素是从 `CComBSTR` 对象的一个字符。|  
|[CComBSTR::ByteLength](../Topic/CComBSTR::ByteLength.md)|在字节返回 `m_str` 的长度。|  
|[CComBSTR::Copy](../Topic/CComBSTR::Copy.md)|返回 `m_str`的副本。|  
|[CComBSTR::CopyTo](../Topic/CComBSTR::CopyTo.md)|通过 **\[out\]** 参数返回 `m_str` 的副本|  
|[CComBSTR::Detach](../Topic/CComBSTR::Detach.md)|分离 `CComBSTR` 对象的 `m_str`。|  
|[CComBSTR::Empty](../Topic/CComBSTR::Empty.md)|释放 `m_str`。|  
|[CComBSTR::Length](../Topic/CComBSTR::Length.md)|返回 `m_str`的长度。|  
|[CComBSTR::LoadString](../Topic/CComBSTR::LoadString.md)|加载一字符串资源。|  
|[CComBSTR::ReadFromStream](../Topic/CComBSTR::ReadFromStream.md)|从流加载一 `BSTR` 对象。|  
|[CComBSTR::ToLower](../Topic/CComBSTR::ToLower.md)|将字符串转换为小写。|  
|[CComBSTR::ToUpper](../Topic/CComBSTR::ToUpper.md)|将字符串转换为大写。|  
|[CComBSTR::WriteToStream](../Topic/CComBSTR::WriteToStream.md)|保存 `m_str` 入流。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CComBSTR::operator BSTR](../Topic/CComBSTR::operator%20BSTR.md)|转换为 `BSTR`的一 `CComBSTR` 对象。|  
|[CComBSTR::operator \!](../Topic/CComBSTR::operator%20!.md)|返回 `true` 或 `false`，根据 `m_str`是否 `NULL`。|  
|[CComBSTR::operator \!\=](../Topic/CComBSTR::operator%20!=.md)|`CComBSTR` 的字符串比较。|  
|[CComBSTR::operator &](../Topic/CComBSTR::operator%20&.md)|返回 `m_str`地址。|  
|[CComBSTR::operator \+\=](../Topic/CComBSTR::operator%20+=.md)|追加 `CComBSTR` 为对象。|  
|[CComBSTR::operator \<](../Topic/CComBSTR::operator%20%3C.md)|`CComBSTR` 的字符串比较。|  
|[CComBSTR::operator \=](../Topic/CComBSTR::operator%20=.md)|赋值。`m_str`。|  
|[CComBSTR::operator \=\=](../Topic/CComBSTR::operator%20==.md)|`CComBSTR` 的字符串比较。|  
|[CComBSTR::operator \>](../Topic/CComBSTR::operator%20%3E.md)|`CComBSTR` 的字符串比较。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComBSTR::m\_str](../Topic/CComBSTR::m_str.md)|包含 `BSTR` 与 `CComBSTR` 对象。|  
  
## 备注  
 `CComBSTR` 选件类是 `BSTR`的包装，长度为前缀的字符串。  该长度存储为上面数据的内存位置的整数。该字符串。  
  
 最后，在计数的字符，但也可以包含在字符串中后，嵌入null字符 [BSTR](http://msdn.microsoft.com/zh-cn/1b2d7d2c-47af-4389-a6b6-b01b7e915228) Null终止。  字符数不依赖于字符串长度，不带第一个null字符。  
  
> [!NOTE]
>  `CComBSTR` 选件类提供大量该名称的成员\(构造函数、赋值运算符和比较运算符\)若要拍摄ANSI或Unicode字符串作为参数。  因为临时Unicode字符串在内部，通常为这些功能创建ANSI版本比其Unicode重复效率低。  为提高效率，尽可能使用Unicode版本。  
  
> [!NOTE]
>  由于Visual Studio实现改进的查找行为.NET，应实现代码\(如 `bstr = L"String2" + bstr;`，以前的版本可能生成的，作为 `bstr = CStringW(L"String2") + bstr`。  
  
 有关小心列表，在使用 `CComBSTR`中，请参见 [编程时CComBSTR](../../atl/programming-with-ccombstr-atl.md)。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)   
 [ATL and MFC String Conversion Macros](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)