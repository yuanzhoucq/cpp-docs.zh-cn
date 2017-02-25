---
title: "CStrBufT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CStrBufT<TCharType>"
  - "ATL.CStrBufT"
  - "CStrBufT"
  - "ATL::CStrBufT"
  - "ATL.CStrBufT<TCharType>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStrBufT class"
  - "shared classes, CStrBufT"
  - "字符串 [C++], custom memory management"
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CStrBufT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类。`GetBuffer` 提供自动清理资源，并 `ReleaseBuffer` 在现有 `CStringT` 对象调用。  
  
## 语法  
  
```  
  
      template<  
   typename TCharType  
>  
class CStrBufT  
```  
  
#### 参数  
 *TCharType*  
 `CStrBufT` 选件类的字符类型。  可以是如下内容之一：  
  
-   `char` \(对于ANSI字符字符串\)  
  
-   `wchar_t` \(对于Unicode字符串\)  
  
-   **TCHAR** \(对于ANSI和Unicode字符串\)  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|`PCXSTR`|对常数字符串的指针。|  
|`PXSTR`|为字符串的指针。|  
|`StringType`|缓冲区将由此选件类模板的专用化操作的字符串类型。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CStrBufT::CStrBufT](../Topic/CStrBufT::CStrBufT.md)|字符串缓冲区对象的构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CStrBufT::SetLength](../Topic/CStrBufT::SetLength.md)|设置关联的字符串对象的字符缓冲区长度。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CStrBufT::operator PCXSTR](../Topic/CStrBufT::operator%20PCXSTR.md)|检索 **const** 指向关联的字符串对象的字符缓冲区。|  
|[CStrBufT::operator PXSTR](../Topic/CStrBufT::operator%20PXSTR.md)|检索指向关联的字符串对象的字符缓冲区。|  
  
### 公共常量  
  
|名称|说明|  
|--------|--------|  
|[CStrBufT::AUTO\_LENGTH](../Topic/CStrBufT::AUTO_LENGTH.md)|将自动确定该字符串的新长度在版本。|  
|[CStrBufT::SET\_LENGTH](../Topic/CStrBufT::SET_LENGTH.md)|设置字符串对象的长度。GetBuffer时间|  
  
## 备注  
 此选件类用作包装选件类用于替换调用 [GetBuffer](../Topic/CSimpleStringT::GetBuffer.md) 和 [ReleaseBuffer](../Topic/CSimpleStringT::ReleaseBuffer.md)或 [GetBufferSetLength](../Topic/CSimpleStringT::GetBufferSetLength.md) 和 `ReleaseBuffer`。  
  
 主设计为帮助器选件类，`CStrBufT` 如何在为开发人员提供了一种方便地与字符串对象的字符缓冲区一起使用，而不必担心或调用 `ReleaseBuffer`。  因为包装对象自然超出范围后异常或多个退出点的代码路径，这是可能的;导致其析构函数释放字符串资源。  
  
## 要求  
 **Header:** atlsimpstr.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)