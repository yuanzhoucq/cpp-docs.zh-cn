---
title: 多线程处理：在 MFC 中创建工作线程
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
ms.openlocfilehash: ab5b05b64ebcfbd6d15bd2229ee19d18fa7f919d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140518"
---
# <a name="multithreading-creating-worker-threads-in-mfc"></a>多线程处理：在 MFC 中创建工作线程

工作线程通常用于处理后台任务，用户无需等待即可继续使用应用程序。 重新计算和后台打印等任务就是工作线程的很好的例子。 本主题详细介绍了创建辅助线程所需的步骤。 包括以下主题：

- [启动线程](#_core_starting_the_thread)

- [实现控制函数](#_core_implementing_the_controlling_function)

- [示例](#_core_controlling_function_example)

创建辅助线程是一个相对简单的任务。 只需执行两个步骤就能使线程运行：实现控制函数并启动线程。 不需要从[CWinThread](../mfc/reference/cwinthread-class.md)派生类。 如果需要特殊版本的 `CWinThread`，则可以派生类，但对于大多数简单的工作线程，此方法不是必需的。 无需修改即可使用 `CWinThread`。

## <a name="_core_starting_the_thread"></a>启动线程

`AfxBeginThread`有两个重载版本：一个只能创建辅助线程，另一个可创建用户界面线程和工作线程。 若要使用第一个重载开始执行工作线程，请调用[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，并提供以下信息：

- 控制函数的地址。

- 要传递到控制函数的参数。

- 可有可无线程所需的优先级。 默认值为正常优先级。 有关可用优先级的详细信息，请参阅 Windows SDK 中的[参见 setthreadpriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 。

- 可有可无线程所需的堆栈大小。 默认值与创建线程的堆栈大小相同。

- 可有可无如果希望在挂起状态中创建线程，则 CREATE_SUSPENDED。 默认值为0，或正常启动线程。

- 可有可无所需的安全特性。 默认值与父线程具有相同的访问权限。 有关此安全信息的格式的详细信息，请参阅 Windows SDK 中的[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 。

`AfxBeginThread` 为您创建和初始化一个 `CWinThread` 对象，启动该对象并返回其地址，以便以后可以引用它。 在整个过程中进行检查，以确保在创建过程中的任何部分都不会正确释放所有对象。

## <a name="_core_implementing_the_controlling_function"></a>实现控制函数

控制函数定义线程。 输入此函数后，线程将开始，并且在退出时，线程终止。 此函数应具有以下原型：

```cpp
UINT MyControllingFunction( LPVOID pParam );
```

参数是单个值。 函数在此参数中接收的值是创建线程对象时传递给构造函数的值。 控制函数可以通过它选择的任何方式解释此值。 它可以被视为标量值或指向包含多个参数的结构的指针，也可以被忽略。 如果参数引用结构，则该结构不仅可用于将数据从调用方传递到线程，还可以将数据从线程传递回调用方。 如果使用此类结构将数据传递回调用方，则在结果准备就绪时，该线程需要通知调用方。 有关从工作线程到调用方的通信的信息，请参见[多线程处理：编程提示](multithreading-programming-tips.md)。

当函数终止时，它应返回指示终止原因的 UINT 值。 通常，此退出代码为0，表示成功，并提供指示不同错误类型的其他值。 这是纯粹依赖实现的。 某些线程可以维护对象的使用计数，并返回该对象的当前使用数量。 若要查看应用程序如何检索此值，请参阅[多线程处理：终止线程](multithreading-terminating-threads.md)。

对于使用 MFC 库编写的多线程程序中的内容，有一些限制。 有关这些限制的说明以及有关使用线程的其他提示，请参阅[多线程处理：编程提示](multithreading-programming-tips.md)。

## <a name="_core_controlling_function_example"></a>控制函数示例

下面的示例演示如何定义控制函数并从程序的其他部分使用它。

```cpp
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

## <a name="see-also"></a>另请参阅

[使用 C++ 和 MFC 进行多线程编程](multithreading-with-cpp-and-mfc.md)
