---
title: "TN058：MFC 模块状态实现 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.implementation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], 模块状态"
  - "MFC [C++], 管理状态数据"
  - "模块状态 [C++], 管理状态数据"
  - "模块状态 [C++], 切换"
  - "进程状态 [C++]"
  - "线程状态 [C++]"
  - "TN058"
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN058：MFC 模块状态实现
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此技术声明介绍 MFC“模块状态”构造的实现。  使用模块状态执行的了解这一点十分重要的。使用来自 \(DLL 或 OLE 进程内服务器\) 共享 MFC 的 DLL。  
  
 在读取此注释前，请参见“管理 MFC 模块的状态数据”中的 [创建新的文档、窗口和视图](../mfc/creating-new-documents-windows-and-views.md)。  本文包含关键用法信息和概述有关此主题。  
  
## 概述  
 有三个 MFC 状态信息：模块状态、线程处理状态和状态。  有时这些状态类型可以合并。  例如，MFC 的句柄映射是模块本机和线程本地变量。  允许这两个模块在不同的映射它们的每个线程。  
  
 处理状态和线程状态类似。  这些数据项是传统上是全局变量的事物，但需要特定于特定进程或线程适当的 Win32s 支持的或不适宜的多线程支持的。  哪个类别特定数据项成为依赖于该项及其所需的语义与进程和线程边界。  
  
 模块状态的独特之处在于它可以包含正确处理本机或线程本机或声明全局状态。  此外，它可以快速切换。  
  
## 模块状态切换  
 每线程包含指针为“当前”或“活动”状态模块 \(毫不为奇，因为指针是 MFC 线程本地状态的一部分\)。  更改，当执行线程边界时模块传递，如应用程序调入一个 OLE 控件或 DLL 或一个 OLE 控件的回调入该指针应用程序。  
  
 当前模块状态通过调用 **AfxSetModuleState**开关。  在很大程度上，不直接处理 API。  MFC，大多数情况下，它将在您 \(OLE、WinMain 入口点、**AfxWndProc**等\)。这将在通过了解的静态链接中编写特殊的 **WndProc**中的任何组件执行和特定 `WinMain` \(或 `DllMain`\) 的模块状态应当前。  可以通过查看 DLLMODUL.CPP 或 APPMODUL.CPP 看到此代码在 MFC \\SRC 目录。  
  
 很少见要设置模块状态并将其设置为。  大多数时间要“按下”拥有模块状态作为当前消息，在执行后，然后“剩余”原始上下文返回。  这由宏 [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md) 和特殊类 **AFX\_MAINTAIN\_STATE**完成。  
  
 `CCmdTarget` 具有支持的模块状态切换特殊功能。  具体而言，`CCmdTarget` 是用于 OLE 自动化 COM 和 OLE 入口点类的根。  与公开的其他入口点对系统，这些入口点必须设置正确的模块状态。  特定 `CCmdTarget` 如何知道“右”模块状态应可接受？  回答是“记忆”哪些“当前”模块状态是构造，这样它将当前模块的状态设置为 DLL“记忆”值，则之后调用时。  因此，给定的 `CCmdTarget` 对象关联的模块状态是当前的模块状态，当在构造对象了。  将加载 INPROC 服务器，创建对象并调用其方法的简单示例。  
  
1.  使用 **LoadLibrary**，DLL 由 OLE 加载。  
  
2.  首先调用**RawDllMain**。  将模块状态到 DLL 的已知静态的模块状态。  因此 **RawDllMain** 静态链接到 DLL。  
  
3.  工厂的类构造函数与我们的对象调用。  `COleObjectFactory` 从 `CCmdTarget` 派生，因此，和在哪模块状态确保其实例化。  这很重要\)，以便类工厂创建请求对象时，现在它知道使当前的模块状态。  
  
4.  调用`DllGetClassObject` 以获取类工厂。  MFC 类工厂搜索列表与此模块并将其返回。  
  
5.  **COleObjectFactory::XClassFactory2::CreateInstance** 调用。  在创建对象并返回值之前，此函数将为当前模块状态在第 3 步中的模块状态 \(当前的版本，当 `COleObjectFactory` 实例化。\)  这会在 [METHOD\_PROLOGUE](../Topic/METHOD_PROLOGUE.md)中。  
  
6.  在创建对象时，也是确保的模块状态为活动的 `CCmdTarget` 派生对象和类似地，`COleObjectFactory`，因此执行此新的对象。  了解对象现在开关的哪模块状态，只要该调用。  
  
7.  客户端调用 COM 对象在接收 `CoCreateInstance` 从其调用 OLE 的函数。  当调用对象时它使用 `METHOD_PROLOGUE` 开关状态模块，如 `COleObjectFactory`。  
  
 您可以看到，模块状态从对象传送到对象，当创建它们。  重要的 let 模块状态正确设置。  如果未设置，DLL 或 COM 对象可以使用调用它的 MFC 应用程序的性能进行交互，或者可能无法找到它的资源可能会失败或其他凄惨的方式。  
  
 注意某些 DLL 类型，“MFC 扩展”DLL 专门切换其 **RawDllMain** 的模块状态 \(实际上，他们甚至通常没有 **RawDllMain**\)。  这是因为，它们旨在行为“，就像”them 实际上在使用它们的应用程序。  它们是，和是这些修改视图运行的应用程序的全局状态应用程序的一部分。  
  
 OLE 控件和其他 DLL 是截然不同。  他们不想修改调用应用程序的状态；调用这些过程的应用程序可能甚至不是 MFC 应用程序并因此无法在不修改状态。  这是原因模块状态切换时开发的。  
  
 如果从一个DLL中导出函数，例如启动在 DLL 的对话框的一个，需要以下代码添加到函数的开头：  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 这将交换当前模块状态，从[AfxGetStaticModuleState](../Topic/AfxGetStaticModuleState.md)状态返回到当前作用域结束。  
  
 如果`AFX_MODULE_STATE`宏没有使用会发生资源DLL中存在的问题。  默认情况下，MFC 使用主应用的资源句柄加载资源模板。  此模板实际存储在 DLL 。  根本原因是MFC的模块状态信息还没有被 `AFX_MODULE_STATE` 宏切换。  资源句柄从 MFC 的模块状态恢复。  不使转换模块状态导致使用错误的资源句柄。  
  
 `AFX_MODULE_STATE` 不需要放置到DLL的每个函数。  例如，`InitInstance` 可由应用程序的 MFC 代码调用，而无需 `AFX_MODULE_STATE`，因为在 `InitInstance`之前 MFC自动切换模块状态然后切回在 `InitInstance` 返回之后。  上述情况同样适用于所有消息映射处理程序。  规则DLL实际上有一个特殊的主窗口过程在路由的任何消息之前自动切换模块状态。  
  
## 处理本地数据  
 处理本地数据不是这样若优先没有 Win32s DLL 模型方面。  在 Win32s 所有 DLL 共享，全局数据中，即使由加载多个应用程序。  这非常不同“实际”Win32 DLL 数据模型不同，每个 DLL 在每个进程的数据获取空间单独副本附加到 DLL。  若要添加到复杂，在 Win32s DLL 堆分配的数据事实上是处理特定 \(至少，只要所有权为\)。  考虑以下数据和代码：  
  
```  
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
  
 先想想发生了什么事，如果上面的代码在 DLL 中，该 DLL 由两个进程加载 \(A 和 B，事实上，它可以是同一应用程序的两个实例。\)  调用 `SetGlobalString("Hello from A")`。  因此，内存为 `CString` 分配数据上下文 A. 进程中。  记住 `CString` 全局和可见为 A 和 B。  现在将调用 `GetGlobalString(sz, sizeof(sz))`。  B 中找到该设置的。的数据。  这是因为，Win32s 不提供进程间 \(如 Win32 的保护。  这是第一问题；在大多数情况下都视为由不同的应用程序拥有的应用程序会影响全局数据是不理想。  
  
 有其他问题。  假定 A 立即退出。  当退出 A 时，'`strGlobal`' 使用的字符串的内存可用于系统，即分配的所有内存处理 A 由操作系统自动释放。  因为 `CString` 析构函数调用，则不会发布；尚未调用。  它将被释放，因为分配该应用程序退出的区域。  现在，如果 B 调用 `GetGlobalString(sz, sizeof(sz))`，它可能无法获取有效数据。  其他应用程序可能以其他使用了该内存。  
  
 显然存在问题。  MFC 3.x 使用名为线程本地存储的技术 \(TLS\)。  MFC 3.x 将分配 Win32s 实际上是进程。下本地存储索引的 TLS，索引，即使未将该调用引用基于该 TLS 索引的所有数据。  这类似于用于存储上的 Win32 线程本地数据的索引 \(TLS 下面参见有关该主题的更多信息。\)  这使每 MFC DLL 使用每进程至少两 TLS 索引。  当您考虑多加载的 DLL \(OCXs OLE 控件\)，您很快就会用完所有索引 \(TLS 只有 64 可用\)。  此外，MFC 都必须在一个地方放置所有这些数据，一个结构中。  它不非常易于扩展并不是所需的实例与使用索引 \(它的使用。  
  
 MFC 4.x 解决此与一组您可以“在数据环绕”应为处理本机类模板。  例如，上述问题可以通过编写解决：  
  
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
  
 MFC 实现这一点。两个步骤。  首先，则层在仅使用两个索引的每个进程 \(Win32 API **Tls\*** \(**TlsAlloc**、**TlsSetValue**、**TlsGetValue**、\) 的顶部，即，而不论涉及多少 DLL 有。  接下来，提供模板 `CProcessLocal` 访问此数据。  它重写\> 的运算符是。可以看到上面的语法直观。  由 `CProcessLocal` 包装的对象必须派生自 `CNoTrackObject`。  为自`CNoTrackObject` 分配器 \(**LocalAlloc**\/**LocalFree**\) 和虚析构函数的 MFC 可自动销毁处理本地对象，在进程停止时。  如果需要，这些对象可以具有自定义析构函数的额外清除。  因为编译器将生成默认析构函数销毁嵌入在其中的 `CString` 对象，上面示例不需要。  
  
 有其他有趣的优势。此方法。  不仅自动销毁所有 `CProcessLocal` 对象，则不会构造之前，他们需要的。  速度将实例化`CProcessLocal::operator->` 对象关联，首次调用，而不是。  在上面的示例中，该 '`strGlobal`' 意味着字符串第一次不会构造直到调用 **SetGlobalString** 或 **GetGlobalString**。  在某些情况下，这有助于减小 DLL 启动时间。  
  
## 线程本地数据  
 当数据必须是本地的。特定线程时，类似于处理本地数据，线程本地数据。  即需要数据的单独实例用于访问该数据的每个线程。  这可能多次代替大量同步机制。  如果不需要数据被多个线程共享，这样的机制可能非常昂贵和不必要的。  假设有一个 `CString` 对象 \(就像上例\)。  我们可以将它使其成为线程本地使用 `CThreadLocal` 模板：  
  
```  
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
      randErr = rand_s( &randomNumber );  
      if ( randErr == 0 )  
      {  
         TCHAR ch = randomNumber % 52 + 1;  
         if (str.Find(ch) < 0)  
            str += ch; // not found, add it  
      }  
   }  
}  
```  
  
 如果 `MakeRandomString` 同时从不同线程调用，其中每个“将随机选择”字符串不同的方式，而不干扰。  这是因为，每个线程实际上有一个 `strThread` 实例而非全局实例。  
  
 说明如何一次引用用于捕获 `CString` 地址而不是一次每个循环迭代。  循环可以编写程序使用在 `threadData->strThread` '`str`' 使用，但是，代码是慢在执行。  当这种引用循环中时，会缓存对数据的引用是最佳的。  
  
 `CThreadLocal` 类模板使用相同的机制和 `CProcessLocal` 执行同样实现方法。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)