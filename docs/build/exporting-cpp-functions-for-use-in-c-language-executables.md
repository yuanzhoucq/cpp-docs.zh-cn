---
title: 导出 C++ 函数以用于 C 语言可执行文件
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
ms.openlocfilehash: a694b77e3730ab82ec1698076cc66729ff115cdc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195229"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>导出 C++ 函数以用于 C 语言可执行文件

如果要从 C 语言模块访问用 C++ 编写的 DLL 中的函数，则应使用 C 链接（而不是 C++ 链接）声明这些函数。 除非另外指定，否则 C++ 编译器会使用 C++ 类型安全命名（也称为名称修饰）和 C++ 调用约定（可能难以从 C 中进行调用）。

若要指定 C 链接，请为函数声明指定 `extern "C"`。 例如：

```
extern "C" __declspec( dllexport ) int MyFunc(long parm1);
```

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用 .def 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec(dllexport) 从 DLL 导出](exporting-from-a-dll-using-declspec-dllexport.md)

- [使用 AFX_EXT_CLASS 导出和导入](exporting-and-importing-using-afx-ext-class.md)

- [导出 C 函数以用于 C 或 C++ 语言可执行文件](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 导入到应用程序中](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [修饰名](reference/decorated-names.md)

- [使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>请参阅

[从 DLL 导出](exporting-from-a-dll.md)
