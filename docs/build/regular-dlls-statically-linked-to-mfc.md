---
title: 静态链接到 MFC 的规则 MFC Dll
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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314775"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>静态链接到 MFC 的规则 MFC Dll

正则表达式以静态方式链接到 MFC 的 MFC DLL 是在内部，使用 MFC 的 DLL 和可由 MFC 或非 MFC 可执行文件调用 DLL 中导出的函数。 如名称所述，使用静态链接库版本的 MFC 生成此类型的 DLL。 通常是从正则表达式使用标准的 C 接口的 MFC DLL 导出函数。 有关如何编写、 构建和使用的规则 MFC DLL 的示例，请参阅示例[DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap)。

请注意，在视觉对象中不再使用的术语 USRDLLC++文档。 静态链接到 MFC 的规则 MFC DLL 具有 usrdll 相同的特性。

规则 MFC DLL，静态链接到 MFC，具有以下功能：

- 客户端可执行文件可以采用任何支持 Dll 使用的语言 (C， C++，Pascal、 Visual Basic 中，依次类推);它不必是 MFC 应用程序。

- DLL 可链接到应用程序使用的相同 MFC 静态链接库。 不再用于 Dll 的静态链接库的单独版本。

- 之前版本的 MFC 4.0，Usrdll 提供相同类型的与静态链接到 MFC 的规则 MFC Dll 的功能。 截至 VisualC++版本 4.0 中，术语 USRDLL 已过时。

规则 MFC DLL，静态链接到 MFC，具有以下要求：

- 这种类型的 DLL 必须实例化派生自的类`CWinApp`。

- 这种类型的 DLL 将`DllMain`MFC 提供。 将中的所有 DLL 特定初始化代码都放`InitInstance`中的成员函数和终止代码`ExitInstance`如普通的 MFC 应用程序中所示。

- 尽管术语 USRDLL 已过时，仍必须定义"**_USRDLL**"编译器命令行上。 此定义确定从 MFC 标头文件复制的声明。

规则 MFC Dll 必须具有`CWinApp`-派生的类以及该类应用程序的单个对象的 MFC 应用程序一样。 但是， `CWinApp` DLL 的对象不具有主消息泵，如同`CWinApp`应用程序的对象。

请注意，`CWinApp::Run`机制不适用于 DLL，因为应用程序拥有主消息泵。 如果 DLL 打开无模式对话框或有其自己的主框架窗口，应用程序的主消息泵必须调用反过来调用 DLL 导出的例程`CWinApp::PreTranslateMessage`DLL 的应用程序对象的成员函数。

此函数的示例，请参阅 DLLScreenCap 示例。

通常是从正则表达式使用标准的 C 接口的 MFC DLL 导出的符号。 从规则 MFC DLL 导出函数的声明将如下所示：

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

规则 MFC DLL 的所有内存分配应都遵守 DLL;DLL 不应传递给或接收从调用的可执行文件的以下任何：

- MFC 对象的指针

- 指向由 MFC 分配的内存的指针

如果您需要执行上述任何操作或需要调用的可执行文件和 DLL 之间传递 MFC 派生的对象，则必须生成 MFC 扩展 DLL。

它可以安全地将指针传递给已分配的内存的 C 运行时库应用程序和 DLL 之间仅当您制作数据的副本。 您必须删除或调整这些指针的大小或使用它们而无需进行的内存的副本。

静态链接到 MFC 的 DLL 还可以动态不能链接到共享 MFC Dll。 静态链接到 MFC 的 DLL 是动态绑定到应用程序就像任何其他 DLL;应用程序链接到它就像任何其他 DLL。

根据所述的约定命名标准 MFC 静态链接库[MFC dll 命名约定](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)。 但是，使用 MFC 3.0 版及更高版本，就不再需要手动指定链接器所需中链接的 MFC 库版本。 MFC 标头文件相反，自动确定要根据预处理器中链接的 MFC 库的正确版本定义，如**\_调试**或 **_UNICODE**。 MFC 标头文件添加 /DEFAULTLIB 指令指示链接器以特定版本的 MFC 库中的链接。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [初始化规则 MFC Dll](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [将 MFC 作为 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [在规则 MFC DLL 中使用数据库、OLE 和套接字 MFC 扩展 DLL](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [创建 MFC DLL](../mfc/reference/mfc-dll-wizard.md)

- [动态链接到 MFC 的规则 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 扩展 DLL](extension-dlls-overview.md)

## <a name="see-also"></a>请参阅

[DLL 的类型](kinds-of-dlls.md)
