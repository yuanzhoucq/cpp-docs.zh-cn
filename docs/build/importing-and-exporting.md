---
title: 导入和导出
ms.date: 05/06/2019
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
ms.openlocfilehash: 03931f7f128ab0666890bb8e76677db67dda8fc7
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220639"
---
# <a name="importing-and-exporting"></a>导入和导出

可以使用两种方法将公共符号导入应用程序或从 DLL 导出函数：

- 生成 DLL 时使用模块定义 (.def) 文件

- 在主应用程序的函数定义中使用关键字 __declspec(dllimport)  或 __declspec(dllexport) 

## <a name="using-a-def-file"></a>使用 .def 文件

模块定义 (.def) 文件是文本文件，其中包含一个或多个描述 DLL 的各种特性的模块语句。 如果不使用 __declspec(dllimport)  或 __declspec(dllexport)  导出 DLL 的函数，则 DLL 需要 .def 文件。

可以使用 .def 文件[导入到应用程序中](importing-using-def-files.md)或[从 DLL 导出](exporting-from-a-dll-using-def-files.md)。

## <a name="using-__declspec"></a>使用 __declspec

无需使用 __declspec(dllimport)  即可正确编译代码，但使用它会使编译器生成更好的代码。 编译器能够生成更好的代码，因为它可以确定某个函数是否存在于 DLL 中，这使编译器生成的代码可以跳过在跨越 DLL 边界的函数调用中通常存在的间接级别。 但是，必须使用 __declspec(dllimport)  导入 DLL 中使用的变量。

使用正确的 .def 文件 EXPORTS 节时，不需要 __declspec(dllexport)  。 添加了 __declspec(dllexport)  以提供一种简单方法，用于在不使用 .def 文件的情况下从 .exe 或 .dll 文件导出函数。

Win32 可移植可执行文件格式旨在最大程度减少修复导入所必须涉及的页数。 为此，它将任何程序的所有导入地址都放置在一个名为导入地址表的位置。 这使加载程序可以在访问这些导入时仅修改一页或两页。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [导入到应用程序中](importing-into-an-application-using-declspec-dllimport.md)

- [从 DLL 导出](exporting-from-a-dll.md)

## <a name="see-also"></a>请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)
