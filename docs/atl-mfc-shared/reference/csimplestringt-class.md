---
title: "CSimpleStringT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CSimpleStringT"
  - "ATL::CSimpleStringT"
  - "ATL::CSimpleStringT<BaseType>"
  - "ATL.CSimpleStringT<BaseType>"
  - "CSimpleStringT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleStringT class"
  - "shared classes, CSimpleStringT"
  - "字符串 [C++], ATL 类"
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CSimpleStringT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类表示 `CSimpleStringT` 对象。  
  
## 语法  
  
```  
  
      template <typename   
      BaseType  
      >  
class CSimpleStringT  
```  
  
#### 参数  
 `BaseType`  
 字符串选件类的字符类型。  可以是如下内容之一：  
  
-   `char` \(对于ANSI字符字符串\)。  
  
-   `wchar_t` \(对于Unicode字符串\)。  
  
-   **TCHAR** \(对于ANSI和Unicode字符串\)。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|描述|  
|--------|--------|  
|[CSimpleStringT::PCXSTR](../Topic/CSimpleStringT::PCXSTR.md)|对常数字符串的指针。|  
|[CSimpleStringT::PXSTR](../Topic/CSimpleStringT::PXSTR.md)|为字符串的指针。|  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CSimpleStringT::CSimpleStringT](../Topic/CSimpleStringT::CSimpleStringT.md)|构造 `CSimpleStringT` 对象以多种方式。|  
|[CSimpleStringT::~CSimpleStringT](../Topic/CSimpleStringT::~CSimpleStringT.md)|析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CSimpleStringT::Append](../Topic/CSimpleStringT::Append.md)|追加到现有 `CSimpleStringT` 对象的一 `CSimpleStringT` 对象。|  
|[CSimpleStringT::AppendChar](../Topic/CSimpleStringT::AppendChar.md)|将字符追加到现有 `CSimpleStringT` 对象。|  
|[CSimpleStringT::CopyChars](../Topic/CSimpleStringT::CopyChars.md)|将一个或多个字符到另一个字符串。|  
|[CSimpleStringT::CopyCharsOverlapped](../Topic/CSimpleStringT::CopyCharsOverlapped.md)|将一个或多个字符对缓冲区重叠的另一个字符串。|  
|[CSimpleStringT::Empty](../Topic/CSimpleStringT::Empty.md)|强制字符串零长度。|  
|[CSimpleStringT::FreeExtra](../Topic/CSimpleStringT::FreeExtra.md)|释放字符串对象以前指定的任何多余的内存。|  
|[CSimpleStringT::GetAllocLength](../Topic/CSimpleStringT::GetAllocLength.md)|检索 `CSimpleStringT` 对象分配的长度。|  
|[CSimpleStringT::GetAt](../Topic/CSimpleStringT::GetAt.md)|返回字符在特定位置。|  
|[CSimpleStringT::GetBuffer](../Topic/CSimpleStringT::GetBuffer.md)|返回指向在 `CSimpleStringT`的字符。|  
|[CSimpleStringT::GetBufferSetLength](../Topic/CSimpleStringT::GetBufferSetLength.md)|返回指向在 `CSimpleStringT`的字符，截断为指定长度的。|  
|[CSimpleStringT::GetLength](../Topic/CSimpleStringT::GetLength.md)|返回字符数。`CSimpleStringT` 对象的。|  
|[CSimpleStringT::GetManager](../Topic/CSimpleStringT::GetManager.md)|检索 `CSimpleStringT` 对象的内存管理器。|  
|[CSimpleStringT::GetString](../Topic/CSimpleStringT::GetString.md)|检索字符串。|  
|[CSimpleStringT::IsEmpty](../Topic/CSimpleStringT::IsEmpty.md)|测试 `CSimpleStringT` 对象是否不包含字符。|  
|[CSimpleStringT::LockBuffer](../Topic/CSimpleStringT::LockBuffer.md)|禁用引用计数并防止在缓冲区的字符串。|  
|[CSimpleStringT::Preallocate](../Topic/CSimpleStringT::Preallocate.md)|分配字符缓冲区的特定量的内存。|  
|[CSimpleStringT::ReleaseBuffer](../Topic/CSimpleStringT::ReleaseBuffer.md)|缓冲区的释放控件由 `GetBuffer`返回。|  
|[CSimpleStringT::ReleaseBufferSetLength](../Topic/CSimpleStringT::ReleaseBufferSetLength.md)|缓冲区的释放控件由 `GetBuffer`返回。|  
|[CSimpleStringT::SetAt](../Topic/CSimpleStringT::SetAt.md)|字符集在特定位置。|  
|[CSimpleStringT::SetManager](../Topic/CSimpleStringT::SetManager.md)|设置 `CSimpleStringT` 对象的内存管理器。|  
|[CSimpleStringT::SetString](../Topic/CSimpleStringT::SetString.md)|设置 `CSimpleStringT` 对象的字符串。|  
|[CSimpleStringT::StringLength](../Topic/CSimpleStringT::StringLength.md)|返回字符数在指定字符串的。|  
|[CSimpleStringT::Truncate](../Topic/CSimpleStringT::Truncate.md)|截断该字符串使其达到指定的长度。|  
|[CSimpleStringT::UnlockBuffer](../Topic/CSimpleStringT::UnlockBuffer.md)|启用引用计数和版本缓冲区的字符串。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[CSimpleStringT::operator PCXSTR](../Topic/CSimpleStringT::operator%20PCXSTR.md)|在 `CSimpleStringT` 对象存储的直接访问字符.作为c样式字符串。|  
|[CSimpleStringT::operator](../Topic/CSimpleStringT::operator.md)|返回字符在特定位置— `GetAt`的运算符替换。|  
|[CSimpleStringT::operator \+\=](../Topic/CSimpleStringT::operator%20+=.md)|连接一个新字符串为现有字符串的末尾。|  
|[CSimpleStringT::operator \=](../Topic/CSimpleStringT::operator%20=.md)|赋新值。`CSimpleStringT` 对象。|  
  
## 备注  
 `CSimpleStringT` 是Visual C\+\+支持的各个字符串选件类的基类。  它提供最小为字符串对象和基本的缓冲区处理的内存管理支持。  有关更高级的字符串对象，请参见 [CStringT选件类](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
## 要求  
 **Header:** atlsimpstr.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)