---
title: "CGopherFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CGopherFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CGopherFile 类"
  - "gopher protocol files"
  - "Internet, gopher"
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CGopherFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在地鼠服务器提供功能来查找并读取文件。  
  
> [!NOTE]
>  选件类 `CGopherConnection`、 `CGopherFile`、 `CGopherFileFind`、 `CGopherLocator` 及其成员已弃用，因为它们在Windows XP平台不起作用，但是，它们将继续在以前的平台。  
  
## 语法  
  
```  
class CGopherFile : public CInternetFile  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CGopherFile::CGopherFile](../Topic/CGopherFile::CGopherFile.md)|构造 `CGopherFile` 对象。|  
  
## 备注  
 地鼠服务不允许用户将数据写入地鼠文件，因为此服务功能主要是为了找到的信息项列表可使接口。  `CGopherFile` 成员函数 **Write**、 `WriteString`和 `Flush` 没有为 `CGopherFile`实现。  调用 `CGopherFile` 对象的函数，返回 [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 若要了解更多信息 `CGopherFile` 与其他MFC Internet选件类，请参见文章 [编程时WinInet的Internet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C文件](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CGopherFile`  
  
## 要求  
 **Header:** afxinet.h  
  
## 请参阅  
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [CGopherLocator Class](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFileFind Class](../../mfc/reference/cgopherfilefind-class.md)   
 [CGopherConnection Class](../../mfc/reference/cgopherconnection-class.md)