---
title: "CGopherLocator Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CGopherLocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CGopherLocator class"
  - "gopher locator"
  - "Internet, gopher searches"
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CGopherLocator Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从地鼠服务器获取地鼠“定位器”，确定定位器的类型，并使定位器可用 [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)。  
  
> [!NOTE]
>  选件类 `CGopherConnection`、 `CGopherFile`、 `CGopherFileFind`、 `CGopherLocator` 及其成员已弃用，因为它们在Windows XP平台不起作用，但是，它们将继续在以前的平台。  
  
## 语法  
  
```  
class CGopherLocator : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CGopherLocator::CGopherLocator](../Topic/CGopherLocator::CGopherLocator.md)|构造 `CGopherLocator` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CGopherLocator::GetLocatorType](../Topic/CGopherLocator::GetLocatorType.md)|分析地鼠定位器并确定其属性。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CGopherLocator::operator LPCTSTR](../Topic/CGopherLocator::operator%20LPCTSTR.md)|在 `CGopherLocator` 对象存储的直接访问字符.作为c样式字符串。|  
  
## 备注  
 它可以从该服务器之前，检索信息应用程序必须捕获地鼠服务器的定位器\(url）。  一旦具有定位器\(url\)，它必须将定位器\(url\)视为一个不透明的标记。  
  
 每个地鼠定位器具有定位找到文件或服务器类型的属性。  为地鼠定位器类型的列表参见 [GetLocatorType](../Topic/CGopherLocator::GetLocatorType.md)。  
  
 应用程序对通常使用定位器到 [CGopherFileFind::FindFile](../Topic/CGopherFileFind::FindFile.md) 检索一个特定信息。  
  
 若要了解更多信息 `CGopherLocator` 与其他MFC Internet选件类，请参见文章 [编程时WinInet的Internet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGopherLocator`  
  
## 要求  
 **Header:** afxinet.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind Class](../../mfc/reference/cgopherfilefind-class.md)