---
title: TN058:MFC 模块状态实现
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
ms.openlocfilehash: d803dba36b7790173b21dacb6cb34241f27dfb96
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2019
ms.locfileid: "65610989"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058:MFC 模块状态实现

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

此技术说明描述了 MFC 的"模块状态"构造的实现。 模块状态实现了解至关重要，使用 MFC 共享的 DLL 中的 Dll （或在进程内 OLE 服务器）。

之前阅读此说明，请参阅"管理数据的 MFC 模块状态"中[创建新文档，Windows 和视图](../mfc/creating-new-documents-windows-and-views.md)。 本文包含重要的使用情况信息和有关此主题的概述信息。

## <a name="overview"></a>概述

有三种类型的 MFC 状态信息：模块状态、 过程状态和线程状态。 有时可以组合这些状态类型。 例如，MFC 的句柄映射为模块本地和线程本地。 这允许两个不同的模块用于在每个其线程中具有不同的映射。

进程状态和线程状态很相似。 这些数据项是传统上是全局变量，但具有需要特定于给定进程或线程正确 Win32s 支持或正确的多线程支持的事情。 将给定的数据项所能容纳的类别取决于该项目以及有关进程和线程边界其所需的语义。

模块状态是唯一的因为它可以包含真正的全局状态或是本地的进程或线程本地状态。 此外，它可以快速切换。

## <a name="module-state-switching"></a>切换模块状态

每个线程包含"当前"或"活动"的模块状态的指针 （毫无疑问，该指针是 MFC 的线程本地状态的一部分）。 执行该线程会传递模块边界，例如调用 OLE 控件或 DLL 或 OLE 控件回调到应用程序的应用程序，此指针会更改。

通过调用切换当前模块状态`AfxSetModuleState`。 大多数情况下，您将永远不会直接处理 API。 MFC 中，在许多情况下，将它命名为您 (WinMain，OLE 的入口点，在`AfxWndProc`，等等。)。 这是在编写通过以静态方式链接在一个特殊的任何组件`WndProc`，和一个特殊`WinMain`(或`DllMain`)，知道哪些模块状态应为当前。 通过查看 DLLMODUL，可以看到此代码。CPP 或 APPMODUL。CPP MFC\SRC 目录中。

很少你想要设置的模块状态，然后不重新设置。 大多数情况下你想要"推送"自己的模块与当前状态，然后，完成后，"pop"回原始上下文。 这是由宏[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)和特殊类`AFX_MAINTAIN_STATE`。

`CCmdTarget` 具有特殊功能，以支持模块状态切换。 具体而言，`CCmdTarget`是用于 OLE 自动化和 OLE COM 入口点的根类。 像任何其他入口点公开到系统，这些入口点必须设置正确的模块状态。 如何 does 给定`CCmdTarget`知道"正确"的模块状态应该是什么答案是，它"记住"的"current"的模块状态是在构造，以便它可以设置的当前模块状态的"记住"值更高版本时调用。 因此，该模块状态的给定`CCmdTarget`对象所关联与构造对象时的当前模块状态。 举一个简单例子加载进程内服务器、 创建对象，并调用其方法。

1. 由 OLE 加载了 DLL 使用`LoadLibrary`。

2. `RawDllMain` 首先调用。 它将该 DLL 的模块状态设置为已知静态模块状态。 出于此原因`RawDllMain`静态链接到 DLL。

1. 调用与我们的对象相关联的类工厂的构造函数。 `COleObjectFactory` 派生自`CCmdTarget`和结果，它会记住在哪些模块状态中其实例化。 这一点很重要 — 当系统询问的类工厂创建对象，它现在知道哪些模块状态设为当前。

4. `DllGetClassObject` 调用以获取类工厂。 MFC 搜索与此模块相关联的类工厂列表，并将其返回。

5. 调用 `COleObjectFactory::XClassFactory2::CreateInstance`。 在创建对象并将其返回之前, 此函数的模块状态设置为在步骤 3 中的当前模块状态 (是最新的那个`COleObjectFactory`实例化)。 这是内部[METHOD_PROLOGUE](com-interface-entry-points.md)。

1. 创建对象后，它也是`CCmdTarget`衍生和相同的方式`COleObjectFactory`记住哪些模块状态已处于活动状态，此新对象也是如此。 现在，该对象知道要切换到哪种模块状态时调用。

1. 客户端上从它收到的 OLE COM 对象调用一个函数及其`CoCreateInstance`调用。 它使用时的对象称为`METHOD_PROLOGUE`就像切换模块状态`COleObjectFactory`does。

正如您所看到的模块状态将传播从对象到对象创建。 请务必将适当地设置模块状态。 如果未设置，DLL 或 COM 对象可能会与进行交互效果不佳的 MFC 应用程序在调用它，或可能找不到它自己的资源，或者其他感到痛苦的方式可能会失败。

请注意某些种类的 Dll，特别是"MFC 扩展"Dll 不会切换模块状态中的其`RawDllMain`(实际上，它们通常甚至没有`RawDllMain`)。 这是因为它们旨在""就像使用它们的应用程序中实际存在的行为。 它们是很大程度的正在运行的应用程序的一部分，其打算修改该应用程序的全局状态。

OLE 控件和其他 Dll 有很大差异。 他们不想修改调用应用程序的状态;在调用它们的应用程序甚至可能不是一个 MFC 应用程序，因此可能没有要修改状态。 这是发明时切换模块状态的原因。

导出函数的 DLL，如启动某一对话框在您的 DLL，需要将以下代码添加到函数的开头：

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

此交换当前模块状态与从返回的状态[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)结束前的当前作用域。

如果不使用 AFX_MODULE_STATE 宏，会出现问题的 Dll 中的资源。 默认情况下，MFC 使用主应用程序的资源句柄来加载资源模板。 此模板实际存储在 DLL 中。 根本原因是，不通过 AFX_MODULE_STATE 宏来切换 MFC 的模块状态信息时。 资源句柄将从 MFC 的模块状态中恢复。 不切换模块状态将导致使用错误的资源句柄。

AFX_MODULE_STATE 不需要将置于 DLL 中的每个函数。 例如，`InitInstance`因为 MFC 会自动切换模块状态之前可由未经 AFX_MODULE_STATE 的应用程序中的 MFC 代码调用`InitInstance`，然后将其切换回来后`InitInstance`返回。 同样适用于所有消息映射处理程序。 常规 MFC Dll 实际上有一个特殊的主窗口过程，路由任何消息之前将自动切换模块状态。

## <a name="process-local-data"></a>处理本地数据

处理本地数据不会这样严重问题它尚未 Win32s DLL 模型的难度。 在 Win32s 所有 Dll 都共享其全局数据，即使在多个应用程序加载时。 这是非常不同于"真实"Win32 DLL 数据模型，其中每个 DLL 获取其数据空间将附加到 DLL 的每个进程中的单独副本。 若要添加到复杂性，Win32s DLL 在堆上分配的数据实际上是特定过程 （至少为在不远所有权转）。 请考虑以下数据和代码：

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

请考虑如果上面的代码中位于在 DLL 中，通过 A 和 B （它，事实上，可以在同一应用程序的两个实例） 的两个进程加载的 DLL，会发生什么情况。 调用`SetGlobalString("Hello from A")`。 因此，分配的内存`CString`A.将保留在进程的上下文中的数据记住`CString`本身是全局而是对这两个一个可见和 b。现在，B 调用`GetGlobalString(sz, sizeof(sz))`。 B 将能够看到一组数据。 这是因为 Win32s 提供类似 Win32 执行的操作的进程之间无保护。 这就是第一个问题;在许多情况下不需要具有一个应用程序会影响被视为拥有的另一个应用程序的全局数据。

有其他问题。 假设现在退出。 一个退出时，所使用的内存`strGlobal`字符串可用于系统 — 即所有内存分配进程 A 由操作系统自动都释放。 它不会释放因为`CString`调用析构函数; 它在未尚未调用。 只需释放它因为分配给它的应用程序已离开场景。 现在，如果 B 调用`GetGlobalString(sz, sizeof(sz))`，它可能无法获得有效的数据。 其他一些应用程序可能使用了该内存用于其他用途。

清楚地存在问题。 MFC 3.x 使用一种称为线程本地存储 (TLS) 技术。 MFC 3.x 会分配一个 TLS 索引，它在 Win32s 实际上充当了一个进程本地存储区的索引，即使它不调用，然后将引用该 TLS 索引所基于的所有数据。 这是用于将线程本地数据存储在 Win32 上的 TLS 索引相似 （请参阅下面有关该主题的详细信息）。 这导致每个 MFC DLL，利用每个进程的至少两个 TLS 索引。 当您考虑加载多个 OLE 控件 Dll (Ocx) 时，则将快速用尽 TLS 索引 （有仅 64 可用）。 此外，MFC 必须将所有这些数据放在一个位置，在一个结构中。 它不是很强，并不是理想的 TLS 索引其使用方面。

MFC 4.x 解决此问题的一系列你可以"环绕"应是本地的过程的数据的类模板。 例如，可以通过编写解决上面提到的问题：

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

MFC 实现这两个步骤中。 首先，存在这一层基于 Win32 __Tls\*__  Api (**TlsAlloc**， **TlsSetValue**， **TlsGetValue**等) 的使用每个进程，无论有多少 Dll 的只有两个 TLS 索引。 第二个，`CProcessLocal`模板提供访问此数据。 它将替代运算符-> 这是允许直观如上所示的语法。 由包装的所有对象`CProcessLocal`必须派生自`CNoTrackObject`。 `CNoTrackObject` 提供低级分配器 (**LocalAlloc**/**LocalFree**) 和虚拟析构函数，以便 MFC 可自动销毁处理本地对象时的进程将终止。 此类对象可以自定义的析构函数，如果其他清除操作。 由于编译器将生成默认析构函数销毁嵌入上面的示例中不需要其中一个，`CString`对象。

还有其他有趣的优点，这种方法。 不只是所有`CProcessLocal`对象被自动销毁，它们不构造的需要。 `CProcessLocal::operator->` 将实例化第一次调用时，关联的对象和时间不早。 在上面的示例中，这意味着，'`strGlobal`' 字符串不会构造第一次之前`SetGlobalString`或`GetGlobalString`调用。 在某些情况下，这可以帮助减少 DLL 启动时间。

## <a name="thread-local-data"></a>线程本地数据

类似于处理本地数据，线程本地数据时使用的数据必须是本地的给定线程。 也就是说，对于每个线程访问该数据需要数据的单独实例。 这可以多次使用而不是广泛的同步机制。 如果数据不需要共享的多个线程，此类机制可能成本高昂且不必要。 假设我们有`CString`对象 （非常类似于上面的示例）。 我们可以保证其线程本地通过将其与包装`CThreadLocal`模板：

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

如果`MakeRandomString`调用从两个不同的线程，每个将"无序播放"该字符串以不同的方式而不会干扰其他。 这是因为没有实际`strThread`每个线程而不是只是一个全局实例的实例。

请注意如何使用的引用来捕获`CString`地址一次而不是一次每个循环迭代。 循环代码无法使用编写`threadData->strThread`无处不在`str`使用时，但代码会在执行过程中要慢得多。 最好是在循环中发生此类引用时缓存数据的引用。

`CThreadLocal`类模板使用相同的机制，`CProcessLocal`不，而且相同的实现技术。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
