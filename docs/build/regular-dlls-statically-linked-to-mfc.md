---
title: 静态链接到 MFC 的规则 MFC DLL
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
ms.openlocfilehash: 1f05b5e3c268935cf3161fb7184e04b3e3ea1446
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314775"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>静态链接到 MFC 的规则 MFC DLL

静态链接到 MFC 的规则 MFC DLL 是在内部使用 MFC 的 DLL，而 DLL 中的导出函数可以由 MFC 或非 MFC 可执行文件调用。 顾名思义，此类型的 DLL 使用 MFC 的静态链接库发布生成。 通常使用标准 C 接口从规则 MFC DLL 导出函数。 有关如何编写、生成和使用规则 MFC DLL 的示例，请参阅示例 [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap)。

请注意，术语 USRDLL 已不再用于 Visual C++ 文档。 静态链接到 MFC 的规则 MFC DLL 具有与以前 USRDLL 相同的特性。

静态链接到 MFC 的规则 MFC DLL 具有以下功能：

- 可以采用支持使用 DLL 的任何语言（C、C++、Pascal、Visual Basic 等）编写客户端可执行文件；它不必是 MFC 应用程序。

- DLL 可以链接到应用程序使用的相同 MFC 静态链接库。 DLL 不再有单独的静态链接库版本。

- 在 MFC 版本 4.0 之前，USRDLL 提供了与静态链接到 MFC 的规则 MFC DLL 相同类型的功能。 从 Visual C++ 版本 4.0 起，术语 USRDLL 已过时。

静态链接到 MFC 的规则 MFC DLL 具有以下要求：

- 这种类型的 DLL 必须实例化派生自 `CWinApp` 的类。

- 这种 DLL 使用 MFC 提供的 `DllMain`。 将所有特定于 DLL 的初始化代码都置于 `InitInstance` 成员函数中，而将终止代码置于 `ExitInstance` 中，就如同在普通 MFC 应用程序中一样。

- 即使术语 USRDLL 已过时，仍必须在编译器命令行上定义“_USRDLL  ”。 此定义确定从 MFC 头文件拉取的声明。

与 MFC 应用程序一样，规则 MFC DLL 必须具有 `CWinApp` 派生类和该应用程序类的单个对象。 但是，DLL 的 `CWinApp` 对象没有主消息泵，而应用程序的 `CWinApp` 对象也是如此。

请注意，`CWinApp::Run` 机制不适用于 DLL，因为应用程序拥有主消息泵。 如果 DLL 打开无模式对话框或具有其自己的主框架窗口，则应用程序的主消息泵必须调用由 DLL 导出的例程，该例程又会调用 DLL 的应用程序对象的 `CWinApp::PreTranslateMessage` 成员函数。

有关此函数的示例，请参阅 DLLScreenCap 示例。

通常使用标准 C 接口从规则 MFC DLL 导出符号。 从规则 MFC DLL 导出的函数的声明类似于以下内容：

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

规则 MFC DLL 内的所有内存分配都应保留在 DLL 内；DLL 不应向调用可执行文件传递或从其接收以下任何内容：

- 指向 MFC 对象的指针

- 指向由 MFC 分配的内存的指针

如果需要执行上述任何操作或需要在调用可执行文件与 DLL 之间传递 MFC 派生对象，则必须生成 MFC 扩展 DLL。

仅当创建数据的副本时，才可安全地在应用程序和 DLL 之间传递指向由 C 运行时库分配的内存的指针。 不得删除这些指针或重设其大小，也不得在不创建内存副本的情况下使用它们。

静态链接到 MFC 的 DLL 还无法动态链接到共享 MFC DLL。 静态链接到 MFC 的 DLL 会动态绑定到应用程序，就像任何其他 DLL 一样；应用程序会链接到它，就像任何其他 DLL 一样。

标准 MFC 静态链接库按照 [MFC DLL 命名约定](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)中所述的约定进行命名。 但是，在 MFC 3.0 版及更高版本中，不再需要向链接器手动指定要链接的 MFC 库的版本。 相反，MFC 头文件将基于预处理器定义（如 \_DEBUG  或 _UNICODE  ）自动确定要链接的 MFC 库的正确版本。 MFC 头文件会添加 /DEFAULTLIB 指令来指示链接器链接到特定的 MFC 库版本中。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [初始化规则 MFC DLL](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [将 MFC 用作 DLL 的一部分](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [在规则 MFC DLL 中使用数据库、OLE 和套接字 MFC 扩展 DLL](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [创建 MFC DLL](../mfc/reference/mfc-dll-wizard.md)

- [动态链接到 MFC 的规则 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 扩展 DLL](extension-dlls-overview.md)

## <a name="see-also"></a>请参阅

[DLL 的类型](kinds-of-dlls.md)
