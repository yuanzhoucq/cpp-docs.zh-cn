---
title: 多线程处理：创建 MFC 用户界面线程
ms.date: 08/27/2018
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
ms.openlocfilehash: 1cd28a848f9be223f43412c3e0f3961cef9db6c7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512086"
---
# <a name="multithreading-creating-mfc-user-interface-threads"></a>多线程处理：创建 MFC 用户界面线程

用户界面线程通常用于处理用户输入，并独立于执行应用程序其他部分的线程来响应用户事件。 主应用程序线程（在派生类`CWinApp`中提供）已创建并启动。 本主题介绍创建其他用户界面线程所需的步骤。

创建用户界面线程时，必须执行的第一件事是从[CWinThread](../mfc/reference/cwinthread-class.md)派生类。 必须使用[DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate)和[IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate)宏声明并实现此类。 此类必须重写一些函数，并且可以重写其他函数。 下表介绍了这些函数及其功能。

### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>创建用户界面线程时要重写的函数

|函数|用途|
|--------------|-------------|
|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)|当线程终止时执行清理。 通常被重写。|
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)|执行线程实例初始化。 必须重写。|
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)|执行特定于线程的空闲时间处理。 通常不重写。|
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)|在将消息调度到`TranslateMessage`和`DispatchMessage`之前筛选消息。 通常不重写。|
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)|截获线程消息和命令处理程序引发的未经处理的异常。 通常不重写。|
|[运行](../mfc/reference/cwinthread-class.md#run)|控制线程的函数。 包含消息泵。 很少重写。|

MFC 通过参数重载提供两个版本的 `AfxBeginThread`：一个只能创建辅助线程，另一个既可创建用户界面线程也可创建辅助线程。 若要启动用户界面线程，请调用[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)的第二个重载，并提供以下信息：

- 派生自`CWinThread`的类的 [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class)。

- 可有可无所需的优先级。 默认值为正常优先级。 有关可用优先级的详细信息，请参阅 Windows SDK 中的[参见 setthreadpriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 。

- 可有可无线程所需的堆栈大小。 默认值与创建线程的堆栈大小相同。

- 可有可无如果希望线程在挂起状态中创建，则为 CREATE_SUSPENDED。 默认值为0，或正常启动线程。

- 可有可无所需的安全特性。 默认值与父线程具有相同的访问权限。 有关此安全信息的格式的详细信息，请参阅 Windows SDK 中的[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 。

`AfxBeginThread`为您完成大部分工作。 它创建类的新对象，使用您提供的信息对其进行初始化，并调用[CWinThread：： CreateThread](../mfc/reference/cwinthread-class.md#createthread)以开始执行线程。 在整个过程中进行检查，以确保在创建过程中的任何部分都不会正确释放所有对象。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [多线程处理：终止线程](multithreading-terminating-threads.md)

- [多线程处理：创建工作线程](multithreading-creating-worker-threads.md)

- [进程和线程](/windows/win32/ProcThread/processes-and-threads)

## <a name="see-also"></a>请参阅

[使用 C++ 和 MFC 进行多线程编程](multithreading-with-cpp-and-mfc.md)
