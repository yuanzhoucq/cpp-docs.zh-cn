---
title: 多线程处理： 创建 MFC 用户界面线程 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06158f50364320c96223d5627386a059761baa77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416313"
---
# <a name="multithreading-creating-mfc-user-interface-threads"></a>多线程处理： 创建 MFC 用户界面线程

用户界面线程通常用于处理用户输入并响应用户事件独立于执行的应用程序其他部分的线程。 主应用程序线程 (中提供你`CWinApp`的派生类) 已创建并启动。 本主题介绍创建其他用户界面线程所需的步骤。

创建用户界面线程时必须执行操作的第一件事是从派生类[CWinThread](../mfc/reference/cwinthread-class.md)。 必须声明并实现此类，使用[DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate)并[IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate)宏。 此类必须重写某些函数，可以覆盖其他人。 下表中显示这些函数以及应做些什么。

### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>要创建用户界面线程时重写函数

|函数|目标|
|--------------|-------------|
|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)|当线程终止时执行清理。 通常被重写。|
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)|执行线程实例初始化。 必须重写。|
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)|执行特定于线程的空闲时间处理。 通常不重写。|
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)|筛选消息之前发送到`TranslateMessage`和`DispatchMessage`。 通常不重写。|
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)|截获由线程的消息和命令处理程序引发的未经处理的异常。 通常不重写。|
|[运行](../mfc/reference/cwinthread-class.md#run)|线程的控制函数。 包含消息泵。 很少被重写。|

MFC 通过参数重载提供两个版本的 `AfxBeginThread`：一个只能创建辅助线程，另一个既可创建用户界面线程也可创建辅助线程。 若要启动你的用户界面线程，调用第二个重载[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，提供以下信息：

- [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class)类派生自的`CWinThread`。

- （可选）所需的优先级。 默认值为正常优先级。 有关可用的优先级级别的详细信息，请参阅[SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) Windows SDK 中。

- （可选）线程所需的堆栈大小。 默认值为同一个与创建线程堆栈大小。

- （可选）如果你想要创建一个处于挂起状态的线程，CREATE_SUSPENDED。 默认值为 0，或正常启动线程。

- （可选）所需的安全属性。 默认值为与父线程相同的访问权限。 有关此安全信息的格式的详细信息，请参阅[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) Windows SDK 中。

`AfxBeginThread` 为您完成大部分工作。 它创建您的类的新对象，使用你提供的信息，并调用其进行初始化[CWinThread::CreateThread](../mfc/reference/cwinthread-class.md#createthread)开始执行线程。 整个过程进行检查以确保所有对象都都已解除分配正确应创建的任何部分出现故障。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [多线程处理：终止线程](multithreading-terminating-threads.md)

- [多线程处理：创建辅助线程](multithreading-creating-worker-threads.md)

- [进程和线程](/windows/desktop/ProcThread/processes-and-threads)

## <a name="see-also"></a>请参阅

[使用 C++ 和 MFC 进行多线程编程](multithreading-with-cpp-and-mfc.md)