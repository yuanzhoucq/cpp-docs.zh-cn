---
title: 多线程处理：终止 MFC 中的线程
ms.date: 08/27/2018
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
ms.openlocfilehash: 0625be0a628a6ae991acd2fa1f7118a4deabccda
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217865"
---
# <a name="multithreading-terminating-threads-in-mfc"></a>多线程处理：终止 MFC 中的线程

两种正常情况导致线程终止：控制函数退出，或者不允许线程运行完成。 如果字处理器使用线程进行后台打印，则当打印成功完成时，控制函数将正常终止。 但是，如果用户想要取消打印，则后台打印线程必须提前终止。 本主题介绍了如何实现每种情况，以及如何在线程终止后获取该线程的退出代码。

- [正常线程终止](#_core_normal_thread_termination)

- [过早的线程终止](#_core_premature_thread_termination)

- [检索线程的退出代码](#_core_retrieving_the_exit_code_of_a_thread)

## <a name="normal-thread-termination"></a><a name="_core_normal_thread_termination"></a>正常线程终止

对于工作线程，正常线程终止很简单：退出控制函数并返回一个表示终止原因的值。 可以使用[AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread)函数或 **`return`** 语句。 通常，0表示成功完成，但这由您来完成。

对于用户界面线程，此过程非常简单：从用户界面线程中，在 Windows SDK 中调用[PostQuitMessage](/windows/win32/api/winuser/nf-winuser-postquitmessage) 。 采用的唯一参数 `PostQuitMessage` 是线程的退出代码。 对于工作线程，0通常表示成功完成。

## <a name="premature-thread-termination"></a><a name="_core_premature_thread_termination"></a>过早的线程终止

提前终止线程几乎非常简单：从线程内调用[AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) 。 传递所需的退出代码作为唯一的参数。 这会停止执行线程，释放线程的堆栈，分离附加到线程的所有 Dll，并从内存中删除线程对象。

`AfxEndThread`必须从要终止的线程中调用。 如果要从另一个线程终止线程，则必须在这两个线程之间设置通信方法。

## <a name="retrieving-the-exit-code-of-a-thread"></a><a name="_core_retrieving_the_exit_code_of_a_thread"></a>检索线程的退出代码

若要获取辅助线程或用户界面线程的退出代码，请调用[GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)函数。 有关此函数的信息，请参阅 Windows SDK。 此函数采用线程（存储在对象的数据成员中）的句柄 `m_hThread` `CWinThread` 和 DWORD 的地址。

如果线程仍处于活动状态，则 `GetExitCodeThread` 将 STILL_ACTIVE 放置在提供的 DWORD 地址中; 否则，将在此地址中放置退出代码。

检索[CWinThread](../mfc/reference/cwinthread-class.md)对象的退出代码需额外的步骤。 默认情况下，当 `CWinThread` 线程终止时，将删除该线程对象。 这意味着不能访问 `m_hThread` 数据成员，因为该 `CWinThread` 对象已不存在。 若要避免这种情况，请执行下列操作之一：

- 将 `m_bAutoDelete` 数据成员设置为 FALSE。 这允许 `CWinThread` 对象在线程终止后保留下来。 然后，你可以在 `m_hThread` 线程终止后访问数据成员。 但是，如果使用此方法，则需要负责销毁 `CWinThread` 对象，因为框架不会自动删除它。 这是首选方法。

- 单独存储线程的句柄。 创建线程后，将其 `m_hThread` 数据成员（使用）复制 `::DuplicateHandle` 到另一个变量，并通过该变量访问它。 这样一来，当终止发生时，将自动删除该对象，并且仍可以发现该线程终止的原因。 请注意，在复制句柄之前，该线程不会终止。 要执行此操作，最安全的方法是将 CREATE_SUSPENDED 传递给[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，存储句柄，然后通过调用[ResumeThread](../mfc/reference/cwinthread-class.md#resumethread)恢复线程。

任一方法都可以确定 `CWinThread` 对象终止的原因。

## <a name="see-also"></a>另请参阅

[使用 C++ 和 MFC 进行多线程编程](multithreading-with-cpp-and-mfc.md)<br/>
[_endthread、_endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)<br/>
[_beginthread、_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread)
