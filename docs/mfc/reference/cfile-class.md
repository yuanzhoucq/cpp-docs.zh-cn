---
title: "CFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchive class, using with CFile"
  - "CFile class"
  - "文件 [C++], classes for"
ms.assetid: b2eb5757-d499-4e67-b044-dd7d1abaa0f8
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft基础选件类文件的基类。  
  
## 语法  
  
```  
class CFile : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CFile::CFile](../Topic/CFile::CFile.md)|构造一个路径或文件句柄的一 `CFile` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CFile::Abort](../Topic/CFile::Abort.md)|关闭忽略任何警告和错误的文件。|  
|[CFile::Close](../Topic/CFile::Close.md)|关闭文件和删除对象。|  
|[CFile::Duplicate](../Topic/CFile::Duplicate.md)|构造基于此文件的重复的对象。|  
|[CFile::Flush](../Topic/CFile::Flush.md)|对于要写入的所有数据。|  
|[CFile::GetFileName](../Topic/CFile::GetFileName.md)|检索所选文件的文件名。|  
|[CFile::GetFilePath](../Topic/CFile::GetFilePath.md)|检索所选文件的完整文件路径。|  
|[CFile::GetFileTitle](../Topic/CFile::GetFileTitle.md)|检索所选文件的标题。|  
|[CFile::GetLength](../Topic/CFile::GetLength.md)|检索文件的长度。|  
|[CFile::GetPosition](../Topic/CFile::GetPosition.md)|检索当前文件指针。|  
|[CFile::GetStatus](../Topic/CFile::GetStatus.md)|检索打开文件的状态，或在静态版本，检索指定的文件\(静态，虚函数\)的状态。|  
|[CFile::LockRange](../Topic/CFile::LockRange.md)|锁定字节的范围在文件中。|  
|[CFile::Open](../Topic/CFile::Open.md)|安全打开包含一个错误测试的选项的文件。|  
|[CFile::Read](../Topic/CFile::Read.md)|读取\(无缓冲区的\)数据从文件在当前文件的位置。|  
|[CFile::Remove](../Topic/CFile::Remove.md)|删除指定的文件\(静态函数）。|  
|[CFile::Rename](../Topic/CFile::Rename.md)|对指定的文件\(静态函数\)重命名为。|  
|[CFile::Seek](../Topic/CFile::Seek.md)|确定当前文件指针。|  
|[CFile::SeekToBegin](../Topic/CFile::SeekToBegin.md)|在文件开头确定当前文件指针。|  
|[CFile::SeekToEnd](../Topic/CFile::SeekToEnd.md)|确定当前文件指针在文件末尾。|  
|[CFile::SetFilePath](../Topic/CFile::SetFilePath.md)|将所选文件的完整文件路径。|  
|[CFile::SetLength](../Topic/CFile::SetLength.md)|更改文件的长度。|  
|[CFile::SetStatus](../Topic/CFile::SetStatus.md)|设置中指定的文件\(静态，虚函数\)的状态。|  
|[CFile::UnlockRange](../Topic/CFile::UnlockRange.md)|打开字节的范围在文件中。|  
|[CFile::Write](../Topic/CFile::Write.md)|在一个文件的写\(无缓冲区的\)数据到当前文档位置。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CFile::operator HANDLE](../Topic/CFile::operator%20HANDLE.md)|为 `CFile` 对象的句柄。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CFile::hFileNull](../Topic/CFile::hFileNull.md)|确定 `CFile` 对象是否具有有效句柄。|  
|[CFile::m\_hFile](../Topic/CFile::m_hFile.md)|通常包含操作系统的文件句柄。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CFile::m\_pTM](../Topic/CFile::m_pTM.md)|为 `CAtlTransactionManager` 对象的指针。|  
  
## 备注  
 它直接提供无缓冲区，二进制磁盘输入\/输出服务，因此，它通过其派生类间接支持文本文件和内存文件。  `CFile` 与 `CArchive` 选件类共同支持Microsoft基础选件类对象的序列化。  
  
 此选件类及其派生类之间的分层关系使您的程序通过多态 `CFile` 接口来操作任何文件对象。  内存文件，例如，其行为类似于磁盘文件。  
  
 有关常规磁盘I\/O使用 `CFile` 及其派生类。  为格式化文本使用 `ofstream` 或其他Microsoft iostream选件类发送到磁盘文件。  
  
 通常，磁盘文件在 `CFile` 构造在损坏将自动打开和关闭。  静态成员函数可以询问文件的状态，而不必打开文件。  
  
 有关使用 `CFile`的更多信息，请参见文章[MFC 中的文件](../../mfc/files-in-mfc.md) 和 *运行库参考*中的 [文件处理](../../c-runtime-library/file-handling.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CFile`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [MFC示例DRAWCLI](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CStdioFile Class](../../mfc/reference/cstdiofile-class.md)   
 [CMemFile Class](../../mfc/reference/cmemfile-class.md)   
 [如何:我使用C文件选件类?](http://go.microsoft.com/fwlink/?LinkId=128046)