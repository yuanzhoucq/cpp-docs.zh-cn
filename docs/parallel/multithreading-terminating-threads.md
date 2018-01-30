---
title: "多线程处理： 终止线程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CREATE_SUSPENDED
dev_langs:
- C++
helpviewer_keywords:
- premature thread termination
- starting threads
- threading [MFC], terminating threads
- multithreading [C++], terminating threads
- threading [C++], stopping threads
- terminating threads
- stopping threads
- AfxEndThread method
ms.assetid: 4c0a8c6d-c02f-456d-bd02-0a8c8d006ecb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c287de62169ef5d205ac791071cee4b103f60abc
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2018
---
# <a name="multithreading-terminating-threads"></a>多线程处理：终止线程
两种正常情况下会导致线程终止： 控制函数退出或不允许线程能够运行完成。 如果字处理器用于后台打印的线程，如果已成功打印已完成控制函数将正常终止。 如果用户想要取消的打印，但是，后台打印线程必须提前终止。 本主题说明如何实现的每种情形和如何获取线程的退出代码之后它终止。  
  
-   [正常线程终止](#_core_normal_thread_termination)  
  
-   [过早的线程终止](#_core_premature_thread_termination)  
  
-   [检索线程的退出代码](#_core_retrieving_the_exit_code_of_a_thread)  
  
##  <a name="_core_normal_thread_termination"></a>正常线程终止  
 对于工作线程，普通线程终止很简单： 退出控制函数并返回一个值，表示终止的原因。 你可以使用[AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread)函数或`return`语句。 通常情况下，0 表示成功完成，但这取决于你。  
  
 对于用户界面线程，该过程很同样很简单： 从用户界面线程中中, 调用[PostQuitMessage](http://msdn.microsoft.com/library/windows/desktop/ms644945)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。 唯一的参数， **PostQuitMessage**采用是在线程退出代码。 对于工作线程，0 通常表示成功完成。  
  
##  <a name="_core_premature_thread_termination"></a>过早的线程终止  
 过早终止线程是几乎一样简单： 调用[AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread)从线程中。 将所需的退出代码作为唯一参数传递。 这停止线程的执行，释放线程的堆栈，分离附加到线程，所有 Dll 并从内存中删除使线程对象。  
  
 `AfxEndThread`必须从中进行调用的线程将被终止。 如果你想要从另一个线程终止线程，必须设置两个线程之间的通信方法。  
  
##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a>检索线程的退出代码  
 若要获取的辅助进程或用户界面线程退出代码，调用[GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190)函数。 有关此函数的信息，请参阅[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。 此函数采用到线程句柄 (存储在`m_hThread`数据成员的`CWinThread`对象) 的地址`DWORD`。  
  
 如果线程是仍处于活动状态， **GetExitCodeThread**放置**STILL_ACTIVE**从提供`DWORD`地址; 否则，退出代码放在此地址。  
  
 检索的退出代码[CWinThread](../mfc/reference/cwinthread-class.md)对象所花费额外的步骤。 默认情况下，当`CWinThread`线程终止时，删除使线程对象。 这意味着你无法访问`m_hThread`数据成员因为`CWinThread`对象不再存在。 若要避免这种情况下，请执行以下操作：  
  
-   设置`m_bAutoDelete`到的数据成员**FALSE**。 这允许`CWinThread`对象得以后终止线程。 然后就可以访问`m_hThread`数据成员后终止线程。 如果你使用此技术，但是，你将负责销毁`CWinThread`对象，因为框架将不会自动为你删除。 这是首选的方法。  
  
-   单独存储的线程句柄。 创建线程后，将复制其`m_hThread`数据成员 (使用**:: DuplicateHandle**) 给另一个变量，并且通过该变量访问它。 当发生终止，并且你仍可以找出线程终止的原因，将自动删除这种方式对象。 请注意，线程不会终止之前可以复制该句柄。 若要执行此操作的最安全方法是将传递**CREATE_SUSPENDED**到[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)存储句柄，，然后通过调用恢复线程[ResumeThread](../mfc/reference/cwinthread-class.md#resumethread)。  
  
 任何一种方法可以确定为何`CWinThread`终止的对象。  
  
## <a name="see-also"></a>请参阅  
 [使用 c + + 和 MFC 多线程处理](../parallel/multithreading-with-cpp-and-mfc.md)   
 [_endthread、_endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)   
 [_beginthread、_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659)