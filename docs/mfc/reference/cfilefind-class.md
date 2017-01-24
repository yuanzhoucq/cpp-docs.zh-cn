---
title: "CFileFind Class | Microsoft Docs"
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
  - "CFileFind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFileFind class"
  - "文件 [C++], 查找"
  - "Internet files [C++], 查找"
  - "local files"
  - "local files, 搜索"
  - "URLs [C++], 搜索"
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
caps.latest.revision: 22
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFileFind Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

执行本地文件搜索和是 [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) 和 [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)的基类，执行Internet文件搜索。  
  
## 语法  
  
```  
class CFileFind : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CFileFind::CFileFind](../Topic/CFileFind::CFileFind.md)|构造 `CFileFind` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CFileFind::Close](../Topic/CFileFind::Close.md)|关闭搜索请求。|  
|[CFileFind::FindFile](../Topic/CFileFind::FindFile.md)|搜索一个目录一个指定的文件名。|  
|[CFileFind::FindNextFile](../Topic/CFileFind::FindNextFile.md)|继续以前的文件搜索调用 [FindFile](../Topic/CFileFind::FindFile.md)。|  
|[CFileFind::GetCreationTime](../Topic/CFileFind::GetCreationTime.md)|获取文件的创建时间。|  
|[CFileFind::GetFileName](../Topic/CFileFind::GetFileName.md)|获取名称，包括扩展，找到的文件|  
|[CFileFind::GetFilePath](../Topic/CFileFind::GetFilePath.md)|获取已找到文件的完整路径。|  
|[CFileFind::GetFileTitle](../Topic/CFileFind::GetFileTitle.md)|获取已找到文件的标题。  标题不包含扩展名。|  
|[CFileFind::GetFileURL](../Topic/CFileFind::GetFileURL.md)|获取URL，包括文件路径，则找到文件。|  
|[CFileFind::GetLastAccessTime](../Topic/CFileFind::GetLastAccessTime.md)|获取时文件上次访问时间。|  
|[CFileFind::GetLastWriteTime](../Topic/CFileFind::GetLastWriteTime.md)|获取上次更改并保存文件的时间。|  
|[CFileFind::GetLength](../Topic/CFileFind::GetLength.md)|获取已找到文件的长度，以字节为单位）。|  
|[CFileFind::GetRoot](../Topic/CFileFind::GetRoot.md)|获取已找到文件的根目录。|  
|[CFileFind::IsArchived](../Topic/CFileFind::IsArchived.md)|确定找到的文件是否存档。|  
|[CFileFind::IsCompressed](../Topic/CFileFind::IsCompressed.md)|确定找到的文件是否压缩。|  
|[CFileFind::IsDirectory](../Topic/CFileFind::IsDirectory.md)|确定找到的文件是否为内容。|  
|[CFileFind::IsDots](../Topic/CFileFind::IsDots.md)|确定找到的文件的名称是否具有名称“”。或者“。”，指示实际上是内容。|  
|[CFileFind::IsHidden](../Topic/CFileFind::IsHidden.md)|确定找到的文件是否为隐藏的。|  
|[CFileFind::IsNormal](../Topic/CFileFind::IsNormal.md)|确定找到的文件是否为的规则\(换言之，没有其他属性）。|  
|[CFileFind::IsReadOnly](../Topic/CFileFind::IsReadOnly.md)|确定找到的文件是否为只读。|  
|[CFileFind::IsSystem](../Topic/CFileFind::IsSystem.md)|确定找到的文件是否是系统文件。|  
|[CFileFind::IsTemporary](../Topic/CFileFind::IsTemporary.md)|确定找到的文件是否是瞬态的。|  
|[CFileFind::MatchesMask](../Topic/CFileFind::MatchesMask.md)|指示要找到文件的所需文件属性。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CFileFind::CloseContext](../Topic/CFileFind::CloseContext.md)|关闭当前搜索处理指定的文件。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CFileFind::m\_pTM](../Topic/CFileFind::m_pTM.md)|为 `CAtlTransactionManager` 对象的指针。|  
  
## 备注  
 `CFileFind` 包括开始搜索，查找文件，并返回文件的标题、名称或路径的成员函数。  对于Internet搜索，成员函数 [GetFileURL](../Topic/CFileFind::GetFileURL.md) 返回文件的URL。  
  
 `CFileFind` 是旨在的其他两MFC选件类的基类搜索特定服务器类型: `CGopherFileFind` 专门尤其是对于地鼠服务器和 `CFtpFileFind` 使用与FTP服务器协同。  同时，无论服务器协议、文件类型或位置，本地计算机或远程服务器，这三选件类为客户端提供一种无缝的结构，查找文件。  
  
 下面的代码将枚举在当前目录中的所有文件，打印每个文件的名称:  
  
 [!code-cpp[NVC_MFCFiles#31](../../mfc/codesnippet/CPP/cfilefind-class_1.cpp)]  
  
 若要使该示例简单，此代码使用标准C\+\+库 `cout` 选件类。  `cout` 行中用到 `CListBox::AddString`的调用替换，例如，在程序与图形用户界面。  
  
 有关如何使用 `CFileFind` 和其他WinInet选件类的更多信息，请参见文章 [编程时WinInet的Internet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CFileFind`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFtpFileFind Class](../../mfc/reference/cftpfilefind-class.md)   
 [CGopherFileFind Class](../../mfc/reference/cgopherfilefind-class.md)   
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile Class](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile Class](../../mfc/reference/chttpfile-class.md)