---
title: 扩展 DLL
ms.date: 05/06/2019
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
ms.openlocfilehash: 55b1e55a9c7bdf6daaff98a7fe3f1a2a55f68334
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220773"
---
# <a name="mfc-extension-dlls"></a>MFC 扩展 DLL

MFC 扩展 DLL 是通常实现从现有 Microsoft 基础类库类派生的可重用类的 DLL。

MFC 扩展 DLL 具有以下功能和要求：

- 客户端可执行文件必须是使用定义的 `_AFXDLL` 编译的 MFC 应用程序。

- MFC 扩展 DLL 还可由动态链接到 MFC 的规则 MFC DLL 使用。

- MFC 扩展 DLL 应使用定义的 `_AFXEXT` 进行编译。 这会强制同时定义 `_AFXDLL`，并确保从 MFC 头文件拉取正确的声明。 它还确保在生成 DLL 时 `AFX_EXT_CLASS` 定义为 `__declspec(dllexport)`，这在使用此宏声明 MFC 扩展 DLL 中的类时是必需的。

- MFC 扩展 DLL 不应实例化派生自 `CWinApp` 的类，但应依赖于客户端应用程序（或 DLL）来提供此对象。

- 但是，MFC 扩展 DLL 应提供 `DllMain` 函数并在其中执行任何所需初始化。

扩展 DLL 使用 MFC 的动态链接库版本（也称为 MFC 的共享版本）生成。 只有使用 MFC 的共享版本生成的 MFC 可执行文件（应用程序或规则 MFC DLL）才能使用 MFC 扩展 DLL。 客户端应用程序和 MFC 扩展 DLL 都必须使用相同版本的 MFCx0.dll。 使用 MFC 扩展 DLL 时，可以从 MFC 派生新的自定义类，然后将 MFC 的此扩展版本提供给调用 DLL 的应用程序。

扩展 DLL 还可用于在应用程序与 DLL 之间传递 MFC 派生对象。 与传递的对象关联的成员函数存在于创建对象的模块中。 由于这些函数会在使用 MFC 的共享 DLL 版本时正确导出，因此可以在应用程序与它所加载的 MFC 扩展 DLL 之间自由传递 MFC 或 MFC 派生对象指针。

MFC 扩展 DLL 使用 MFC 的共享版本的方式与应用程序使用 MFC 的共享 DLL 版本的方式相同，有一些其他注意事项：

- 它没有 `CWinApp` 派生对象。 它必须使用客户端应用程序的 `CWinApp` 派生对象。 这意味着客户端应用程序拥有主消息泵、空闲循环等。

- 它在其 `DllMain` 函数中调用 `AfxInitExtensionModule`。 应检查此函数的返回值。 如果从 `AfxInitExtensionModule` 返回零值，则从 `DllMain` 函数返回 0。

- 如果 MFC 扩展 DLL 要将 `CRuntimeClass` 对象或资源导出到应用程序，则它会在初始化过程中创建 CDynLinkLibrary  对象。

在 MFC 版本 4.0 之前，此类型的 DLL 称为 AFXDLL。 AFXDLL 引用在生成 DLL 时定义的 `_AFXDLL` 预处理器符号。

MFC 的共享版本的导入库按照 [MFC DLL 命名约定](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)中所述的约定进行命名。 Visual Studio 提供 MFC Dll 的预生成版本，以及一些可随应用程序使用和分发的非 MFC DLL。 这些内容记录在 Redist.txt（会安装到 Program Files\Microsoft Visual Studio 文件夹）中。

如果要使用 .def 文件导出，请将以下代码放置在头文件的开头和结尾：

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

这四行代码可确保为 MFC 扩展 DLL 正确地编译代码。 省略这四行代码可能会导致 DLL 无法正确编译或链接。

如果需要与 MFC DLL 来回传递 MFC 或 MFC 派生对象指针，则 DLL 应为 MFC 扩展 DLL。 与传递的对象关联的成员函数存在于创建对象的模块中。 由于这些函数会在使用 MFC 的共享 DLL 版本时正确导出，因此可以在应用程序与它所加载的 MFC 扩展 DLL 之间自由传递 MFC 或 MFC 派生对象指针。

由于 C++ 名称重整和导出问题，一个 MFC 扩展 DLL 中的导出列表在同一个 DLL 的调试版本和零售版本之间以及用于不同平台的 DLL 之间可能不同。 零售 MFCx0.dll 具有大约 2,000 个导出入口点；调试 MFCx0D.dll 具有大约 3,000 个导出入口点。

## <a name="memory-management"></a>内存管理

MFCx0.dll 以及加载到客户端应用程序地址空间中的所有 MFC 扩展 DLL 使用相同的内存分配器、资源加载和其他 MFC 全局状态，就如同它们位于同一个应用程序中一样。 这一点十分重要，因为非 MFC DLL 库和规则 MFC DLL 恰好相反，使每个 DLL 都从其自己的内存池中进行分配。

如果 MFC 扩展 DLL 分配内存，则该内存可以自由地与任何其他应用程序分配的对象混合。 此外，如果动态链接到 MFC 的应用程序失败，则操作系统的保护会维护共享 DLL 的任何其他 MFC 应用程序的完整性。

同样，其他全局 MFC 状态（如从其加载资源的当前可执行文件）也在客户端应用程序与所有 MFC 扩展 DLL 以及 MFCx0.dll 本身之间共享。

## <a name="sharing-resources-and-classes"></a>共享资源和类

导出资源通过资源列表来进行。 每个应用程序都包含 CDynLinkLibrary  对象的单独链接列表。 查找资源时，加载资源的大多数标准 MFC 实现首先查看当前资源模块 (`AfxGetResourceHandle`)，如果未找到资源，则会遍历尝试加载所请求资源的 CDynLinkLibrary  对象的列表。

遍历该列表的缺点是稍微慢一些，需要管理资源 ID 范围。 其优点是链接到多个 MFC 扩展 DLL 的客户端应用程序可以使用任何 DLL 提供的资源，而无需指定 DLL 实例句柄。 `AfxFindResourceHandle` 是用于遍历资源列表以查找给定匹配项的 API。 它采用资源的名称和类型，并返回首次找到该资源的资源句柄（或 NULL）。

如果不想遍历列表并只从特定位置加载资源，请使用函数 `AfxGetResourceHandle` 和 `AfxSetResourceHandle` 保存旧句柄并设置新句柄。 在返回到客户端应用程序之前，请务必还原旧资源句柄。 有关使用此方法显式加载菜单的示例，请参阅 MFC 示例 [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk) 中的 Testdll2 .cpp。

给定 MFC 名称的 MFC 对象以类似方式动态创建。 MFC 对象反序列化机制需要注册所有 `CRuntimeClass` 对象，以便它可以通过基于之前存储的内容动态创建所需类型的 C++ 对象来重新构造。

对于 MFC 示例 [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)，列表如下所示：

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

其中 xx  是版本号；例如，42 表示版本 4.2。

MFCxx.dll 通常位于资源和类列表的最后。 MFCxx.dll 包含所有标准 MFC 资源，包括所有标准命令 ID 的提示字符串。 将它放在列表末尾使 DLL 和客户端应用程序本身可以没有自己的标准 MFC 资源副本，而是依赖于 MFCxx.dll 中的共享资源。

将所有 DLL 的资源和类名合并到客户端应用程序的命名空间的缺点在于，需要谨慎处理选择的 ID 或名称。

[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk) 示例使用多个头文件管理共享资源命名空间。

如果 MFC 扩展 DLL 需要维护每个应用程序的额外数据，则可以从 CDynLinkLibrary  派生新类并在 `DllMain` 中创建它。 在运行时，DLL 可以检查当前应用程序的 CDynLinkLibrary  对象列表，以查找该特定 MFC 扩展 DLL 的对应对象。

### <a name="what-do-you-want-to-do"></a>你希望做什么？

- [初始化 MFC 扩展 DLL](run-time-library-behavior.md#initializing-extension-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [有关使用共享资源文件的提示](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

- [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)

- [静态链接到 MFC 的规则 MFC DLL](regular-dlls-statically-linked-to-mfc.md)

- [动态链接到 MFC 的规则 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [在规则 MFC DLL 中使用数据库、OLE 和套接字 MFC 扩展 DLL](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

## <a name="see-also"></a>请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)
