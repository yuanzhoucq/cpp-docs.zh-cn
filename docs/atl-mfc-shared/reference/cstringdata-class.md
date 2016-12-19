---
title: "CStringData Class | Microsoft Docs"
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
  - "CStringData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringData class"
  - "shared classes, CStringData"
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
caps.latest.revision: 16
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStringData Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类表示字符串对象的数据。  
  
## 语法  
  
```  
  
struct CStringData  
  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[AddRef](../Topic/CStringData::AddRef.md)|增加字符串数据对象的引用计数。|  
|[data](../Topic/CStringData::data.md)|检索字符串对象的字符数据。|  
|[IsLocked](../Topic/CStringData::IsLocked.md)|确定关联的字符串对象的缓冲区是否锁定。|  
|[IsShared](../Topic/CStringData::IsShared.md)|确定关联的字符串对象的缓冲区当前是否共享。|  
|[锁定](../Topic/CStringData::Lock.md)|锁关联的字符串对象的缓冲区。|  
|[Release](../Topic/CStringData::Release.md)|释放指定字符串对象。|  
|[unlock](../Topic/CStringData::Unlock.md)|打开关联的字符串对象的缓冲区。|  
  
### 数据成员  
  
|||  
|-|-|  
|[nAllocLength](../Topic/CStringData::nAllocLength.md)|分配的数据的长度。`XCHAR`中的\(不包括终止null\)|  
|[nDataLength](../Topic/CStringData::nDataLength.md)|在 `XCHAR`中的当前使用的数据的长度\(不包括终止null\)|  
|[nRefs](../Topic/CStringData::nRefs.md)|当前对对象的引用计数。|  
|[pStringMgr](../Topic/CStringData::pStringMgr.md)|此字符串对象的字符串管理器的指针。|  
  
## 备注  
 应由实现自定义字符串管理器的开发人员只使用此选件类。  有关自定义字符串管理器的更多信息，请参见 [内存管理和CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)  
  
 此选件类封装信息和的各种数据类型与了更高的字符串对象，例如 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)、 [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)或 [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) 对象。  每更高的字符串对象包含指向其关联的 `CStringData` 对象，允许多个字符串对象指向同一字符串数据对象。  此关系由引用计数\(`nRefs`\)表示 `CStringData` 对象。  
  
> [!NOTE]
>  在某些情况下，字符串类型\(例如 **CFixedString**\)使用多个更高的字符串对象不会共享字符串数据对象。  有关这方面的更多信息，请参见 [内存管理和CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
 此数据组成:  
  
-   内存管理器的类型\( [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)\)的字符串。  
  
-   当前长度\([nDataLength](../Topic/CStringData::nDataLength.md)\)的字符串。  
  
-   分配的长度\([nAllocLength](../Topic/CStringData::nAllocLength.md)\)的字符串。  出于性能原因，这可能与当前字符串的长度不同  
  
-   当前引用计数\([nRefs](../Topic/CStringData::nRefs.md)\) `CStringData` 对象。  此值用于确定了字符串对象共享同一 `CStringData` 对象。  
  
-   实际字符缓冲区\([数据](../Topic/CStringData::data.md)\)字符串。  
  
    > [!NOTE]
    >  字符串管理器将字符串对象实际字符缓冲区和追加到 `CStringData` 对象。  
  
## 要求  
 **Header:** atlsimpstr.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)