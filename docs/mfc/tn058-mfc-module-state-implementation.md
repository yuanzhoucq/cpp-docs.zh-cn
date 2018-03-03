---
title: "TN058: MFC 模块状态实现 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.implementation
dev_langs:
- C++
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed7bc195c771026ff3e58d53f9e3936791810e76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058：MFC 模块状态实现
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此技术说明描述 MFC"模块状态"构造的实现。 模块状态实现了解至关重要，使用 MFC 共享的 DLL 中的 Dll （或 OLE 进程内服务器）。  
  
 在阅读本说明之前, 请参考"的 MFC 模块中管理状态数据"中的[创建新文档、 窗口和视图](../mfc/creating-new-documents-windows-and-views.md)。 本文包含重要的使用情况信息和有关此主题的概述信息。  
  
## <a name="overview"></a>概述  
 有三种类型的 MFC 状态信息： 模块状态、 过程状态和线程状态。 有时可以组合这些状态类型。 例如，MFC 的句柄映射是本地的模块和本地的线程。 这允许两个不同的模块，若要在其线程的每个具有不同的映射。  
  
 进程状态和线程状态很相似。 这些数据项几点传统上已全局变量，但需要是特定于给定进程或线程正确 Win32s 支持或正确的多线程处理支持。 给定的数据项所能容纳的类别取决于该项目和进程和线程边界与其所需的语义。  
  
 模块状态是唯一的因为它可以包含真正全局状态或是本地的进程或线程本地的状态。 此外，它可以切换快速。  
  
## <a name="module-state-switching"></a>切换模块状态  
 每个线程包含"当前"或"活动"的模块状态的指针 （毫无疑问，该指针是 MFC 的线程本地状态的一部分）。 此指针会更改执行的线程将传递模块边界，例如调入 OLE 控件或 DLL 或 OLE 控件回调到应用程序的应用程序。  
  
 将当前模块状态切换通过调用**AfxSetModuleState**。 大多数情况下，你将永远不会处理直接使用 API。 MFC 中，在许多情况下，将调用它为你 (WinMain，OLE 的入口点，在**AfxWndProc**等。)。 这是你编写在一个特殊静态链接的任何组件中**WndProc**，和一个特殊`WinMain`(或`DllMain`) 知道哪些模块状态应为当前。 你可以通过查看 DLLMODUL 看到此代码。CPP 或 APPMODUL。CPP MFC\SRC 目录中。  
  
 很少你想要设置的模块状态，然后不返回设置。 大多数情况下你想要"push"你自己的模块与当前状态，然后，完成后，"pop"回原始上下文。 这通过宏[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)和特殊类**AFX_MAINTAIN_STATE**。  
  
 `CCmdTarget`具有特殊功能支持切换模块状态。 具体而言，`CCmdTarget`是根类使用 OLE 自动化和 OLE COM 入口点。 像任何其他入口点向系统公开，这些入口点必须设置正确的模块状态。 如何未给定`CCmdTarget`知道"正确"的模块状态应该是什么问题的回答是它"记住"的"当前"的模块状态时，是什么构造它，以便它可以设置与当前模块状态"记住"值更高版本时调用。 因此，该模块状态，给定`CCmdTarget`对象所关联与对象构造的时使用的当前模块状态。 举一个简单例子加载 INPROC 服务器、 创建的对象，并调用其方法。  
  
1.  通过 OLE 加载该 DLL 使用**LoadLibrary**。  
  
2. **RawDllMain**都会首先调用。 它将该 DLL 的模块状态设置为已知的静态模块状态。 出于此原因**RawDllMain**静态链接到 DLL。  
  
3.  调用与我们对象相关联的类工厂的构造函数。 `COleObjectFactory`派生自`CCmdTarget`和结果，它会记住在哪些模块状态中其实例化。 这一点很重要，当系统询问类工厂来创建对象，它现在知道要设置为当前哪些模块状态。  
  
4. `DllGetClassObject`调用以获取类工厂。 MFC 搜索与此模块关联的类工厂列表，并返回它。  
  
5. **COleObjectFactory::XClassFactory2::CreateInstance**调用。 在创建对象并将其返回之前, 此函数的模块状态设置为在步骤 3 中的当前模块状态 (是最新的一个`COleObjectFactory`实例化)。 这是内部的[METHOD_PROLOGUE](com-interface-entry-points.md)。  
  
6.  创建对象，它也是`CCmdTarget`派生和相同的方式`COleObjectFactory`记住的模块状态处于活动状态，也将此新的对象。 现在对象知道要切换到哪种模块状态时调用。  
  
7.  客户端在收到来自 OLE 和 COM 对象上调用一个函数其`CoCreateInstance`调用。 当该对象调用它会使用`METHOD_PROLOGUE`就像切换模块状态`COleObjectFactory`未。  
  
 如你所见，模块状态将传播从对象到对象创建时。 请务必具有适当地设置的模块状态。 如果未设置，你的 DLL 或 COM 对象可能会不佳交互的 MFC 应用程序在调用它，或可能找不到其自己的资源，或者其他痛苦方式可能会失败。  
  
 请注意某些种类的 Dll，专门"MFC 扩展"Dll 不会切换模块状态中的其**RawDllMain** (实际上，它们通常甚至没有**RawDllMain**)。 这是因为它们旨在以不同的""就像使用它们的应用程序中实际存在。 它们是很大程度的应用程序正在运行的一部分，其打算修改该应用程序的全局状态。  
  
 OLE 控件和其他 Dll 有很大不同。 它们不想修改调用应用程序的状态;应用程序调用它们甚至可能不是 MFC 应用程序，所以可能没有要修改状态。 这是已发明了切换模块状态的原因。  
  
 从 DLL，例如启动对话框中您的 DLL 中导出的函数，你需要将以下代码添加到函数的开头：  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState())  
```  
  
 此交换与从返回的状态将当前模块状态[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)直至当前范围的末尾。  
  
 如果未使用 `AFX_MODULE_STATE` 宏，则 DLL 中将产生资源问题。 默认情况下，MFC 使用主应用程序的资源句柄来加载资源模板。 此模板实际存储在 DLL 中。 根本原因是 `AFX_MODULE_STATE` 宏尚未切换 MFC 的模块状态信息。 资源句柄将从 MFC 的模块状态中恢复。 不切换模块状态将导致使用错误的资源句柄。  
  
 `AFX_MODULE_STATE`不需要置于 DLL 中的每个函数。 例如，`InitInstance` 可由应用程序中的 MFC 代码调用，而无需 `AFX_MODULE_STATE`，因为 MFC 会在 `InitInstance` 之前自动切换模块状态，然后在 `InitInstance` 返回之后将其切换回来。 同样适用于所有消息映射处理程序。 常规 MFC Dll 实际上有一个特殊的主窗口过程，在路由任何消息之前自动切换模块状态。  
  
## <a name="process-local-data"></a>处理本地数据  
 处理本地数据并不是此类让人担心它尚未为 Win32s DLL 模型很难中。 在 Win32s 所有 Dll 都共享其全局数据，即使由多个应用程序加载。 这是非常不同的"真实"Win32 DLL 数据模型，其中每个 DLL 获取其每个进程，将附加到该 DLL 中的数据空间的单独副本。 若要添加到复杂性，Win32s DLL 中的堆上分配的数据实际上是特定过程 （至少只要才归）。 请考虑以下数据和代码：  
  
```  
static CString strGlobal; // at file scope  
 
__declspec(dllexport)   
void SetGlobalString(LPCTSTR lpsz)  
{  
    strGlobal = lpsz;  
}  
 
__declspec(dllexport)  
void GetGlobalString(LPCTSTR lpsz,
    size_t cb)  
{  
    StringCbCopy(lpsz,
    cb,
    strGlobal);

}  
```  
  
 请考虑如果上面的代码将在位于在 DLL 中并由 A 和 B （它，事实上，可以同一个应用程序的两个实例） 的两个进程加载 DLL 会发生什么情况。 调用`SetGlobalString("Hello from A")`。 因此，为分配内存`CString`A.将保留在进程的上下文中的数据记住，`CString`本身是全局设置，可见到这两个 A 和 b。现在，B 调用`GetGlobalString(sz, sizeof(sz))`。 B 将能够看到一组的数据。 这是因为 Win32s 提供类似 Win32 执行的操作的进程之间无保护。 第一个出现问题;在许多情况下不需要将会影响被视为拥有的不同应用程序的全局数据的一个应用程序。  
  
 有其他问题。 让我们假设现在退出。 A 退出时，使用的内存`strGlobal`字符串将可供系统-即，所有进程 A 所分配的内存由操作系统自动都释放。 它不会释放因为`CString`调用析构函数; 尚未尚未被调用。 只需释放因为分配它的应用程序已离开场景。 现在，如果 B 调用`GetGlobalString(sz, sizeof(sz))`，它可能无法获得有效的数据。 某个其他应用程序可能使用的内存用于其他用途。  
  
 清楚地存在问题。 MFC 3.x 使用名为线程本地存储 (TLS) 的技术。 MFC 3.x 将分配一个 TLS 索引，它在 Win32s 真正充当一个进程本地存储区的索引，即使它不调用，然后将引用该 TLS 索引所基于的所有数据。 它类似于用于在 Win32 上存储线程本地数据的 TLS 索引 （请参阅下面有关该主题的详细信息）。 这将导致每个 MFC DLL 利用每个进程的至少两个 TLS 索引。 当你考虑到加载多个 OLE 控件 Dll （ocx 文件） 时，则将快速用尽 TLS 索引 （有可用的仅 64）。 此外，MFC 必须将所有这些数据放在单个结构中的一个位置。 它不是非常可扩展并不是理想的 TLS 索引其使用方面。  
  
 MFC 4.x 解决此问题与一组你可以"环绕"应是本地的过程的数据的类模板。 例如，可以通过编写修复上面提到的问题：  
  
```  
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
  
 MFC 实现这两个步骤中。 首先，将一个层，Win32 **Tls\***  Api (**TlsAlloc**， **TlsSetValue**， **TlsGetValue**等) 的使用每个进程，无论多少 Dll 必须仅有两个 TLS 索引。 第二个，`CProcessLocal`模板可用于访问此数据。 重写运算符-> 这是什么允许上面的直观语法。 通过包装的所有对象`CProcessLocal`必须派生自`CNoTrackObject`。 `CNoTrackObject`提供一个较低级别的分配器 (**LocalAlloc**/**LocalFree**) 和虚拟的析构函数，以便该进程时，MFC 自动可以销毁进程本地对象终止。 此类对象可以包含自定义的析构函数，前提是必需的附加清理。 上面的示例中不要求获得密码，因为编译器将生成默认析构函数销毁嵌入`CString`对象。  
  
 有这种方法其他有趣优点。 不只是所有`CProcessLocal`对象销毁自动，它们不构造的需要。 `CProcessLocal::operator->`将实例化第一次调用时，关联的对象并不会更快。 在上面的示例中，这意味着，`strGlobal`第一次之前不会构造字符串**SetGlobalString**或**GetGlobalString**调用。 在某些情况下，这可以帮助减少 DLL 启动时间。  
  
## <a name="thread-local-data"></a>线程本地数据  
 类似于处理本地数据，线程本地数据时使用的数据必须是本地的给定线程。 也就是说，你需要访问该数据的每个线程数据的单独实例。 这可以多次使用而不是广泛的同步机制。 如果数据并不需要由多个线程共享，此类的机制可能成本高昂且不必要。 假设我们有`CString`（非常类似于上面的示例） 的对象。 我们可以通过使该线程本地包装在与`CThreadLocal`模板：  
  
```  
struct CMyThreadData : public CNoTrackObject  
{  
    CString strThread;  
};  
CThreadLocal<CMyThreadData> threadData;  
 
void MakeRandomString()  
{ *// a kind of card shuffle (not a great one)  
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
  
 如果`MakeRandomString`调用从两个不同的线程，每个将"随机排列"字符串以不同的方式而不会干扰其他。 这是因为没有实际`strThread`每个线程而不是一个全局实例的实例。  
  
 请注意如何使用的引用来捕获`CString`地址一次而不是一次每个循环迭代。 循环代码无法使用编写`threadData->strThread`everywhere`str`使用时，但该代码会在执行过程中要慢得多。 最好在循环中发生这种引用时缓存对数据的引用。  
  
 `CThreadLocal`类模板使用相同的机制，`CProcessLocal`功能以及相同的实现方法。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

