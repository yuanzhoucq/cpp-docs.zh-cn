---
title: "CMemFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMemFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMemFile class"
  - "memory files"
  - "temporary files, memory files"
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CMemFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[C文件](../../mfc/reference/cfile-class.md)\-支持内存文件的派生类。  
  
## 语法  
  
```  
class CMemFile : public CFile  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMemFile::CMemFile](../Topic/CMemFile::CMemFile.md)|构造内存文件对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMemFile::Attach](../Topic/CMemFile::Attach.md)|附加内存块。`CMemFile`。|  
|[CMemFile::Detach](../Topic/CMemFile::Detach.md)|分离内存块从 `CMemFile` 并返回指向分离的内存块。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMemFile::Alloc](../Topic/CMemFile::Alloc.md)|修改内存分配行为的重写。|  
|[CMemFile::Free](../Topic/CMemFile::Free.md)|修改内存释放行为的重写。|  
|[CMemFile::GrowFile](../Topic/CMemFile::GrowFile.md)|修改行为的重写，当存在文件时。|  
|[CMemFile::Memcpy](../Topic/CMemFile::Memcpy.md)|修改内存中复本行为的重写，在读取和写入文件时。|  
|[CMemFile::Realloc](../Topic/CMemFile::Realloc.md)|修改内存重新分配行为的重写。|  
  
## 备注  
 这些内存文件的行为与磁盘文件，排除文件在RAM中而不是磁盘。  内存文件进行快速临时存储非常有用的或对调用原始的字节或序列化的对象处于独立进程。  
  
 `CMemFile` 对象可以自动将其分配的内存或可以附加到的内存块向 `CMemFile` 对象是通过调用 [附加](../Topic/CMemFile::Attach.md)。  在任一情况下，因此，如果 `nGrowBytes` 不为零，可能存在的内存文件中存在 `nGrowBytes`大小增加自动指派。  
  
 内存块将被自动删除在 `CMemFile` 对象析构 `CMemFile` 对象是否最初分配内存;否则，您负责释放程序附加到对象的内存。  
  
 您可以通过访问所提供的指针内存块，则通过调用 [分离](../Topic/CMemFile::Detach.md)分离它从 `CMemFile` 对象时。  
  
 最常见 `CMemFile` 是创建 `CMemFile` 对象并使用它通过调用 [C文件](../../mfc/reference/cfile-class.md) 成员函数。  请注意创建 `CMemFile` 的，自动将其打开:您不调用 [CFile::Open](../Topic/CFile::Open.md)，对于磁盘文件只使用。  由于 `CMemFile` 不使用一个磁盘文件，不使用数据成员 `CFile::m_hFile` 并没有意义。  
  
 `CFile` 成员函数 [重复](../Topic/CFile::Duplicate.md)、 [LockRange](../Topic/CFile::LockRange.md)和 [UnlockRange](../Topic/CFile::UnlockRange.md) 没有为 `CMemFile`实现。  如果对 `CMemFile` 对象的这些功能，您将收到 [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 `CMemFile` 使用运行库函数 [malloc](../../c-runtime-library/reference/malloc.md)、 [realloc](../../c-runtime-library/reference/realloc.md)和 [免](../../c-runtime-library/reference/free.md) 分配，分配和释放内存;和内部块复制内存的 [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)，在读取和写入时。  如果要更改此行为或该行为，当 `CMemFile` 其文件时，从 `CMemFile` 派生您的选件类并重写相应的功能。  
  
 有关 `CMemFile` 的更多信息，请参见文章 [Files in MFC](../../mfc/files-in-mfc.md) 和 [内存管理 \(MFC\)](../../mfc/memory-management.md) 并查看 *运行库参考* 中的 [文件处理](../../c-runtime-library/file-handling.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C文件](../../mfc/reference/cfile-class.md)  
  
 `CMemFile`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)