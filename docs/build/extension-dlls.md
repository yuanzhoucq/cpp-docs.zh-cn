---
title: "扩展 Dll |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: afxdll
dev_langs: C++
helpviewer_keywords:
- memory [C++], DLLs
- MFC extension DLLs [C++]
- AFXDLL library
- shared resources [C++]
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- resource sharing [C++]
- extension DLLs [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: f69ac3d4-e474-4b1c-87a1-6738843a135c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 45e94997dbeb2c6413ffcdc1272a3a46a7e220ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-extension-dlls"></a>MFC 扩展 Dll
MFC 扩展 DLL 是通常实现从现有的 Microsoft 基础类库类派生的可重用类的 DLL。  
  
 MFC 扩展 DLL 具有以下功能和要求：  
  
-   客户端可执行文件必须是 MFC 应用程序使用编译`_AFXDLL`定义。  
  
-   MFC 扩展 DLL 还可通过动态链接到 MFC 常规 MFC DLL。  
  
-   应使用编译 MFC 扩展 Dll`_AFXEXT`定义。 这将强制`_AFXDLL`还定义，并确保从 MFC 标头文件的适当声明拉入。 它还确保`AFX_EXT_CLASS`定义为`__declspec(dllexport)`时生成 DLL，这是必需的如果你使用此宏来声明 MFC 扩展 DLL 中的类。  
  
-   MFC 扩展 Dll 不应实例化的类派生自`CWinApp`，但应依赖于客户端应用程序 （或 DLL），以提供此对象。  
  
-   但是，提供 MFC 扩展 Dll 后，应该`DllMain`函数，并且是否那里任何必要的初始化。  
  
 扩展 Dll 是使用 MFC （也称为 MFC 的共享版本） 的动态链接库版本生成的。 仅 MFC 可执行文件 （应用程序或 MFC 的规则 Dll） 使用共享版本的 MFC 生成可以使用 MFC 扩展 DLL。 客户端应用程序和 MFC 扩展 DLL 必须使用相同版本的 MFCx0.dll。 MFC 扩展 DLL，可以从 MFC 派生新的自定义类，然后提供此扩展的版本的 MFC 应用程序调用 DLL。  
  
 扩展 Dll 还可用于应用程序和 DLL 之间传递 MFC 派生的对象。 在其中创建对象的模块中存在与传递的对象关联的成员函数。 由于使用 MFC 的共享的 DLL 版本时，这些函数将正确导出，你可以自由地传递 MFC 或应用程序和 MFC 扩展 Dll 加载之间的 MFC 派生的对象指针。  
  
 MFC 扩展 DLL 使用共享的版本的 MFC 应用程序使用的共享的 DLL 版本的 MFC 中，有几个额外的注意事项的方式相同：  
  
-   它不具有`CWinApp`-派生对象。 它必须使用`CWinApp`-派生对象的客户端应用程序。 这意味着客户端应用程序拥有的主消息泵，空闲循环中，依次类推。  
  
-   它调用`AfxInitExtensionModule`中其`DllMain`函数。 应检查此函数的返回值。 如果从返回零值`AfxInitExtensionModule`，返回从 0 你`DllMain`函数。  
  
-   它将创建**CDynLinkLibrary**对象在初始化期间，如果 MFC 扩展 DLL 要导出`CRuntimeClass`对象或对应用程序的资源。  
  
 之前版本的 MFC 4.0，这种类型的 DLL 调用了 AFXDLL。 AFXDLL 指`_AFXDLL`生成 DLL 时定义的预处理器符号。  
  
 按照中所述的约定命名共享版本的 MFC 导入库[MFC Dll 命名约定](../build/naming-conventions-for-mfc-dlls.md)。 Visual c + + 提供 MFC Dll 和一个数字的非 MFC Dll，你可以使用和你的应用程序一起分发的预构建的的版本。 这些记录在 Redist.txt，安装到 Program Files\Microsoft Visual Studio 文件夹中。  
  
 如果你要导出使用.def 文件，在起点和标头文件的末尾将以下代码：  
  
```cpp  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
 这四行确保你的代码已正确编译 MFC 扩展 DLL。 省去这四个行可能会导致 DLL 来编译或链接不正确。  
  
 如果你需要传递 MFC 或 MFC 派生的对象指针是指向还是从 MFC DLL，DLL 应为 MFC 扩展 DLL。 在其中创建对象的模块中存在与传递的对象关联的成员函数。 由于使用 MFC 的共享的 DLL 版本时，这些函数将正确导出，你可以自由地传递 MFC 或应用程序和 MFC 扩展 Dll 加载之间的 MFC 派生的对象指针。  
  
 由于 c + + 名称重整以及导出的问题，导出文件列表中的从 MFC 扩展 DLL 可能不同同一 DLL 的调试和发布版本和 Dll 之间针对不同的平台。 零售 MFCx0.dll 已大约 2000 导出入口点;调试 MFCx0D.dll 具有约 3000 名导出的入口点。  
  
## <a name="memory-management"></a>内存管理  
 MFCx0.dll 和所有 MFC 扩展 Dll 加载到客户端应用程序的地址空间可以使用相同的内存分配器、 资源加载和其他 MFC 全局状态，就像它们是在同一应用程序。 这很重要，因为非 MFC DLL 库和规则的 MFC Dll 不精确求反，并且具有其自己的内存池之外分配每个 DLL。  
  
 MFC 扩展 DLL 分配内存，如果该内存能够随便与任何其他应用程序分配的对象。 此外，如果动态链接到 MFC 的应用程序失败，操作系统保护维护共享 DLL 任何其他 MFC 的应用程序的完整性。  
  
 同样其他全局的 MFC 状态，类似于当前的可执行文件加载资源，还为客户端应用程序和所有 MFC 扩展 Dll，以及 MFCx0.dll 本身之间共享。  
  
## <a name="sharing-resources-and-classes"></a>共享资源和类  
 导出资源均通过的资源列表。 每个应用程序包含单向链表的**CDynLinkLibrary**对象。 在查看资源时，大部分加载资源的标准 MFC 实现应当首先查看当前的资源模块 (`AfxGetResourceHandle`) 如果未找到资源和引导的列表**CDynLinkLibrary**对象尝试加载请求的资源。  
  
 遍历列表也有缺点，它会稍慢些，并需要管理资源 ID 范围。 它具有链接到多个 MFC 扩展 Dll 的客户端应用程序可以使用任何 DLL 提供的资源，而无需指定 DLL 实例句柄的优势。 `AfxFindResourceHandle`是一个 API 用于遍历资源列表以查找给定的匹配项。 它采用的名称和类型的资源，并返回的第一次找的资源句柄 （或 NULL）。  
  
 如果你不想要浏览列表，而仅从特定的位置加载资源，使用函数`AfxGetResourceHandle`和`AfxSetResourceHandle`保存旧句柄并设置新的句柄。 请确保还原旧资源句柄，然后返回到客户端应用程序。 使用此方法以显式加载菜单的示例，请参阅 MFC 示例中的 Testdll2.cpp [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)。  
  
 动态创建的 MFC 对象 MFC 名称是类似的。 MFC 对象反序列化机制需要具有的所有`CRuntimeClass`对象注册，以便它可以重新构造通过动态创建基于以前存储的内容所需类型的 c + + 对象。  
  
 在 MFC 示例[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)，列表如下所示：  
  
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
  
 其中*xx*是版本号; 例如，42 表示版本 4.2。  
  
 MFCxx.dll 是通常的最后一个的资源和类列表。 MFCxx.dll 包括所有标准 MFC 资源，包括所有标准命令 Id 的提示字符串。 将其放在列表末尾允许 Dll 和客户端应用程序本身不能使用他们自己的副本的标准 MFC 资源，而是改为依赖于 MFCxx.dll 中的共享资源。  
  
 资源和类名称的所有 Dll 合并到客户端应用程序的命名空间具有需要您要注意哪些 Id 或你选择的名称的缺点。  
  
 [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)示例通过使用多个标头文件来管理共享的资源命名空间。  
  
 如果你的 MFC 扩展 DLL 需要维护每个应用程序的额外数据，你可以派生新类从**CDynLinkLibrary**并创建在`DllMain`。 DLL 运行时，可以检查当前应用程序的列表的**CDynLinkLibrary**要查找该特定的 MFC 扩展 DLL 的一个对象。  
  
### <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [初始化 MFC 扩展 DLL](../build/run-time-library-behavior.md#initializing-extension-dlls)  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [使用共享的资源文件的提示](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)  
  
-   [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)  
  
-   [静态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [动态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [在规则 MFC DLL 中使用数据库、OLE 和套接字 MFC 扩展 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
## <a name="see-also"></a>请参阅  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)