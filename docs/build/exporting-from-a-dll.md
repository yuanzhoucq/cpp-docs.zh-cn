---
title: 从 DLL 导出
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [C++], about exporting from DLLs
- exporting functions [C++], DLLs (exporting from)
- exporting DLLs [C++]
- DLLs [C++], exporting from
- DLL exports [C++]
- functions [C++], exporting
- exports table [C++]
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
ms.openlocfilehash: 6bdf5b86724ae07aa073a9feb1cc4d5723bc6e6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196737"
---
# <a name="exporting-from-a-dll"></a>从 DLL 导出

DLL 文件的布局与 .exe 文件非常相似，但有一个重要的区别：DLL 文件包含导出表。 导出表包含 DLL 导出到其他可执行文件的每个函数的名称。 这些函数是进入 DLL 中的入口点；只有导出表中的函数才能被其他可执行文件访问。 DLL 中的任何其他函数都是 DLL 的私有函数。 可通过使用带有 /EXPORTS 选项的 [DUMPBIN](reference/dumpbin-reference.md) 工具来查看 DLL 导出表。

可使用两种方法从 DLL 导出函数：

- 创建模块定义 (.def) 文件，然后在生成 DLL 时使用 .def 文件。 如果希望[按序号而不是按名称从 DLL 中导出函数](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)，请使用此方法。

- 在函数定义中使用关键字 __declspec(dllexport)  。

用任一方法导出函数时，请确保使用 [__stdcall](../cpp/stdcall.md) 调用约定。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用 .def 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec(dllexport) 从 DLL 导出](exporting-from-a-dll-using-declspec-dllexport.md)

- [使用 AFX_EXT_CLASS 导出和导入](exporting-and-importing-using-afx-ext-class.md)

- [导出 C++ 函数以用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [导出 C 函数以用于 C 或 C++ 语言可执行文件](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [按序号而不是按名称从 DLL 导出函数](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [导入到应用程序中](importing-into-an-application.md)

- [导入和导出内联函数](importing-and-exporting-inline-functions.md)

- [相互导入](mutual-imports.md)

## <a name="see-also"></a>请参阅

[导入和导出](importing-and-exporting.md)
