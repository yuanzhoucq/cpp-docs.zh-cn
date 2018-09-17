---
title: 扩展 Dll |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- afxdll
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62bb287cca78875bf6c3ad11f426b23db3b6f7e1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718064"
---
# <a name="mfc-extension-dlls"></a>MFC 扩展 Dll

MFC 扩展 DLL 是通常实现从现有的 Microsoft 基础类库类派生的可重用类的 DLL。

MFC 扩展 DLL 具有以下功能和要求：

- 客户端可执行文件必须与编译的 MFC 应用程序`_AFXDLL`定义。

- 动态链接到 MFC 的规则 MFC DLL 还可以使用 MFC 扩展 DLL。

- 应使用编译 MFC 扩展 Dll`_AFXEXT`定义。 这会强制`_AFXDLL`也定义，并确保从 MFC 标头文件的正确声明提取的。 它还确保`AFX_EXT_CLASS`定义为`__declspec(dllexport)`时生成 DLL 时，这是必需的如果使用此宏来声明类在 MFC 扩展 DLL 中。

- MFC 扩展 Dll 不应实例化派生自的类`CWinApp`，但是应依赖于客户端应用程序 （或 DLL） 来提供此对象。

- MFC 扩展 Dll，但是，提供`DllMain`函数，并进行任何必需初始化。

扩展 Dll 是使用 MFC （也称为共享的 MFC 版本） 的动态链接库版本构建的。 MFC 的可执行文件 （应用程序或规则 MFC Dll） 使用共享 MFC 版本构建的可以使用 MFC 扩展 DLL。 客户端应用程序和 MFC 扩展 DLL 必须使用相同版本的 MFCx0.dll。 MFC 扩展 DLL，可从 MFC 派生新的自定义类，并再提供此扩展的版本的 MFC 应用程序调用 DLL 的。

扩展 Dll 还可以用于应用程序和 DLL 之间传递 MFC 派生的对象。 创建对象时的模块中存在与所传递的对象相关联的成员函数。 由于使用共享的 MFC DLL 版本时正确导出了这些函数，因此可以自由地传递 MFC 或应用程序和 MFC 扩展 Dll 加载之间 MFC 派生的对象指针。

MFC 扩展 DLL 使用共享的版本的 MFC 应用程序使用共享的 DLL 版本的 MFC，有几个额外的注意事项的方式相同：

- 它不具有`CWinApp`-派生的对象。 必须使用`CWinApp`-派生的对象的客户端应用程序。 这意味着客户端应用程序拥有主消息泵，空闲循环中，依次类推。

- 它将调用`AfxInitExtensionModule`在其`DllMain`函数。 应检查此函数的返回值。 如果返回值为零`AfxInitExtensionModule`，返回 0 从你`DllMain`函数。

- 它会创建**CDynLinkLibrary**对象在初始化期间，如果 MFC 扩展 DLL 要导出`CRuntimeClass`对象或对应用程序的资源。

之前版本的 MFC 4.0，这种类型的 DLL 调用 AFXDLL。 AFXDLL 指`_AFXDLL`生成 DLL 时定义的预处理器符号。

根据所述的约定命名共享版本的 MFC 导入库[MFC Dll 命名约定](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)。 Visual c + + 提供了 MFC Dll 和一个数字的非 MFC Dll，您可以使用和与您的应用程序一起分发的预构建的版本。 这些记录在 Redist.txt，安装到 Program Files\Microsoft Visual Studio 文件夹中。

如果要导出使用.def 文件，在开头和末尾标头文件中放置以下代码：

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

这四行代码确保你的代码已正确编译 MFC 扩展 DLL。 省去这四行代码可能会导致 DLL 编译或链接不正确。

如果您需要传递 MFC 或到或从非 MFC DLL，DLL 的 MFC 派生的对象指针应为 MFC 扩展 DLL。 创建对象时的模块中存在与所传递的对象相关联的成员函数。 由于使用共享的 MFC DLL 版本时正确导出了这些函数，因此可以自由地传递 MFC 或应用程序和 MFC 扩展 Dll 加载之间 MFC 派生的对象指针。

由于 c + + 名称重整和导出问题，导出列表从 MFC 扩展 DLL 可能会有所不同的同一个 DLL 的调试和零售版本和 Dll 之间针对不同的平台。 零售 MFCx0.dll 具有大约 2,000 导出入口点;调试 MFCx0D.dll 有大约 3,000 名已导出的入口点。

## <a name="memory-management"></a>内存管理

MFCx0.dll 和所有 MFC 扩展 Dll 加载到客户端应用程序的地址空间可以使用相同的内存分配器，资源加载和其他 MFC 全局状态，就好像在同一应用程序。 这很重要，因为非 MFC DLL 库和规则 MFC Dll 执行完全相反的操作，并且具有移出其自己的内存池分配每个 DLL。

MFC 扩展 DLL 分配内存，如果该内存可以随便与任何其他应用程序分配的对象。 此外，如果动态链接到 MFC 应用程序失败，操作系统保护维护共享 DLL 任何其他 MFC 的应用程序的完整性。

同样还为客户端应用程序和所有 MFC 扩展 Dll 以及 MFCx0.dll 本身之间共享其他全局的 MFC 状态，类似于当前的可执行文件加载资源，从。

## <a name="sharing-resources-and-classes"></a>共享资源和类

导出资源是通过资源的列表。 每个应用程序包含的单向链接的列表**CDynLinkLibrary**对象。 大多数标准加载资源的 MFC 实现时查找的资源，请先查看当前的资源模块 (`AfxGetResourceHandle`) 如果未找到资源和指导的列表**CDynLinkLibrary**对象尝试加载所请求的资源。

遍历列表也有缺点，它是速度稍慢，需要管理资源 ID 范围。 它具有链接到多个 MFC 扩展 Dll 的客户端应用程序可以使用任何 DLL 提供的资源，而无需指定 DLL 实例句柄的优势。 `AfxFindResourceHandle` 是一个 API 用于资源列表的每个步骤来查找给定的匹配项。 它采用名称和资源类型，并返回其中第一次发现的资源句柄 （或 NULL）。

如果您不想要浏览列表，而只能从特定位置加载资源，使用函数`AfxGetResourceHandle`和`AfxSetResourceHandle`保存旧句柄并设置新的句柄。 请确保还原旧资源句柄，然后返回到客户端应用程序。 使用这种方法来显式加载一个菜单的示例，请参阅 MFC 示例中的 Testdll2.cpp [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)。

动态创建 MFC 对象 MFC 名称是类似的。 MFC 对象反序列化机制需要具有的所有`CRuntimeClass`对象注册，以便它可以通过动态创建基于以前存储的内容所需类型的 c + + 对象重新构造。

在 MFC 示例的情况下[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)，列表看起来类似于：

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

MFCxx.dll 是通常的最后一个的资源和类列表。 MFCxx.dll 包括所有标准 MFC 资源，包括所有标准命令 Id 的提示字符串。 将其放在列表末尾允许 Dll 和客户端应用程序本身不具有其自己副本标准 MFC 资源，而改为依赖于 MFCxx.dll 中的共享资源。

合并到客户端应用程序的命名空间的资源和类名称的所有 Dll 具有的缺点是需要谨慎使用 Id 或您选择的名称。

[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)示例通过使用多个标头文件来管理共享的资源命名空间。

如果您的 MFC 扩展 DLL 需要维护每个应用程序的额外数据，可以派生新类从**CDynLinkLibrary**并创建在`DllMain`。 运行时，该 DLL 可以检查当前应用程序的列表**CDynLinkLibrary**对象以查找该特定 MFC 扩展 DLL 的一个。

### <a name="what-do-you-want-to-do"></a>你希望做什么？

- [初始化 MFC 扩展 DLL](../build/run-time-library-behavior.md#initializing-extension-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [有关使用共享的资源文件的提示](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

- [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)

- [静态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-statically-linked-to-mfc.md)

- [动态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [在规则 MFC DLL 中使用数据库、OLE 和套接字 MFC 扩展 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

## <a name="see-also"></a>请参阅

[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)