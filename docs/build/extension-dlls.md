---
title: "扩展 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "afxdll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFXDLL 库"
  - "DLL [C++], 扩展"
  - "扩展 DLL [C++]"
  - "扩展 DLL [C++], 关于扩展 DLL"
  - "内存 [C++], DLL"
  - "MFC DLL [C++], 扩展 DLL"
  - "MFC 扩展 DLL [C++]"
  - "资源共享 [C++]"
  - "共享的 DLL 版本 [C++]"
  - "共享的资源 [C++]"
ms.assetid: f69ac3d4-e474-4b1c-87a1-6738843a135c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 扩展 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 扩展 DLL 是通常实现从现有 Microsoft 基础类库类派生的可重用类的 DLL。  
  
 MFC 扩展 DLL 具有下列功能和要求：  
  
-   客户端可执行文件必须是用定义的 **\_AFXDLL** 编译的 MFC 应用程序。  
  
-   扩展 DLL 也可由动态链接到 MFC 的规则 DLL 使用。  
  
-   扩展 DLL 应该用定义的 `_AFXEXT` 编译。  这将强制同时定义 **\_AFXDLL**，并确保从 MFC 头文件中拉入正确的声明。  它也确保了在生成 DLL 时将 **AFX\_EXT\_CLASS** 定义为 **\_\_declspec\(dllexport\)**，这在使用此宏声明扩展 DLL 中的类时是必要的。  
  
-   扩展 DLL 不应实例化从 `CWinApp` 派生的类，而应依赖客户端应用程序（或 DLL）提供此对象。  
  
-   但扩展 DLL 应提供 `DllMain` 函数，并在那里执行任何必需的初始化。  
  
 扩展 DLL 是使用 MFC 动态链接库版本（也称作共享 MFC 版本）生成的。  只有用共享 MFC 版本生成的 MFC 可执行文件（应用程序或规则 DLL）才能使用扩展 DLL。  客户端应用程序和扩展 DLL 必须使用相同版本的 MFCx0.dll。  使用扩展 DLL，可以从 MFC 派生新的自定义类，然后将此“扩展”版本的 MFC 提供给调用 DLL 的应用程序。  
  
 扩展 DLL 也可用于在应用程序和 DLL 之间传递 MFC 派生的对象。  与已传递的对象关联的成员函数存在于创建对象所在的模块中。  由于在使用 MFC 的共享 DLL 版本时正确导出了这些函数，因此可以在应用程序和它加载的扩展 DLL 之间随意传递 MFC 或 MFC 派生的对象指针。  
  
 MFC 扩展 DLL 使用共享 MFC 版本的方式与应用程序使用 MFC 的共享 DLL 版本的方式相同，但有另外几点需要注意的事项：  
  
-   它没有 `CWinApp` 派生对象。  它必须与客户端应用程序的 `CWinApp` 派生对象一起使用。  这意味着客户端应用程序拥有主消息泵、空闲循环等。  
  
-   它在自己的 `DllMain` 函数中调用 `AfxInitExtensionModule`。  应检查此函数的返回值。  如果从 `AfxInitExtensionModule` 返回的是零值，则从 `DllMain` 函数返回 0。  
  
-   如果扩展 DLL 希望将 `CRuntimeClass` 对象或资源导出到应用程序中，它将在初始化期间创建一个 **CDynLinkLibrary** 对象。  
  
 在 MFC 4.0 版之前，这类 DLL 称作 AFXDLL。  AFXDLL 引用生成 DLL 时定义的 **\_AFXDLL** 预处理器符号。  
  
 共享版本 MFC 的导入库的命名依据 [MFC DLL 命名约定](../build/naming-conventions-for-mfc-dlls.md)中描述的约定。  Visual C\+\+ 提供预生成的 MFC DLL 版本，以及若干可以使用并用应用程序发布的非 MFC DLL。  它们记录在安装到 Program Files\\Microsoft Visual Studio 文件夹的 Redist.txt 中。  
  
 如果要使用 .def 文件导出，请在头文件的开始和结尾处放置下列代码：  
  
```  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
 这四行确保为扩展 DLL 正确编译代码。  省去这四行可能导致 DLL 不能正确地编译或链接。  
  
 如果需要与 MFC DLL 来回传递 MFC 或 MFC 派生对象的指针，DLL 应为扩展 DLL。  与已传递的对象关联的成员函数存在于创建对象所在的模块中。  由于在使用 MFC 的共享 DLL 版本时正确导出了这些函数，因此可以在应用程序和它加载的扩展 DLL 之间随意传递 MFC 或 MFC 派生的对象指针。  
  
 由于存在 C\+\+ 名称重整和导出问题，在同一 DLL 的调试版本和零售版本及用于不同平台的 DLL 之间，扩展 DLL 中的导出列表可能不同。  零售版本的 MFCx0.dll 有大约 2,000 个导出入口点；调试版本的 MFCx0D.dll 有大约 3,000 个导出入口点。  
  
## 内存管理  
 MFCx0.dll 和所有加载到客户端应用程序的地址空间中的扩展 DLL 使用相同的内存分配器、资源加载和其他 MFC“全局”状态，就好像它们在同一个应用程序中一样。  这一点意义重大，因为非 MFC DLL 库和规则 DLL 正好相反，它们让每个 DLL 在各自的内存池之外分配。  
  
 如果扩展 DLL 分配内存，则该内存能够随意与任何其他应用程序分配的对象相混合。  同时，如果动态链接到 MFC 的应用程序失败，操作系统的保护将维护共享 DLL 的任何其他 MFC 应用程序的完整性。  
  
 同样，其他“全局”MFC 状态（如从中加载资源的当前可执行文件）也在客户端应用程序与 MFCx0.dll 本身以及所有 MFC 扩展 DLL 之间共享。  
  
## 共享资源和类  
 导出资源的操作是通过资源列表完成的。  每个应用程序均包含 **CDynLinkLibrary** 对象的单向链接表。  查找资源时，大部分加载资源的标准 MFC 实现首先查看当前资源模块 \(`AfxGetResourceHandle`\)，如果未找到资源，则浏览 **CDynLinkLibrary** 对象的列表，并尝试加载请求的资源。  
  
 浏览列表的做法有一些缺点，即速度稍慢且需要管理资源 ID 范围。  它的优点在于，链接到几个扩展 DLL 的客户端应用程序可以使用 DLL 提供的任何资源，而无需指定 DLL 实例句柄。  `AfxFindResourceHandle` 是用于浏览资源列表以查找给定匹配的 API。  它采用资源的名称和类型，并从最先找到匹配项的位置返回资源句柄（或 NULL）。  
  
 如果不想浏览列表，而是仅从特定的位置加载资源，请使用函数 `AfxGetResourceHandle` 和 `AfxSetResourceHandle` 保存旧句柄和设置新句柄。  返回到客户端应用程序之前，请务必还原旧资源句柄。  有关使用此方法显式加载菜单的示例，请参见 MFC 示例 [DLLHUSK](http://msdn.microsoft.com/zh-cn/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) 中的 Testdll2 .cpp。  
  
 动态创建给定了 MFC 名称的 MFC 对象与此类似。  MFC 对象反序列化机制需要注册所有的 `CRuntimeClass` 对象，以便可以通过基于以前存储的内容动态创建所需类型的 C\+\+ 对象来重新构造。  
  
 在 MFC 示例 [DLLHUSK](http://msdn.microsoft.com/zh-cn/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) 中，此列表的形式如下：  
  
```  
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE  
               |                      |  
          TESTDLL2.DLL           TESTDLL2.DLL  
               |                      |  
          TESTDLL1.DLL           TESTDLL1.DLL  
               |                      |  
           MFCOxxD.DLL                |  
               |                      |  
           MFCDxxD.DLL                |  
               |                      |  
            MFCxxD.DLL            MFCxx.DLL  
```  
  
 其中 *xx* 是版本号；例如 42 表示 4.2 版。  
  
 MFCxx.dll 通常排在资源和类列表的最后。  MFCxx.dll 包含所有的标准 MFC 资源，其中包括所有标准命令 ID 的提示字符串。  将 MFCxx.dll 放在列表的最后使得 DLL 和客户端应用程序本身不必有自己的标准 MFC 资源副本，而是可以依赖 MFCxx.dll 中的共享资源。  
  
 将所有 DLL 的资源名和类名合并到客户端应用程序的命名空间中，这种做法的缺点是需要小心选取 ID 或名称。  
  
 [DLLHUSK](http://msdn.microsoft.com/zh-cn/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) 示例通过使用多个头文件来管理共享资源命名空间。  
  
 如果 MFC 扩展 DLL 需要为每个应用程序维护额外的数据，可从 **CDynLinkLibrary** 派生一个新类并在 `DllMain` 中创建此类。  运行时，DLL 会检查当前应用程序的 **CDynLinkLibrary** 对象列表，以查找用于特定扩展 DLL 的对象。  
  
### 你希望做什么？  
  
-   [初始化扩展 DLL](../build/initializing-extension-dlls.md)  
  
### 您想进一步了解什么？  
  
-   [关于使用共享资源文件的提示](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)  
  
-   [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)  
  
-   [静态链接到 MFC 的规则 DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [动态链接到 MFC 的规则 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [在规则 DLL 中使用数据库、OLE 和套接字扩展 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)