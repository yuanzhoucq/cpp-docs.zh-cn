---
title: "CCachedDataPathProperty Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CCachedDataPathProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], 异步"
  - "asynchronous controls [C++]"
  - "CCachedDataPathProperty class"
  - "memory files [C++]"
  - "OLE 控件 [C++], 异步"
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CCachedDataPathProperty Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在内存文件实现一个OLE控件的属性调用了异步和缓存。  
  
## 语法  
  
```  
class CCachedDataPathProperty : public CDataPathProperty  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CCachedDataPathProperty::CCachedDataPathProperty](../Topic/CCachedDataPathProperty::CCachedDataPathProperty.md)|构造 `CCachedDataPathProperty` 对象。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CCachedDataPathProperty::m\_Cache](../Topic/CCachedDataPathProperty::m_Cache.md)|的`CMemFile` 对象来缓存数据。|  
  
## 备注  
 内存文件在RAM中而不是在磁盘中并进行快速临时调用很有用。  
  
 与 **CAysncMonikerFile** 和 `CDataPathProperty`一起，`CCachedDataPathProperty` 提供功能为在OLE控件的异步标记的使用。  `CCachedDataPathProperty` 对象，可以从URL或文件数据源传输异步并将它存储在内存文件。`m_Cache` 公共变量。  所有数据在内存文件中，并且不需要重写 [OnDataAvailable](../Topic/CAsyncMonikerFile::OnDataAvailable.md)，除非要监视通知和响应。  例如，因此，如果调用一种.GIF文件并希望通知您的控件更多数据到达了，并且应重绘自身，重写使通知的 `OnDataAvailable`。  
  
 选件类 `CCachedDataPathProperty` 从 `CDataPathProperty`派生。  
  
 有关如何使用异步标记和ActiveX控件的更多信息在Internet应用程序，请参见以下主题:  
  
-   [Internet第一步:ActiveX控件](../../mfc/activex-controls-on-the-internet.md)  
  
-   [Internet第一步:异步标记](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C文件](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)  
  
 `CCachedDataPathProperty`  
  
## 要求  
 **Header:** afxctl.h  
  
## 请参阅  
 [CDataPathProperty Class](../../mfc/reference/cdatapathproperty-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDataPathProperty Class](../../mfc/reference/cdatapathproperty-class.md)