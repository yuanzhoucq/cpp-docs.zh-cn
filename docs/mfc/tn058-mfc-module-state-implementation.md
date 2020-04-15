---
title: TN058：MFC 模块状态实现
ms.date: 06/28/2018
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
ms.openlocfilehash: b64fb6b97474007c44a2124315e83e1ac119f9ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366610"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058：MFC 模块状态实现

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本技术说明描述了 MFC"模块状态"构造的实现。 了解模块状态实现对于使用 DLL（或 OLE 进程内服务器）的 MFC 共享 DLL 至关重要。

在阅读本说明之前，请参阅[创建新文档、Windows 和视图](../mfc/creating-new-documents-windows-and-views.md)中的"管理 MFC 模块的状态数据"。 本文包含有关此主题的重要使用信息和概述信息。

## <a name="overview"></a>概述

有三种类型的 MFC 状态信息：模块状态、进程状态和线程状态。 有时可以组合这些状态类型。 例如，MFC 的句柄映射都是模块本地和线程本地。 这允许两个不同的模块在其每个线程中具有不同的映射。

进程状态和线程状态类似。 这些数据项传统上是全局变量，但需要特定于给定的进程或线程，以便适当的 Win32s 支持或适当的多线程支持。 给定数据项适合哪个类别取决于该项及其在进程和线程边界方面的所需语义。

模块状态是唯一的，因为它可以包含处理本地或线程本地的真正全局状态或状态。 此外，它可以快速切换。

## <a name="module-state-switching"></a>模块状态切换

每个线程包含指向"当前"或"活动"模块状态的指针（毫不奇怪，指针是 MFC 线程本地状态的一部分）。 当执行线程通过模块边界（如调用到 OLE 控件或 DLL 的应用程序或调用回应用程序的 OLE 控件）时，此指针将发生更改。

通过调用`AfxSetModuleState`来切换当前模块状态。 在大多数情况下，您永远不会直接处理 API。 在许多情况下，MFC 会为您调用它（在 WinMain、OLE 入口点`AfxWndProc`等）。 这是通过静态链接在特殊`WndProc`中写入的任何组件，以及知道哪个模块状态应该是最新的特殊`WinMain`（`DllMain`或 ） 的组件中完成的。 您可以通过查看 DLLMODUL 来查看此代码。CPP 或 APPMODUL。MFC_SRC 目录中的 CPP。

很少要设置模块状态，然后不将其设置回来。 大多数时候，您希望将自己的模块状态"推送"为当前模块状态，然后在完成后将原始上下文"弹出"回来。 这是由宏[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)和特殊类`AFX_MAINTAIN_STATE`完成的。

`CCmdTarget`具有支持模块状态切换的特殊功能。 特别是， 是`CCmdTarget`用于 OLE 自动化和 OLE COM 入口点的根类。 与向系统公开的任何其他入口点一样，这些入口点必须设置正确的模块状态。 给定人`CCmdTarget`如何知道"正确"模块状态应是什么 答案，它"记住"构造时"当前"模块状态，以便它可以将当前模块状态设置为"记住"值，而稍后调用它。 因此，给定`CCmdTarget`对象关联的模块状态是构造对象时当前状态的模块状态。 以加载 INPROC 服务器、创建对象和调用其方法的简单示例为例。

1. DLL 由 OLE 使用`LoadLibrary`加载。

1. `RawDllMain`首先调用。 它将模块状态设置为 DLL 的已知静态模块状态。 因此`RawDllMain`，它是静态链接到 DLL 的。

1. 调用与我们对象关联的类工厂的构造函数。 `COleObjectFactory`派生自`CCmdTarget`，因此，它记住它实例化的模块状态。 这一点很重要 - 当要求类工厂创建对象时，它现在知道要使当前模块状态。

1. `DllGetClassObject`调用以获取类工厂。 MFC 搜索与此模块关联的类工厂列表并返回它。

1. 调用 `COleObjectFactory::XClassFactory2::CreateInstance`。 在创建对象并返回对象之前，此函数将模块状态设置为步骤 3 中的模块状态（实例化时`COleObjectFactory`为当前状态的模块状态）。 这是[METHOD_PROLOGUE](com-interface-entry-points.md)内部完成的。

1. 创建对象时，它也是一个`CCmdTarget`派生，并且以相同的方式`COleObjectFactory`记住哪个模块状态处于活动状态，此新对象也是如此。 现在，对象知道在调用时要切换到哪个模块状态。

1. 客户端在其从`CoCreateInstance`调用中收到的 OLE COM 对象上调用函数。 当调用对象时，它使用`METHOD_PROLOGUE`来切换模块状态，就像`COleObjectFactory`切换对象一样。

如您所见，模块状态在创建时会从对象传播到对象。 正确设置模块状态非常重要。 如果未设置，则 DLL 或 COM 对象可能与调用它的 MFC 应用程序交互不良，或者可能无法找到自己的资源，或者可能以其他悲惨方式失败。

请注意，某些类型的 DLL，特别是"MFC 扩展"DLL 不会在其`RawDllMain`状态中切换模块状态（实际上，它们通常甚至没有 。 `RawDllMain` 这是因为它们旨在"就像"它们实际存在于使用它们的应用程序中一样。 它们在很大程度上是正在运行的应用程序的一部分，他们打算修改该应用程序的全局状态。

OLE 控件和其他 DLL 非常不同。 他们不想修改调用应用程序的状态;因此，它们不想修改调用应用程序的状态。调用它们的应用程序可能甚至不是 MFC 应用程序，因此可能没有要修改的状态。 这就是模块状态切换被发明的原因。

对于从 DLL 导出的函数（例如在 DLL 中启动对话框的函数），您需要向函数的开头添加以下代码：

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

这将将当前模块状态与从[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)返回的状态交换，直到当前作用域结束。

如果不使用AFX_MODULE_STATE宏，则 DLL 中的资源将出现问题。 默认情况下，MFC 使用主应用程序的资源句柄来加载资源模板。 此模板实际存储在 DLL 中。 根本原因是 MFC 的模块状态信息尚未由AFX_MODULE_STATE宏切换。 资源句柄将从 MFC 的模块状态中恢复。 不切换模块状态将导致使用错误的资源句柄。

不需要将AFX_MODULE_STATE放入 DLL 中的每个函数中。 例如，`InitInstance`可以在应用程序中的 MFC 代码调用，而不会AFX_MODULE_STATE因为 MFC 在`InitInstance``InitInstance`返回之前自动转移模块状态，然后切换回。 所有消息映射处理程序也是如此。 常规 MFC DLL 实际上具有特殊的主窗口过程，可在路由任何消息之前自动切换模块状态。

## <a name="process-local-data"></a>处理本地数据

如果不是 Win32s DLL 模型的困难，处理本地数据就不会那么令人关注。 在 Win32 中，所有 DLL 共享其全局数据，即使由多个应用程序加载也是如此。 这与"真实"Win32 DLL 数据模型非常不同，该模型在每个附加到 DLL 的进程中，每个 DLL 都会获得其数据空间的单独副本。 为了增加复杂性，在 Win32s DLL 中分配给堆上的数据实际上是特定于过程的（至少就所有权而言）。 请考虑以下数据和代码：

```cpp
static CString strGlobal; // at file scope

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, strGlobal);
}
```

请考虑如果上述代码位于 DLL 中，并且 DLL 由两个进程 A 和 B 加载（实际上可能是同一应用程序的两个实例），会发生什么情况。 呼叫`SetGlobalString("Hello from A")`。 因此，在进程 A 的上下文中`CString`为数据分配内存。 请记住，自身是全局的`CString`，A 和 B 都可见。现在 B`GetGlobalString(sz, sizeof(sz))`调用 。 B 将能够看到 A 集的数据。 这是因为 Win32 在像 Win32 这样的进程之间没有提供保护。 这是第一个问题;在许多情况下，不希望一个应用程序影响被视为由其他应用程序拥有的全局数据。

还有其他问题。 假设 A 现在退出。 当 A 退出时，"'"`strGlobal`字符串使用的内存可用于系统， 即，进程 A 分配的所有内存都由操作系统自动释放。 它不被释放，`CString`因为正在调用析构函数;它还没有被调用。 它被释放仅仅是因为分配它的应用程序离开了场景。 现在，如果`GetGlobalString(sz, sizeof(sz))`B 调用 ，它可能得不到有效的数据。 其他应用程序可能将该内存用于其他内容。

显然，存在问题。 MFC 3.x 使用了一种称为线程本地存储 （TLS） 的技术。 MFC 3.x 将分配一个 TLS 索引，在 Win32s 下，该索引实际上充当进程本地存储索引，即使不调用该索引，然后根据该 TLS 索引引用所有数据。 这与用于在 Win32 上存储线程本地数据的 TLS 索引类似（有关该主题的详细信息，请参阅下文）。 这导致每个 MFC DLL 每个进程至少使用两个 TLS 索引。 当您考虑加载许多 OLE 控制 DLL （OCX） 时，您很快就会耗尽 TLS 索引（只有 64 个可用）。 此外，MFC 必须将所有这些数据放在一个位置，在单个结构中。 它不是很可扩展，在使用TLS指数方面并不理想。

MFC 4.x 使用一组类模板来解决此问题，您可以围绕应处理本地处理的数据"包装"。 例如，上述问题可以通过书面解决：

```cpp
struct CMyGlobalData : public CNoTrackObject
{
    CString strGlobal;
};
CProcessLocal<CMyGlobalData> globalData;

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    globalData->strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, globalData->strGlobal);
}
```

MFC 分两步实现此功能。 首先，Win32 __Tls\* __ API（TlsAlloc、TlsSetValue、TlsGetValue 等）**TlsGetValue**顶部有一个层，无论您有多少 DLL，每个进程只使用两个 TLS 索引。**TlsAlloc** **TlsSetValue** 其次，`CProcessLocal`提供模板来访问此数据。 它覆盖运算符>这是允许上面看到的直观语法的原因。 所有由 进行`CProcessLocal`换行的对象都必须派生自`CNoTrackObject`。 `CNoTrackObject`提供较低级别的分配器 （**LocalAlloc**/**LocalFree**） 和虚拟析构函数，以便 MFC 可以在进程终止时自动销毁进程本地对象。 如果需要其他清理，此类对象可以具有自定义析构函数。 上述示例不需要一个，因为编译器将生成默认析构函数来销毁嵌入`CString`的对象。

这种方法还有其他有趣的优点。 不仅所有`CProcessLocal`对象都自动销毁，而且直到需要它们才构造它们。 `CProcessLocal::operator->`将在首次调用关联对象时实例化它，并且不会很快。 在上面的示例中，这意味着在第一次`strGlobal``SetGlobalString`或`GetGlobalString`调用之前不会构造 ''字符串。 在某些情况下，这有助于减少 DLL 启动时间。

## <a name="thread-local-data"></a>线程本地数据

与处理本地数据类似，当数据必须是给定线程的本地时，将使用线程本地数据。 也就是说，您需要访问该数据的每个线程的单独数据实例。 这可以多次用于代替广泛的同步机制。 如果数据不需要由多个线程共享，则此类机制可能非常昂贵且没有必要。 假设我们有一个`CString`对象（与上面的示例类似）。 我们可以通过用模板包装它来使其成为本地线程`CThreadLocal`：

```cpp
struct CMyThreadData : public CNoTrackObject
{
    CString strThread;
};
CThreadLocal<CMyThreadData> threadData;

void MakeRandomString()
{
    // a kind of card shuffle (not a great one)
    CString& str = threadData->strThread;
    str.Empty();
    while (str.GetLength() != 52)
    {
        unsigned int randomNumber;
        errno_t randErr;
        randErr = rand_s(&randomNumber);

        if (randErr == 0)
        {
            TCHAR ch = randomNumber % 52 + 1;
            if (str.Find(ch) <0)
            str += ch; // not found, add it
        }
    }
}
```

如果`MakeRandomString`从两个不同的线程调用，每个线程将以不同的方式"洗牌"字符串，而不会干扰另一个线程。 这是因为实际上每个线程有一个`strThread`实例，而不仅仅是一个全局实例。

请注意如何使用引用捕获`CString`地址一次，而不是每个循环迭代一次。 循环代码可能使用`threadData->strThread`"无处不在"，`str`但代码的执行速度会慢得多。 当此类引用在循环中出现时，最好缓存对数据的引用。

类`CThreadLocal`模板使用相同的机制，`CProcessLocal`执行和相同的实现技术。

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
