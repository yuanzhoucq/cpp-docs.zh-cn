---
title: "CAtlFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAtlFile"
  - "ATL::CAtlFile"
  - "ATL.CAtlFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlFile class"
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CAtlFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类文件中处理API的Windows周围提供一个瘦包装。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CAtlFile : public CHandle  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAtlFile::CAtlFile](../Topic/CAtlFile::CAtlFile.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAtlFile::Create](../Topic/CAtlFile::Create.md)|调用此方法创建或打开文件。|  
|[CAtlFile::Flush](../Topic/CAtlFile::Flush.md)|调用此方法清除文件的缓冲区并使所有缓冲区的数据写入文件。|  
|[CAtlFile::GetOverlappedResult](../Topic/CAtlFile::GetOverlappedResult.md)|调用此方法捕获重叠的操作的结果在文件中。|  
|[CAtlFile::GetPosition](../Topic/CAtlFile::GetPosition.md)|调用此方法获取当前文件指针位置从文件。|  
|[CAtlFile::GetSize](../Topic/CAtlFile::GetSize.md)|调用此方法获取范围在文件的字节。|  
|[CAtlFile::LockRange](../Topic/CAtlFile::LockRange.md)|调用此方法锁定文件中的一个区域阻止其他从访问进行处理。|  
|[CAtlFile::Read](../Topic/CAtlFile::Read.md)|调用此方法读取数据从启动在该位置的文件由文件指针。|  
|[CAtlFile::Seek](../Topic/CAtlFile::Seek.md)|调用此方法移动文件的指针。|  
|[CAtlFile::SetSize](../Topic/CAtlFile::SetSize.md)|调用此方法设置文件的大小。|  
|[CAtlFile::UnlockRange](../Topic/CAtlFile::UnlockRange.md)|调用此方法以打开文件的区域。|  
|[CAtlFile::Write](../Topic/CAtlFile::Write.md)|调用此方法将数据写入启动在该位置的文件由文件指针。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAtlFile::m\_pTM](../Topic/CAtlFile::m_pTM.md)|为 `CAtlTransactionManager` 对象的指针|  
  
## 备注  
 比Windows API提供需要使用此选件类文件时，在处理需要时是相对简单，但是，更多抽象，而不包括MFC依赖项。  
  
## 继承层次结构  
 [CHandle](../../atl/reference/chandle-class.md)  
  
 `CAtlFile`  
  
## 要求  
 **Header:** atlfile.h  
  
## 请参阅  
 [marquee示例](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CHandle Class](../../atl/reference/chandle-class.md)