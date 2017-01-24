---
title: "初始化扩展 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], 扩展"
  - "扩展 DLL [C++], 初始化"
  - "初始化 DLL"
ms.assetid: 08ad0381-3808-4bea-a93c-c9ba62496543
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 初始化扩展 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由于扩展 DLL 没有 `CWinApp` 派生对象（规则 DLL 有），应该将初始化代码和终止代码添加到“MFC DLL 向导”生成的 `DllMain` 函数中。  
  
 此向导为扩展 DLL 提供了下列代码。  在代码中，`PROJNAME` 是项目名的占位符。  
  
```  
#include "stdafx.h"  
#include <afxdllx.h>  
  
#ifdef _DEBUG  
#define new DEBUG_NEW  
#undef THIS_FILE  
static char THIS_FILE[] = __FILE__;  
#endif  
static AFX_EXTENSION_MODULE PROJNAMEDLL = { NULL, NULL };  
  
extern "C" int APIENTRY  
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)  
{  
   if (dwReason == DLL_PROCESS_ATTACH)  
   {  
      TRACE0("PROJNAME.DLL Initializing!\n");  
  
      // Extension DLL one-time initialization  
      AfxInitExtensionModule(PROJNAMEDLL,   
                                 hInstance);  
  
      // Insert this DLL into the resource chain  
      new CDynLinkLibrary(Dll3DLL);  
   }  
   else if (dwReason == DLL_PROCESS_DETACH)  
   {  
      TRACE0("PROJNAME.DLL Terminating!\n");  
   }  
   return 1;   // ok  
}  
```  
  
 通过在初始化期间创建新的 **CDynLinkLibrary** 对象，使扩展 DLL 可以将 `CRuntimeClass` 对象或资源导出到客户端应用程序。  
  
 如果打算从一个或多个规则 DLL 使用扩展 DLL，必须导出创建 **CDynLinkLibrary** 对象的初始化函数。  必须从每个使用扩展 DLL 的规则 DLL 调用此函数。  使用扩展 DLL 的任何导出类或函数之前，适合调用此初始化函数的位置是在规则 DLL 的 `CWinApp` 派生对象的 `InitInstance` 成员函数中。  
  
 在“MFC DLL 向导”生成的 `DllMain` 中，对 `AfxInitExtensionModule` 的调用捕获模块的运行时类（`CRuntimeClass` 结构）以及在创建 **CDynLinkLibrary** 对象时使用的对象工厂（`COleObjectFactory` 对象）。  应检查 `AfxInitExtensionModule` 的返回值；如果从 `AfxInitExtensionModule` 返回的是零值，则从 `DllMain` 函数返回零。  
  
 如果扩展 DLL 将显式链接到可执行文件（意味着可执行文件调用 `AfxLoadLibrary` 链接到此 DLL），应在 **DLL\_PROCESS\_DETACH** 上添加对 `AfxTermExtensionModule` 的调用。  此函数使 MFC 能够在每个进程与扩展 DLL 分离时（发生在进程退出时或由于 `AfxFreeLibrary` 调用而卸载 DLL 时）清除扩展 DLL。  如果扩展 DLL 将隐式链接到应用程序，则不需调用 `AfxTermExtensionModule`。  
  
 显式链接到扩展 DLL 的应用程序在释放 DLL 时必须调用 **AfxTermExtensionModule** 。  如果应用程序使用的是多线程，则它们还应使用 `AfxLoadLibrary` 和 `AfxFreeLibrary`（而不是 Win32 函数 **LoadLibrary** 和 **FreeLibrary**）。  使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` 可确保在加载和卸载扩展 DLL 时所执行的启动代码和关闭代码不会损坏全局 MFC 状态。  
  
 由于在调用 `DllMain` 时 MFCx0.dll 已被完全初始化，因此可以在 `DllMain` 内分配内存和调用 MFC 函数（与 16 位版本的 MFC 不同）。  
  
 扩展 DLL 可通过处理 `DllMain` 函数中的 **DLL\_THREAD\_ATTACH** 和 **DLL\_THREAD\_DETACH** 情况来负责多线程。  当线程附加到 DLL 和同 DLL 分离时，这些情况被传递到 `DllMain`。  附加 DLL 时调用 [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) 使得 DLL 得以为每个附加到此 DLL 的线程维护线程本地存储区 \(TLS\) 索引。  
  
 请注意，头文件 Afxdllx.h 包含扩展 DLL 中使用的结构的特殊定义，例如 `AFX_EXTENSION_MODULE` 和 **CDynLinkLibrary** 的定义。  应将此头文件包含在扩展 DLL 中。  
  
> [!NOTE]
>  既不定义也不取消定义 Stdafx.h 中的任何 \_AFX\_NO\_XXX 宏这一点非常重要。  有关更多信息，请参见知识库文章 Q140751“PRB: Problems Occur When Defining \_AFX\_NO\_XXX”（PRB：定义 \_AFX\_NO\_XXX 时出现的问题）。  可在 MSDN Library CD 或 [http:\/\/search.support.microsoft.com](http://search.support.microsoft.com/) 上找到知识库文章。  
  
 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的[在动态链接库中使用线程本地存储区](http://msdn.microsoft.com/library/windows/desktop/ms686997)中包含了一个处理多线程的初始化函数示例。  请注意，此示例包含一个名为 **LibMain** 的入口点函数，但不应将此函数命名为 `DllMain`，以便它能用于 MFC 和 C 运行库。  
  
 MFC 示例 [DLLHUSK](http://msdn.microsoft.com/zh-cn/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) 说明了初始化函数的使用。  
  
## 你希望做什么？  
  
-   [初始化规则 DLL](../build/initializing-regular-dlls.md)  
  
-   [初始化非 MFC DLL](../build/initializing-non-mfc-dlls.md)  
  
## 您想进一步了解什么？  
  
-   [C 运行库行为和 \_DllMainCRTStartup](../build/run-time-library-behavior.md)  
  
-   [在规则 DLL 中使用数据库、OLE 和套接字扩展 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [\<caps:sentence id\="tgt34" sentenceid\="58bb7328659bda9ffb73a1dcd39da06b" class\="tgtSentence"\>DllMain 的函数规范 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682583)  
  
-   [\<caps:sentence id\="tgt35" sentenceid\="f29344705c59343b34b642944921cbdf" class\="tgtSentence"\>动态链接库入口点函数 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682596)  
  
## 请参阅  
 [初始化 DLL](../build/initializing-a-dll.md)