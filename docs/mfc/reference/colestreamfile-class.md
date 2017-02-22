---
title: "COleStreamFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleStreamFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleStreamFile class"
  - "data streams [C++]"
  - "data streams [C++], OLE"
  - "OLE [C++], streams of data"
  - "OLE structured storage [C++]"
  - "streams [C++], OLE"
  - "structured storage in OLE"
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# COleStreamFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示数据流\(`IStream`\)作为OLE结构化存储一部分，在复合文件。  
  
## 语法  
  
```  
class COleStreamFile : public CFile  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleStreamFile::COleStreamFile](../Topic/COleStreamFile::COleStreamFile.md)|构造 `COleStreamFile` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleStreamFile::Attach](../Topic/COleStreamFile::Attach.md)|关联流与对象。|  
|[COleStreamFile::CreateMemoryStream](../Topic/COleStreamFile::CreateMemoryStream.md)|创建从全局内存的流并将其与对象。|  
|[COleStreamFile::CreateStream](../Topic/COleStreamFile::CreateStream.md)|创建一个流并将其与对象。|  
|[COleStreamFile::Detach](../Topic/COleStreamFile::Detach.md)|分离对象的流。|  
|[COleStreamFile::GetStream](../Topic/COleStreamFile::GetStream.md)|返回当前流。|  
|[COleStreamFile::OpenStream](../Topic/COleStreamFile::OpenStream.md)|安全打开流并将其与对象。|  
  
## 备注  
 `IStorage` 对象必须存在，可以打开流或之前，除非它是内存流。  
  
 `COleStreamFile` 对象中操作方式与 [C文件](../../mfc/reference/cfile-class.md) 对象。  
  
 有关操作的流和存储的更多信息，请参见文章 [容器:复合文件](../../mfc/containers-compound-files.md)。  
  
 有关更多信息，请参见 [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) 和 [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) 在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C文件](../../mfc/reference/cfile-class.md)  
  
 `COleStreamFile`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)