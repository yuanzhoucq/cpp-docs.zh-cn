---
title: "CGopherFileFind Class | Microsoft Docs"
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
  - "CGopherFileFind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CGopherFileFind class"
  - "文件搜索 [C++]"
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
caps.latest.revision: 21
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CGopherFileFind Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在Internet地鼠服务器文件搜索的帮助。  
  
> [!NOTE]
>  选件类 `CGopherConnection`、 `CGopherFile`、 `CGopherFileFind`、 `CGopherLocator` 及其成员已弃用，因为它们在Windows XP平台不起作用，但是，它们将继续在以前的平台。  
  
## 语法  
  
```  
class CGopherFileFind : public CFileFind  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CGopherFileFind::CGopherFileFind](../Topic/CGopherFileFind::CGopherFileFind.md)|构造 `CGopherFileFind` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CGopherFileFind::FindFile](../Topic/CGopherFileFind::FindFile.md)|查找在地鼠服务器的文件。|  
|[CGopherFileFind::FindNextFile](../Topic/CGopherFileFind::FindNextFile.md)|继续以前的文件搜索调用 [FindFile](../Topic/CGopherFileFind::FindFile.md)。|  
|[CGopherFileFind::GetCreationTime](../Topic/CGopherFileFind::GetCreationTime.md)|获取指定的文件的创建时间。|  
|[CGopherFileFind::GetLastAccessTime](../Topic/CGopherFileFind::GetLastAccessTime.md)|获取指定文件上次访问时间。|  
|[CGopherFileFind::GetLastWriteTime](../Topic/CGopherFileFind::GetLastWriteTime.md)|获取指定文件上次写入时间。|  
|[CGopherFileFind::GetLength](../Topic/CGopherFileFind::GetLength.md)|获取已找到文件的长度，以字节为单位）。|  
|[CGopherFileFind::GetLocator](../Topic/CGopherFileFind::GetLocator.md)|获取 `CGopherLocator` 对象。|  
|[CGopherFileFind::GetScreenName](../Topic/CGopherFileFind::GetScreenName.md)|获取地鼠屏幕的名称。|  
|[CGopherFileFind::IsDots](../Topic/CGopherFileFind::IsDots.md)|测试当前内容和父目录标记，当循环文件时。|  
  
## 备注  
 `CGopherFileFind` 包括开始搜索，查找文件，并返回文件的URL的成员函数。  
  
 对于Internet和本地文件模型中的其他MFC选件类中搜索包含 [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) 和 [CFileFind](../../mfc/reference/cfilefind-class.md)。  与 `CGopherFileFind`时，这些选件类提供一个无缝的结构以查找特定文件，而不管服务器协议、文件类型或位置\(本地计算机或远程服务器。）请注意不要搜索的MFC选件类在HTTP服务器，因为HTTP不支持搜索需要的直接文件。  
  
> [!NOTE]
>  `CGopherFileFind` 不支持其基类 [CFileFind](../../mfc/reference/cfilefind-class.md)的以下成员函数:  
  
-   [GetRoot](../Topic/CFileFind::GetRoot.md)  
  
-   [GetFileName](../Topic/CFileFind::GetFileName.md)  
  
-   [GetFilePath](../Topic/CFileFind::GetFilePath.md)  
  
-   [GetFileTitle](../Topic/CFileFind::GetFileTitle.md)  
  
-   [GetFileURL](../Topic/CFileFind::GetFileURL.md)  
  
 此外，在中，当使用 `CGopherFileFind`，`CFileFind` 成员函数 [IsDots](../Topic/CFileFind::IsDots.md) 始终是 **FALSE**。  
  
 有关如何使用 `CGopherFileFind` 和其他WinInet选件类的更多信息，请参见文章 [编程时WinInet的Internet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CGopherFileFind`  
  
## 要求  
 **Header:** afxinet.h  
  
## 请参阅  
 [CFileFind Class](../../mfc/reference/cfilefind-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFtpFileFind Class](../../mfc/reference/cftpfilefind-class.md)   
 [CFileFind Class](../../mfc/reference/cfilefind-class.md)   
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile Class](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile Class](../../mfc/reference/chttpfile-class.md)