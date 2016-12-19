---
title: "CMonikerFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMonikerFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMonikerFile class"
  - "IMoniker interface"
  - "IMoniker interface, 绑定"
  - "monikers, MFC"
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMonikerFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示 [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)\([IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)\)命名的数据流。  
  
## 语法  
  
```  
class CMonikerFile : public COleStreamFile  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMonikerFile::CMonikerFile](../Topic/CMonikerFile::CMonikerFile.md)|构造 `CMonikerFile` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMonikerFile::Close](../Topic/CMonikerFile::Close.md)|分离并释放流并发布该标记。|  
|[CMonikerFile::Detach](../Topic/CMonikerFile::Detach.md)|分离此 `CMonikerFile` 对象的 `IMoniker`。|  
|[CMonikerFile::GetMoniker](../Topic/CMonikerFile::GetMoniker.md)|返回当前标记。|  
|[CMonikerFile::Open](../Topic/CMonikerFile::Open.md)|打开所指定的文件获取流。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMonikerFile::CreateBindContext](../Topic/CMonikerFile::CreateBindContext.md)|获取绑定上下文或创建默认初始化的绑定上下文。|  
  
## 备注  
 标记包含信息很象路径名。文件。  如果您有指向标记对象的 `IMoniker` 接口，可以将由标识的文件执行get访问不存在的实际上查找文件的任何其他特定信息。  
  
 从 `COleStreamFile`派生，`CMonikerFile` 使可以通过为标记并绑定到流该标记是一个名称标记或字符串表示形式。  然后可以读写该流。  `CMonikerFile` 的虚拟目的是提供对 `IMoniker`s的简单访问名为的 `IStream`的，因此您不必绑定到流，因此，有 `CFile` 功能入流。  
  
 除了流之外，`CMonikerFile` 不能用于绑定到任何操作。  如果要绑定到存储或对象，则必须直接使用 `IMoniker` 接口。  
  
 有关流的更多信息和标记，请参见 *MFC Reference* 中的 [COleStreamFile](../../mfc/reference/colestreamfile-class.md) 与[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 中的 [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) 和 [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C文件](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 `CMonikerFile`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [COleStreamFile Class](../../mfc/reference/colestreamfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile Class](../../mfc/reference/casyncmonikerfile-class.md)