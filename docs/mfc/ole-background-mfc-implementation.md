---
title: "OLE 后台：MFC 实现 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IMarshall"
  - "IMoniker"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IMarshall 类"
  - "IMoniker 接口, MFC"
  - "MFC 库, 实现"
  - "OLE IMarshal 接口"
  - "OLE IMoniker 接口"
  - "OLE IUnknown"
  - "OLE MFC 库实现"
  - "OLE, 复合文件"
ms.assetid: 2b67016a-d78e-4d60-925f-c28ec8fb6180
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE 后台：MFC 实现
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由于的原始 OLE API 的大小和复杂性，直接调用它编写 OLE 应用程序中非常耗时。  OLE 的 Microsoft 基础类库实现的目的是减少必须编写完成功能齐备的OLE 的应用程序的工作。  
  
 本文说明不是实现的内部 MFC OLE API 的一部分。  该讨论还解释如何什么是实现的映射到 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 OLE 部分。  
  
##  <a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a> 类库不实现的 OLE 的部分  
 MFC 不直接提供 OLE 一些接口和功能。  如果您要使用这些功能，您可以直接调用 OLE API。  
  
 IMoniker 接口  
 `IMoniker` 接口由类库 \(例如，`COleServerItem` 类\)实现，但以前尚未公开到程序员。  有关此接口的更多信息，请参见" [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 OLE 章节的 OLE Moniker实现。  不过，还请参见类 [CMonikerFile](../mfc/reference/cmonikerfile-class.md)和类 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)。  
  
 IUnknown 和 IMarshal 接口  
 **IUnknown** 接口由类库实现，但未公开给开发者。  **IMarshal** 接口未由该类库实现，但是在内部使用。  使用类库生成的自动化服务器已安装的封送功能。  
  
 Docfiles \(复合文件\)  
 复合文件由类库部分支持。  直接操作所创建的复合文件的函数都不受支持。  MFC 使用 **COleFileStream** 类通过使用标准文件函数支持流的处理。  有关更多信息，请参见文章 [容器：复合文件](../mfc/containers-compound-files.md)。  
  
 进程内服务器和对象处理程序  
 进程内服务器和对象处理程序在动态链接库 \(DLL\) 中允许编辑数据或完整的组件对象模型 \(COM\) 对象的可视对象的实现。  为此，可以通过直接调用 OLE API 实现 DLL。  如果正在编写自动化服务器并且该服务器没有用户界面，可以使用AppWizard是该服务器成为进程内服务器并将其完全放入 DLL。  有关这些主题的更多信息，请参见 [自动化服务器](../mfc/automation-servers.md)。  
  
> [!TIP]
>  最简单的方法来实现自动化服务器就是将它放入 DLL。  MFC 支持此方法。  
  
 有关 Microsoft OLE 基础方式的更多信息类实现 OLE 接口，请参见 MFC 技术声明、[38](../mfc/tn038-mfc-ole-iunknown-implementation.md)[39](../mfc/tn039-mfc-ole-automation-implementation.md)和 [40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)。  
  
## 请参阅  
 [OLE 后台](../mfc/ole-background.md)   
 [OLE 后台：实现策略](../mfc/ole-background-implementation-strategies.md)