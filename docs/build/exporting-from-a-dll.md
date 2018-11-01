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
ms.openlocfilehash: f932ba2d9b229d236270eb664ac1291725471706
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493816"
---
# <a name="exporting-from-a-dll"></a>从 DLL 导出

DLL 文件具有与.exe 文件，有一个重要的区别非常相似的布局，DLL 文件中包含的导出表。 导出表包含每个函数的 DLL 将导出到其他可执行文件的名称。 这些函数是 dll; 的入口点可以通过其他可执行文件访问仅导出表中的函数。 在 DLL 中的任何其他函数是私有的 DLL。 可以通过查看 DLL 导出表[DUMPBIN](../build/reference/dumpbin-reference.md) /EXPORTS 选项的工具。

可以使用两种方法从 DLL 导出函数：

- 创建模块定义 (.def) 文件并生成 DLL 时使用.def 文件。 如果您要使用此方法[按序号而不是按名称从 DLL 导出函数](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。

- 使用关键字 **__declspec （dllexport)** 函数的定义中。

当使用任何一种方法导出函数，请务必使用[__stdcall](../cpp/stdcall.md)调用约定。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用.def 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport） 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [导出和导入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [导出 c + + 函数以用于 C 语言可执行文件](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [导出 C 函数以用于 C 或 c + + 语言可执行文件](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [按序号而不是按名称从 DLL 导出函数](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)

- [确定要使用的链接方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [导入到应用程序](../build/importing-into-an-application.md)

- [导入和导出内联函数](../build/importing-and-exporting-inline-functions.md)

- [相互导入](../build/mutual-imports.md)

## <a name="see-also"></a>请参阅

[导入和导出](../build/importing-and-exporting.md)