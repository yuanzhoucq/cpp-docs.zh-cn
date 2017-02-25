---
title: "CFixedStringT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFixedStringT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFixedStringT class"
  - "shared classes, CFixedStringT"
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CFixedStringT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类将使用内置的字符缓冲区表示字符串对象。  
  
## 语法  
  
```  
  
      template< class   
      StringType  
      , int   
      t_nChars  
       >    
class CFixedStringT : private CFixedStringMgr, public StringType  
```  
  
#### 参数  
 `StringType`  
 使用，基类提供的内置的字符串对象，并且可以所有 `CStringT`基于类型。  一些示例包括 `CString`、 `CStringA`和 `CStringW`。  
  
 *t\_nChars*  
 缓冲区中的字符数。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CFixedStringT::CFixedStringT](../Topic/CFixedStringT::CFixedStringT.md)|字符串对象的构造函数。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CFixedStringT::operator \=](../Topic/CFixedStringT::operator%20=.md)|赋新值。`CFixedStringT` 对象。|  
  
## 备注  
 此选件类是基于 `CStringT`的自定义字符串选件类的示例。  虽然相当类似，两选件类的实现方式不同。  `CFixedStringT` 和 `CStringT` 之间的主要差异是:  
  
-   初始字符缓冲区指定为对象的一部分且具有范围 *t\_nChars*。  这允许 **CFixedString** 对象占用性能目的连续内存块。  但是，因此，如果 `CFixedStringT` 对象的内容。*t\_nChars外*增大，动态分配缓冲区。  
  
-   `CFixedStringT` 对象的字符缓冲区始终是相同长度\(*t\_nChars*）。  不在缓冲区大小限制 `CStringT` 对象的。  
  
-   `CFixedStringT` 的内存管理器自定义以便共享两个或多个之间的一 [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) 对象不允许的 `CFixedStringT` objectsis。  `CStringT` 对象没有此限制。  
  
 有关 `CFixedStringT` 和内存管理的自定义项的更多信息字符串对象的一般，请参见 [内存管理和CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## 继承层次结构  
 `IAtlStringMgr`  
  
 `StringType`  
  
 `CFixedStringMgr`  
  
 `CFixedStringT`  
  
## 要求  
 **Header:** cstringt.h  
  
## 请参阅  
 [CStringT Class](../../atl-mfc-shared/reference/cstringt-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)