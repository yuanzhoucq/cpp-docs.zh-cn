---
title: "CSharedFile Class | Microsoft Docs"
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
  - "CSharedFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSharedFile class"
  - "memory files"
  - "shared memory files"
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSharedFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CMemFile](../../mfc/reference/cmemfile-class.md)\-支持共享内存文件的派生类。  
  
## 语法  
  
```  
class CSharedFile : public CMemFile  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSharedFile::CSharedFile](../Topic/CSharedFile::CSharedFile.md)|构造 `CSharedFile` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSharedFile::Detach](../Topic/CSharedFile::Detach.md)|关闭共享内存文件并返回其处理内存块。|  
|[CSharedFile::SetHandle](../Topic/CSharedFile::SetHandle.md)|附加共享内存复制到内存块。|  
  
## 备注  
 内存文件的行为与磁盘文件，排除文件在RAM中而不是磁盘。  内存文件进行快速临时存储非常有用的或对调用原始的字节或序列化的对象处于独立进程。  
  
 共享内存文件从该内存的其他内存文件的区别其随 [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) Windows功能。  在全局分配的 `CSharedFile` 选件类存储数据存储区\(使用创建 **GlobalAlloc**\)，使用DDE、剪贴板，或其他OLE\/COM合并数据传输操作，使用 `IDataObject`，因此，该内存块可以共享，例如。  
  
 **GlobalAlloc** 返回 `HGLOBAL` 处理而不是指向内存，例如 [malloc](../../c-runtime-library/reference/malloc.md)返回的指针。  `HGLOBAL` 处理在某些应用程序可能需要。  例如，将数据放入剪贴板需要 `HGLOBAL` 处理。  
  
 请注意 `CSharedFile` 不使用内存映射文件，并且，如果数据无法直接在进程之间共享。  
  
 `CSharedFile` 对象可以自动将其分配的内存或可以附加到的内存块向 `CSharedFile` 对象是通过调用 [CSharedFile::SetHandle](../Topic/CSharedFile::SetHandle.md)。  在任一情况下，因此，如果 `nGrowBytes` 不为零，可能存在的内存文件中存在 `nGrowBytes`大小增加自动指派。  
  
 有关更多信息，请参见文章[MFC 中的文件](../../mfc/files-in-mfc.md) 和 *运行库参考* 中的 [文件处理](../../c-runtime-library/file-handling.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C文件](../../mfc/reference/cfile-class.md)  
  
 [CMemFile](../../mfc/reference/cmemfile-class.md)  
  
 `CSharedFile`  
  
## 要求  
 **Header:** afxadv.h  
  
## 请参阅  
 [CMemFile Class](../../mfc/reference/cmemfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMemFile Class](../../mfc/reference/cmemfile-class.md)   
 [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)   
 [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)   
 [GlobalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366590)