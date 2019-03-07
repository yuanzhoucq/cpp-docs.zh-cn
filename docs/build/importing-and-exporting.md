---
title: 导入和导出
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
ms.openlocfilehash: 1aaf18003f831ca94ecd90dafb472ecb894b8a60
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424790"
---
# <a name="importing-and-exporting"></a>导入和导出

可以将公共符号导入到应用程序，也可以使用两种方法从 DLL 导出函数：

- 当生成 DLL 时使用的模块定义 (.def) 文件

- 使用关键字 **__declspec （dllimport)** 或 **__declspec （dllexport)** 主应用程序中函数定义中

## <a name="using-a-def-file"></a>使用.def 文件

模块定义 (.def) 文件是包含一个或多个描述 DLL 各种特性的 module 语句的文本文件。 如果不使用 **__declspec （dllimport)** 或 **__declspec （dllexport)** 若要导出的 DLL 函数，则 DLL 需要.def 文件。

可以使用.def 文件复制到[导入应用程序](../build/importing-using-def-files.md)或设置为[从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)。

## <a name="using-declspec"></a>使用 __declspec

Visual c + + 使用 **__declspec （dllimport)** 并 **__declspec （dllexport)** 替换 **__export** 16 位版本的 Visual c + + 中以前使用过的关键字。

不需要使用 **__declspec （dllimport)** 为你的代码来正确编译，但执行此操作允许编译器生成更好的代码。 编译器就能够生成更好的代码，因为它可以确定函数中是否存在一个 DLL，它允许编译器以生成将跳过一定程度的间接性通常会出现跨 DLL 边界函数调用中的代码。 但是，必须使用 **__declspec （dllimport)** 导入一个 DLL 中使用的变量。

使用适当的.def 文件导出部分中， **__declspec （dllexport)** 不是必需的。 **__declspec （dllexport)** 添加了以可以方便地从.exe 或.dll 文件中导出函数，而无需使用.def 文件。

Win32 可移植可执行文件格式设计为最大程度减少必须打开，以修复导入的页面数。 若要执行此操作，它将在一个位置调用导入地址表中的任何程序的所有导入地址。 这样，要访问这些导入时修改只能将一个或两个页面的加载程序。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [导入到应用程序](../build/importing-into-an-application-using-declspec-dllimport.md)

- [从 DLL 导出](../build/exporting-from-a-dll.md)

## <a name="see-also"></a>请参阅

[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)
