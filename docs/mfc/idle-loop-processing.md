---
title: "空闲循环处理 | Microsoft Docs"
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
  - "后台处理"
  - "空闲循环处理"
  - "空闲处理"
  - "消息, 循环"
  - "MFC, 后台处理"
  - "MFC, 消息"
  - "OnIdle 方法"
  - "PeekMessage 方法"
  - "PeekMessage 方法, 消息循环的其他地方"
  - "处理"
  - "处理, 背景"
  - "处理, 在空闲循环过程中"
  - "线程处理 [MFC], 多线程替代方法"
ms.assetid: 5c7c46c1-6107-4304-895f-480983bb1e44
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 空闲循环处理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

许多应用程序执行的操作“在后台”。有时性能注意事项指定使用多线程处理。此类工作。  线程包括额外的开发系统开销，因此，它们不用于与空闲时间工作的简单任务建议 [OnIdle](../Topic/CWinThread::OnIdle.md) MFC 在函数执行。  本文专门空闲处理。  有关多定向功能的更多信息，请参见以下主题 [Multithreading Topics](../parallel/multithreading-support-for-older-code-visual-cpp.md)：  
  
 后台正确完成在此间隔内不否则用户与应用程序交互。  在开发的应用程序针对 Microsoft Windows 操作系统，再安装应用程序可执行处理通过拆分的空闲时间较长的过程到许多小型的片段。  在处理一段之后，应用程序某些执行控件为使用 [PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943) 循环的窗口。  
  
 本文说明两种执行闲置的处理应用程序：  
  
-   使用 MFC 中的主消息循环中的 **PeekMessage**。  
  
-   嵌入其他 **PeekMessage** 循环在应用程序其他位置。  
  
##  <a name="_core_peekmessage_in_the_mfc_message_loop"></a> MFC 中的 PeekMessage 消息循环  
 在应用程序开发与 MFC，`CWinThread` 类的主消息循环包含调用 [PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943) Win32 API 的消息循环。  此循环也称为 `CWinThread` 的 `OnIdle` 成员函数。消息之间的。  应用程序可以重写 `OnIdle` 函数处理本空闲时间的消息。  
  
> [!NOTE]
>  **运行**、`OnIdle`和某些其他成员函数现在是类 `CWinThread` 的成员而不是 `CWinApp`类。  `CWinApp` 是从 `CWinThread` 中派生的。  
  
 有关执行处理的更多信息，请参见" *MFC 参考"中的*[OnIdle](../Topic/CWinThread::OnIdle.md)。  
  
##  <a name="_core_peekmessage_elsewhere_in_your_application"></a> 在其他 PeekMessage 在应用程序  
 执行的处理的其他方法应用程序在某个函数中涉及嵌入消息循环。  此消息循环类似于 MFC 的主消息循环，请在 [CWinThread::Run](../Topic/CWinThread::Run.md)。  这意味着应用程序中所示的循环用开发 MFC 必须执行许多函数和主消息循环中的方法相同。  下面的代码片段演示 MFC 编写与兼容的消息循环：  
  
 [!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/CPP/idle-loop-processing_1.cpp)]  
  
 若要嵌入函数循环执行的空闲处理此代码。  在此循环中，嵌套的循环重复调用 **PeekMessage**。  只要该调用返回一个非零值，所以循环调用 `CWinThread::PumpMessage` 执行常规消息转换并调度。  虽然 `PumpMessage` 是使用未证明的，可以检查它在 ThrdCore.Cpp 文件的源代码。\\atlmfc\\src\\mfc directory of your Visual C \+\+ 安装中。  
  
 一次关闭内部循环，外部循环执行闲置处理的一个或多个调用 `OnIdle`。  第一次调用是为 MFC 的用途。  可以进行的其他调用 `OnIdle` 执行自己后台工作。  
  
 有关执行处理的更多信息，请参见" MFC 参考"中的[OnIdle](../Topic/CWinThread::OnIdle.md)。  
  
## 请参阅  
 [常规 MFC 主题](../mfc/general-mfc-topics.md)