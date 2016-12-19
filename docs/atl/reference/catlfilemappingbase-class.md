---
title: "CAtlFileMappingBase Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAtlFileMappingBase"
  - "ATL::CAtlFileMappingBase"
  - "CAtlFileMappingBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlFileMappingBase class"
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlFileMappingBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类表示一个内存映射文件。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CAtlFileMappingBase  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAtlFileMappingBase::CAtlFileMappingBase](../Topic/CAtlFileMappingBase::CAtlFileMappingBase.md)|构造函数。|  
|[CAtlFileMappingBase::~CAtlFileMappingBase](../Topic/CAtlFileMappingBase::~CAtlFileMappingBase.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAtlFileMappingBase::CopyFrom](../Topic/CAtlFileMappingBase::CopyFrom.md)|调用此方法从一个文件映射对象副本。|  
|[CAtlFileMappingBase::GetData](../Topic/CAtlFileMappingBase::GetData.md)|调用此方法获取一个文件映射对象的数据。|  
|[CAtlFileMappingBase::GetHandle](../Topic/CAtlFileMappingBase::GetHandle.md)|调用此方法返回文件句柄。|  
|[CAtlFileMappingBase::GetMappingSize](../Topic/CAtlFileMappingBase::GetMappingSize.md)|调用此方法获取一个文件映射对象的映射范围。|  
|[CAtlFileMappingBase::MapFile](../Topic/CAtlFileMappingBase::MapFile.md)|调用此方法将创建一个文件映射的对象。|  
|[CAtlFileMappingBase::MapSharedMem](../Topic/CAtlFileMappingBase::MapSharedMem.md)|调用此方法创建许可证所有对所有进程的文件映射对象。|  
|[CAtlFileMappingBase::OpenMapping](../Topic/CAtlFileMappingBase::OpenMapping.md)|调用此方法返回句柄映射文件的对象。|  
|[CAtlFileMappingBase::Unmap](../Topic/CAtlFileMappingBase::Unmap.md)|调用此方法取消一文件映射的对象。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CAtlFileMappingBase::operator \=](../Topic/CAtlFileMappingBase::operator%20=.md)|设置为另一个文件映射对象的当前文件映射的对象。|  
  
## 备注  
 文件是映射文件的目录与处理的虚拟地址空间的部分。  此选件类用于创建轻松地允许程序访问和共享数据的文件映射对象的方法。  
  
 有关更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [映射文件](http://msdn.microsoft.com/library/windows/desktop/aa366556)。  
  
## 要求  
 **Header:** atlfile.h  
  
## 请参阅  
 [CAtlFileMapping Class](../../atl/reference/catlfilemapping-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)