---
title: 多线程处理： 终止线程在 MFC 中的 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b192c0ee4bc7658fc39791545c4aa9334edd183
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131940"
---
# <a name="multithreading-terminating-threads-in-mfc"></a>多线程处理： 终止线程在 MFC 中
两个正常的情况下会导致线程终止： 控制函数退出或不允许线程运行到完成。 如果字处理器使用后台打印线程，如果已成功打印已完成控制函数将正常终止。 如果用户想要取消打印，但是，后台打印线程必须提前终止。 本主题说明如何实现每种情况以及如何在终止后获取线程的退出代码。  
  
- [正常线程终止](#_core_normal_thread_termination)  
  
- [过早的线程终止](#_core_premature_thread_termination)  
  
- [检索线程的退出代码](#_core_retrieving_the_exit_code_of_a_thread)  
  
##  <a name="_core_normal_thread_termination"></a> 正常线程终止  
 
对于辅助线程，正常线程终止很简单： 退出控制函数并返回一个值，表示终止的原因。 你可以使用[AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread)函数或**返回**语句。 通常情况下，0 表示成功完成，但这取决于您。  
  
对于用户界面线程，该过程也很简单： 从在用户界面线程中，调用[PostQuitMessage](http://msdn.microsoft.com/library/windows/desktop/ms644945) Windows SDK 中。 唯一的参数的`PostQuitMessage`采用是线程的退出代码。 对于辅助线程，0 通常表示成功完成。  
  
##  <a name="_core_premature_thread_termination"></a> 过早的线程终止  
 
过早终止线程是很简单： 调用[AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread)从线程内。 将所需的退出代码作为唯一参数传递。 这将停止执行线程、 解除分配线程的堆栈、 分离附加到线程，所有 Dll 和从内存中删除线程对象。  
  
`AfxEndThread` 必须从调用的线程终止内。 如果你想要从另一个线程终止线程，必须设置两个线程间的通信方法。  
  
##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a> 检索线程的退出代码  
 
若要获取的辅助角色或用户界面线程的退出代码，调用[GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190)函数。 有关此函数的信息，请参阅 Windows SDK。 此函数采用到线程句柄 (存储在`m_hThread`的数据成员`CWinThread`对象) 和一个 dword 值的地址。  
  
如果线程仍处于活动状态， `GetExitCodeThread` STILL_ACTIVE 置于所提供的 DWORD 地址; 否则，退出代码放置在该地址。  
  
检索的退出代码[CWinThread](../mfc/reference/cwinthread-class.md)对象采用一个额外的步骤。 默认情况下，当`CWinThread`线程终止时，删除线程对象。 这意味着，不能访问`m_hThread`数据成员因为`CWinThread`对象不再存在。 若要避免这种情况下，请执行以下操作：  
  
- 设置`m_bAutoDelete`数据成员为 FALSE。 这允许`CWinThread`对象后终止线程。 然后，您可以访问`m_hThread`后终止线程的数据成员。 如果使用此方法，但是，您有责任销毁`CWinThread`对象，因为框架将不会自动为你删除它。 这是首选的方法。  
  
- 单独存储线程的句柄。 创建线程后，将复制其`m_hThread`数据成员 (使用`::DuplicateHandle`) 到另一个变量，并且通过该变量访问。 出现终止的情况和你仍然可以找到线程终止的原因时，这种方式对象会自动删除。 请注意该线程不会终止之前您可以复制句柄。 若要执行此操作的最安全方法是将传递到 CREATE_SUSPENDED [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，和存储句柄，然后继续执行线程通过调用[ResumeThread](../mfc/reference/cwinthread-class.md#resumethread)。  
  
这两种方法可以确定为什么`CWinThread`对象终止。  
  
## <a name="see-also"></a>请参阅  
 
[使用 c + + 和 MFC 多线程处理](multithreading-with-cpp-and-mfc.md)   
[_endthread、_endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)   
[_beginthread、_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
[ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659)