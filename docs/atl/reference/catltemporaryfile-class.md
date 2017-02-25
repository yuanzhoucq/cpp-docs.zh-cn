---
title: "CAtlTemporaryFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAtlTemporaryFile"
  - "ATL.CAtlTemporaryFile"
  - "ATL::CAtlTemporaryFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlTemporaryFile class"
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CAtlTemporaryFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供对临时文件的创建和使用。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CAtlTemporaryFile  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CAtlTemporaryFile::CAtlTemporaryFile](../Topic/CAtlTemporaryFile::CAtlTemporaryFile.md)|构造函数。|  
|[CAtlTemporaryFile::~CAtlTemporaryFile](../Topic/CAtlTemporaryFile::~CAtlTemporaryFile.md)|该析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CAtlTemporaryFile::Close](../Topic/CAtlTemporaryFile::Close.md)|调用此方法关闭临时文件和删除其内容或将其存储在指定的文件名下。|  
|[CAtlTemporaryFile::Create](../Topic/CAtlTemporaryFile::Create.md)|调用此方法创建临时文件。|  
|[CAtlTemporaryFile::Flush](../Topic/CAtlTemporaryFile::Flush.md)|调用此方法强制保持在文件缓冲区的任何数据都将写入临时文件。|  
|[CAtlTemporaryFile::GetPosition](../Topic/CAtlTemporaryFile::GetPosition.md)|调用此方法获取当前文件指针位置。|  
|[CAtlTemporaryFile::GetSize](../Topic/CAtlTemporaryFile::GetSize.md)|调用此方法获取范围在临时文件的字节。|  
|[CAtlTemporaryFile::HandsOff](../Topic/CAtlTemporaryFile::HandsOff.md)|调用此方法分离 `CAtlTemporaryFile` 对象的文件。|  
|[CAtlTemporaryFile::HandsOn](../Topic/CAtlTemporaryFile::HandsOn.md)|调用此方法以打开一个现有的临时文件并确定指针在文件末尾。|  
|[CAtlTemporaryFile::LockRange](../Topic/CAtlTemporaryFile::LockRange.md)|调用此方法锁定文件中的一个区域阻止其他从访问进行处理。|  
|[CAtlTemporaryFile::Read](../Topic/CAtlTemporaryFile::Read.md)|调用此方法读取数据从启动在该位置的临时文件由文件指针。|  
|[CAtlTemporaryFile::Seek](../Topic/CAtlTemporaryFile::Seek.md)|调用此方法移动临时文件的指针。|  
|[CAtlTemporaryFile::SetSize](../Topic/CAtlTemporaryFile::SetSize.md)|调用此方法设置临时文件的大小。|  
|[CAtlTemporaryFile::TempFileName](../Topic/CAtlTemporaryFile::TempFileName.md)|调用此方法返回临时文件的名称。|  
|[CAtlTemporaryFile::UnlockRange](../Topic/CAtlTemporaryFile::UnlockRange.md)|调用此方法以打开临时文件的区域。|  
|[CAtlTemporaryFile::Write](../Topic/CAtlTemporaryFile::Write.md)|调用此方法将数据写入启动在该位置的临时文件由文件指针。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[CAtlTemporaryFile::operator HANDLE](../Topic/CAtlTemporaryFile::operator%20HANDLE.md)|将处理返回到临时文件。|  
  
## 备注  
 `CAtlTemporaryFile` 可以轻松地创建和使用临时文件。  文件名为，中打开，会自动关闭，并将其删除。  如果需要文件内容，该文件中关闭后，即可将它们保存到具有指定名称的新文件。  
  
## 要求  
 **Header:** atlfile.h  
  
## 示例  
 为 [CAtlTemporaryFile::CAtlTemporaryFile](../Topic/CAtlTemporaryFile::CAtlTemporaryFile.md)参见示例。  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)   
 [CAtlFile Class](../../atl/reference/catlfile-class.md)