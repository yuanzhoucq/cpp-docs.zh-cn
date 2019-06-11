---
title: 多线程处理：在 MFC 中创建工作线程数
ms.date: 11/04/2016
helpviewer_keywords:
- multithreading [C++], worker threads
- background tasks [C++]
- threading [C++], worker threads
- worker threads [C++]
- threading [C++], creating threads
- threading [MFC], worker threads
- threading [C++], user input not required
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
ms.openlocfilehash: 38757337b1bfe5c7994f9a9f26aad2526aa0279c
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504580"
---
# <a name="multithreading-creating-worker-threads-in-mfc"></a>多线程处理：在 MFC 中创建工作线程数

工作线程通常用于处理后台任务，用户不必等待即可继续使用你的应用程序。 重新计算和后台打印等任务，这样工作线程。 本主题详细介绍创建工作线程所需的步骤。 包括以下主题：

- [启动线程](#_core_starting_the_thread)

- [实现控制函数](#_core_implementing_the_controlling_function)

- [示例](#_core_controlling_function_example)

创建辅助线程是一个相对较简单的任务。 只有两个步骤所需使线程运行： 实现控制函数和启动线程。 不需要从派生类[CWinThread](../mfc/reference/cwinthread-class.md)。 如果您需要的特殊版本，可以派生一个类`CWinThread`，但它不是必需的大多数简单辅助线程。 可以使用`CWinThread`无需修改即可。

##  <a name="_core_starting_the_thread"></a> 启动线程

有两个重载的版本`AfxBeginThread`： 一个只能创建辅助线程，另一个可以创建用户界面线程和工作线程。 若要开始使用第一个重载工作线程的执行，请调用[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，提供以下信息：

- 控制函数的地址。

- 要传递到控制函数的参数。

- （可选）所需的线程优先级。 默认值为正常优先级。 有关可用的优先级级别的详细信息，请参阅[SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) Windows SDK 中。

- （可选）线程所需的堆栈大小。 默认值为同一个与创建线程堆栈大小。

- （可选）如果你想要创建一个处于挂起状态的线程，CREATE_SUSPENDED。 默认值为 0，或正常启动线程。

- （可选）所需的安全属性。 默认值为与父线程相同的访问权限。 有关此安全信息的格式的详细信息，请参阅[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) Windows SDK 中。

`AfxBeginThread` 创建并初始化`CWinThread`对象，启动它，并返回其地址，因此可以对其进行引用更高版本。 整个过程进行检查以确保所有对象都都已解除分配正确应创建的任何部分出现故障。

##  <a name="_core_implementing_the_controlling_function"></a> 实现控制函数

控制函数定义线程。 输入此函数后，线程开始，并退出时的线程终止。 此函数应具有以下原型：

```
UINT MyControllingFunction( LPVOID pParam );
```

参数是单个值。 在函数收到此参数中的值是时创建线程对象传递给构造函数的值。 控制函数可以将此值还选择能以任何方式解释。 它可以视为标量值或指向包含多个参数的结构的指针，或可以忽略。 如果参数引用结构，不仅可以将数据从调用方传递到线程，而且还将数据从线程传递到调用方可以使用该结构。 如果使用此类结构将数据传递回调用方，线程需要结果已准备就绪时通知调用方。 有关从工作线程到调用方进行通信的信息，请参阅[多线程处理：编程提示](multithreading-programming-tips.md)。

该函数在终止时，它应返回一个 UINT 值，该值终止的原因。 通常情况下，此退出代码为 0 以指示成功的其他值，该值指示不同类型的错误。 这是只依赖于实现。 某些线程可能会维护对象的使用计数，并返回当前使用该对象的次数。 若要查看应用程序如何检索此值，请参阅[多线程处理：终止线程](multithreading-terminating-threads.md)。

有一些限制，可以编写与 MFC 库的多线程程序中执行的操作。 有关这些限制和使用线程的其他提示的说明，请参阅[多线程处理：编程提示](multithreading-programming-tips.md)。

##  <a name="_core_controlling_function_example"></a> 控制函数示例

下面的示例演示如何定义控制函数和从该程序的另一部分中使用它。

```
UINT MyThreadProc( LPVOID pParam )
{
    CMyObject* pObject = (CMyObject*)pParam;

    if (pObject == NULL ||
        !pObject->IsKindOf(RUNTIME_CLASS(CMyObject)))
    return 1;   // if pObject is not valid

    // do something with 'pObject'

    return 0;   // thread completed successfully
}

// inside a different function in the program
.
.
.
pNewObject = new CMyObject;
AfxBeginThread(MyThreadProc, pNewObject);
.
.
.
```

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [多线程处理：创建用户界面线程](multithreading-creating-user-interface-threads.md)

## <a name="see-also"></a>请参阅

[使用 C++ 和 MFC 进行多线程编程](multithreading-with-cpp-and-mfc.md)
