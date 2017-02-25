---
title: "Internet 上的异步名字对象 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], 异步"
  - "异步名字对象 [C++]"
  - "下载 Internet 资源和异步名字对象"
  - "Internet [C++], 异步下载"
  - "MFC [C++], 异步名字对象"
  - "优化 [C++], 跨 Internet 异步下载"
  - "Web 应用程序 [C++], 异步"
ms.assetid: 418b0c64-0046-4dae-8118-c9c762b5822e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Internet 上的异步名字对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由于其网络访问的速度慢， Internet 需要新的方法为应用程序设计。  应用程序应执行异步网络访问避免停止用户界面。  MFC 类 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) 为下载文件提供了异步支持。  
  
 使用异步修饰，可以扩展 COM 应用程序在 Internet 上异步下载和对大对象，例如位图和 VRML 对象，提供进度呈现 。  异步修饰使得在 Internet 上下载 ActiveX 控件属性或文件，不阻塞用户界面 \(UI\) 的响应。  
  
## 异步修饰的优点  
 可使用异步修饰于：  
  
-   下载代码和文件不阻塞。  
  
-   下载ActiveX 控件的属性不阻塞。  
  
-   接收下载进度的通知。  
  
-   跟踪进度和就绪状态信息。  
  
-   提供用户有关进度的状态信息。  
  
-   允许用户可以随时取消下载。  
  
## MFC 类的异步修饰  
 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) 派生自 [CMonikerFile](../mfc/reference/cmonikerfile-class.md)，而后者派生自 [COleStreamFile](../mfc/reference/colestreamfile-class.md)。  `COleStreamFile` 对象表示数据流；`CMonikerFile` 对象使用 `IMoniker` 获取数据，而 `CAsyncMonikerFile` 对象异步获取。  
  
 异步修饰主要用于在 Internet 启用的应用程序和 ActiveX 控件，以便文件传输过程提供具有响应能力的用户界面。  这种情况的一个极好示例是使用 [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md) 为 ActiveX 控件提供异步的属性。  
  
## 针对 ActiveX 控件中数据路径的 MFC 类  
 MFC 类 `CDataPathProperty` 和 [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md) 实现 ActiveX 控件的属性使其可以异步加载。  异步的属性在同步的启动后加载。  异步的 ActiveX 控件重复调用回调指示在长时间的属性交换过程中新的数据的可用性。  
  
 `CDataPathProperty` 是从 `CAsyncMonikerFile` 中派生的。  `CCachedDataPathProperty` 是从 `CDataPathProperty` 中派生的。  在 ActiveX 控件中实现异步属性，从 `CDataPathProperty` 或 `CCachedDataPathProperty` 派生一个类并重写 [Ondataavailable](../Topic/CAsyncMonikerFile::OnDataAvailable.md) 和其它希望接收的通知。  
  
#### 使用异步修饰下载文件  
  
1.  声明类派生自 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)  
  
2.  重写 [Ondataavailable](../Topic/CAsyncMonikerFile::OnDataAvailable.md) 来显示数据。  
  
3.  重写其他成员函数，包括 [OnProgress](../Topic/CAsyncMonikerFile::OnProgress.md)[OnStartBinding](../Topic/CAsyncMonikerFile::OnStartBinding.md) 和 [OnStopBinding](../Topic/CAsyncMonikerFile::OnStopBinding.md)。  
  
4.  声明此类的实例并使用它打开 URLs。  
  
 有关在 ActiveX 控件中异步下载的更多信息，请参见 [Internet 上的 ActiveX 控件](../mfc/activex-controls-on-the-internet.md)。  
  
## 请参阅  
 [MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)   
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)