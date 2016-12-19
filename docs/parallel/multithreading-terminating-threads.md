---
title: "多线程处理：终止线程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CREATE_SUSPENDED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxEndThread 方法"
  - "多线程处理 [C++], 终止线程"
  - "过早的线程终止"
  - "启动线程"
  - "终止线程"
  - "终止线程"
  - "线程处理 [C++], 终止线程"
  - "线程处理 [MFC], 终止线程"
ms.assetid: 4c0a8c6d-c02f-456d-bd02-0a8c8d006ecb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 多线程处理：终止线程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通常导致线程终止的两种情况是：控制函数退出或不允许线程完成运行。  如果字处理器使用后台打印线程，若成功完成打印，则控制函数将正常终止。  但是，如果用户要取消打印，后台打印线程则不得不提前终止。  本主题介绍如何实现每一种情况，以及在终止后如何获取线程的退出代码。  
  
-   [正常线程终止](#_core_normal_thread_termination)  
  
-   [过早的线程终止](#_core_premature_thread_termination)  
  
-   [检索线程的退出代码](#_core_retrieving_the_exit_code_of_a_thread)  
  
##  <a name="_core_normal_thread_termination"></a> 正常线程终止  
 对于辅助线程，正常线程终止很简单：退出控制函数并返回表示终止原因的值。  可以使用 [AfxEndThread](../Topic/AfxEndThread.md) 函数或 `return` 语句。  一般情况下，0 表示成功完成，但这取决于您自己。  
  
 对于用户界面线程，该过程也很简单：从用户界面线程内调用 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的 [PostQuitMessage](http://msdn.microsoft.com/library/windows/desktop/ms644945)。  **PostQuitMessage** 采用的唯一参数是线程的退出代码。  对于辅助线程，0 通常表示成功完成。  
  
##  <a name="_core_premature_thread_termination"></a> 过早的线程终止  
 过早终止线程几乎一样简单：从线程内调用 [AfxEndThread](../Topic/AfxEndThread.md)。  将所需的退出代码作为唯一参数传递。  这将停止执行线程、解除对线程堆栈的分配、分离附加到线程的所有 DLL 并从内存中删除线程对象。  
  
 必须从要终止的线程内调用 `AfxEndThread`。  如果要从其他线程终止线程，必须设置两个线程间的通信方法。  
  
##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a> 检索线程的退出代码  
 若要获取辅助线程或用户界面线程的退出代码，请调用 [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190) 函数。  有关此函数的信息，请参见 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)]。  此函数获取线程（存储在 `CWinThread` 对象的 `m_hThread` 数据成员中）的句柄和 `DWORD` 的地址。  
  
 如果线程仍然是活动的，**GetExitCodeThread** 将 **STILL\_ACTIVE** 放置在提供的 `DWORD` 地址中；否则将退出代码放置在该地址中。  
  
 检索 [CWinThread](../mfc/reference/cwinthread-class.md) 对象的退出代码还需要一步。  默认情况下，当 `CWinThread` 线程终止时，删除该线程对象。  这意味着不能访问 `m_hThread` 数据成员，因为 `CWinThread` 对象不再存在。  若要避免出现这种情况，请执行以下操作之一：  
  
-   将 `m_bAutoDelete` 数据成员设置为 **FALSE**。  这使 `CWinThread` 对象在线程终止后仍可以继续存在。  然后可以在线程终止后，访问 `m_hThread` 数据成员。  但是，如果使用此方法，就得销毁 `CWinThread` 对象，因为框架不会自动删除该对象。  这是首选方法。  
  
-   单独存储线程的句柄。  创建线程后，（使用 **::DuplicateHandle**）将其 `m_hThread` 数据成员复制到其他变量，并通过该变量访问该成员。  这样，终止后即会自动删除对象，并且仍然可以找到线程终止的原因。  请注意：在可以复制句柄之前，线程不终止。  执行此操作的最安全的方式是将 **CREATE\_SUSPENDED** 传递到 [AfxBeginThread](../Topic/AfxBeginThread.md)，存储句柄，然后通过调用 [ResumeThread](../Topic/CWinThread::ResumeThread.md) 继续执行线程。  
  
 任一方法都可以使您确定 `CWinThread` 对象终止的原因。  
  
## 请参阅  
 [使用 C\+\+ 和 MFC 进行多线程编程](../parallel/multithreading-with-cpp-and-mfc.md)   
 [\_endthread、\_endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)   
 [\_beginthread、\_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659)