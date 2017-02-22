---
title: "CInternetFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CInternetFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInternetFile class"
  - "Internet files"
  - "Internet files, CInternetFile class"
ms.assetid: 96935681-ee71-4a8d-9783-5abc7b3e6f10
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CInternetFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

允许访问文件的访问使用Internet协议的远程系统。  
  
## 语法  
  
```  
  
class CInternetFile : public CStdioFile  
  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CInternetFile::CInternetFile](../Topic/CInternetFile::CInternetFile.md)|构造 `CInternetFile` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CInternetFile::Abort](../Topic/CInternetFile::Abort.md)|关闭文件，忽略所有警告和错误。|  
|[CInternetFile::Close](../Topic/CInternetFile::Close.md)|关闭 `CInternetFile` 并释放其资源。|  
|[CInternetFile::Flush](../Topic/CInternetFile::Flush.md)|刷新写入缓冲区的内容并确保在内存中的数据对目标计算机编写。|  
|[CInternetFile::GetLength](../Topic/CInternetFile::GetLength.md)|返回文件的大小。|  
|[CInternetFile::Read](../Topic/CInternetFile::Read.md)|读取指定的字节的数目。|  
|[CInternetFile::ReadString](../Topic/CInternetFile::ReadString.md)|读取字符流。|  
|[CInternetFile::Seek](../Topic/CInternetFile::Seek.md)|重新定位在打开文件的指针。|  
|[CInternetFile::SetReadBufferSize](../Topic/CInternetFile::SetReadBufferSize.md)|设置数据将读取缓冲区的大小。|  
|[CInternetFile::SetWriteBufferSize](../Topic/CInternetFile::SetWriteBufferSize.md)|设置数据将写入缓冲区的大小。|  
|[CInternetFile::Write](../Topic/CInternetFile::Write.md)|写入指定的字节的数目。|  
|[CInternetFile::WriteString](../Topic/CInternetFile::WriteString.md)|写入文件的一个Null终止的字符串。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CInternetFile::operator HINTERNET](../Topic/CInternetFile::operator%20HINTERNET.md)|Internet处理的一个强制转换运算符。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CInternetFile::m\_hFile](../Topic/CInternetFile::m_hFile.md)|对文件的句柄。|  
  
## 备注  
 为 [CHttpFile](../../mfc/reference/chttpfile-class.md) 提供基类，并 [CGopherFile](../../mfc/reference/cgopherfile-class.md) 文件分类。  您从不直接创建一 `CInternetFile` 对象。  相反，通过调用 [CGopherConnection::OpenFile](../Topic/CGopherConnection::OpenFile.md) 或 [CHttpConnection::OpenRequest](../Topic/CHttpConnection::OpenRequest.md)创建对象其派生类之一。  通过调用 [CFtpConnection::OpenFile](../Topic/CFtpConnection::OpenFile.md)还创建 `CInternetFile` 对象。  
  
 `CInternetFile` 成员函数 **Open**、 `LockRange`、 `UnlockRange`和 `Duplicate` 没有为 `CInternetFile`实现。  如果对 `CInternetFile` 对象的这些功能，您将收到 [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 若要了解更多信息 `CInternetFile` 与其他MFC Internet选件类，请参见文章 [编程时WinInet的Internet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C文件](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 `CInternetFile`  
  
## 要求  
 **Header:** afxinet.h  
  
## 请参阅  
 [CStdioFile Class](../../mfc/reference/cstdiofile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)