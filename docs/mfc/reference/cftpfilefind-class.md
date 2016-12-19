---
title: "CFtpFileFind Class | Microsoft Docs"
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
  - "CFtpFileFind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFtpFileFind class"
  - "文件搜索 [C++]"
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
caps.latest.revision: 23
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFtpFileFind Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在Internet FTP服务器文件搜索的帮助。  
  
## 语法  
  
```  
class CFtpFileFind : public CFileFind  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CFtpFileFind::CFtpFileFind](../Topic/CFtpFileFind::CFtpFileFind.md)|构造 `CFtpFileFind` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CFtpFileFind::FindFile](../Topic/CFtpFileFind::FindFile.md)|查找在FTP服务器的文件。|  
|[CFtpFileFind::FindNextFile](../Topic/CFtpFileFind::FindNextFile.md)|继续以前的文件搜索调用 [FindFile](../Topic/CFtpFileFind::FindFile.md)。|  
|[CFtpFileFind::GetFileURL](../Topic/CFtpFileFind::GetFileURL.md)|获取URL，其中包含路径，则找到文件。|  
  
## 备注  
 `CFtpFileFind` 包括开始搜索，查找文件，并返回URL或其他描述性信息有关文件的成员函数。  
  
 对于Internet和本地文件模型中的其他MFC选件类中搜索包含 [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) 和 [CFileFind](../../mfc/reference/cfilefind-class.md)。  无论服务器协议或文件类型\(本地计算机或远程服务器\)，而 `CFtpFileFind`时，这些选件类为客户端提供一种无缝的结构以查找特定的文件。  请注意不要搜索的MFC选件类在HTTP服务器，因为HTTP不支持对于搜索所需的直接文件。  
  
 有关如何使用 `CFtpFileFind` 和其他WinInet选件类的更多信息，请参见文章 [编程时WinInet的Internet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 示例  
 下面的代码演示如何枚举在FTP服务器上的当前目录中的所有文件。  
  
 [!code-cpp[NVC_MFCWinInet#8](../../mfc/reference/codesnippet/CPP/cftpfilefind-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CFtpFileFind`  
  
## 要求  
 **Header:** afxinet.h  
  
## 请参阅  
 [CFileFind Class](../../mfc/reference/cfilefind-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind Class](../../mfc/reference/cgopherfilefind-class.md)   
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile Class](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile Class](../../mfc/reference/chttpfile-class.md)