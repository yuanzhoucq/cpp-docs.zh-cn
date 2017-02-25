---
title: "CStdioFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStdioFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStdioFile class"
  - "I/O [MFC], stream"
  - "stream I/O"
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CStdioFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示c.运行时流文件标记为打开该运行时函数 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)。  
  
## 语法  
  
```  
class CStdioFile : public CFile  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CStdioFile::CStdioFile](../Topic/CStdioFile::CStdioFile.md)|构造一个路径或文件指针的一个 `CStdioFile` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CStdioFile::Open](../Topic/CStdioFile::Open.md)|已重载。  打开旨在用于默认 `CStdioFile` 构造函数的使用\(重写 [CFile::Open](../Topic/CFile::Open.md)）。|  
|[CStdioFile::ReadString](../Topic/CStdioFile::ReadString.md)|读取一行文本。|  
|[CStdioFile::Seek](../Topic/CStdioFile::Seek.md)|确定当前文件指针。|  
|[CStdioFile::WriteString](../Topic/CStdioFile::WriteString.md)|编写一行文本。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CStdioFile::m\_pStream](../Topic/CStdioFile::m_pStream.md)|包含指针到打开文件。|  
  
## 备注  
 流文件在文本模式\(默认值\)或二进制模式缓冲区并可以将其打开。  
  
 文本模式用于支持返回换行符提供特殊处理对。  当您编写一个换行符\(0x0A\)时将文本模式 `CStdioFile` 对象，该字节对\(0x0D，0x0A\)发送到文件。  当您读取时，该字节对\(0x0D，0x0A\)转换为单个0x0A字节。  
  
 [C文件](../../mfc/reference/cfile-class.md) 函数 [重复](../Topic/CFile::Duplicate.md)，[LockRange](../Topic/CFile::LockRange.md)，并且，[UnlockRange](../Topic/CFile::UnlockRange.md) 没有为 `CStdioFile`支持。  
  
 如果对 `CStdioFile`的这些功能，您将收到 [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 有关使用 `CStdioFile`的更多信息，请参见文章[MFC 中的文件](../../mfc/files-in-mfc.md) 和 *运行库参考* 中的 [文件处理](../../c-runtime-library/file-handling.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C文件](../../mfc/reference/cfile-class.md)  
  
 `CStdioFile`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [CFile::Duplicate](../Topic/CFile::Duplicate.md)   
 [CFile::LockRange](../Topic/CFile::LockRange.md)   
 [CFile::UnlockRange](../Topic/CFile::UnlockRange.md)   
 [CNotSupportedException Class](../../mfc/reference/cnotsupportedexception-class.md)   
 [如何:我使用C文件选件类?](http://go.microsoft.com/fwlink/?LinkId=128046)