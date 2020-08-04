---
title: 使用 __declspec(dllexport) 从 DLL 导出
ms.date: 05/06/2019
f1_keywords:
- dllexport
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
ms.openlocfilehash: 77dc6dc14efe2a7ccf46c41477ed4fd6d1956856
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224027"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>使用 __declspec(dllexport) 从 DLL 导出

可以使用 `__declspec(dllexport)` 关键字从 DLL 中导出数据、函数、类或类成员函数。 `__declspec(dllexport)` 将导出指令添加到对象文件中，因此你不需要使用 .def 文件。

尝试导出已修饰的 C++ 函数名称时，这种便利性最为明显。 由于名称修饰没有标准规范，因此，导出函数的名称可能会因编译器版本而异。 如果你使用 `__declspec(dllexport)`，则只有在考虑到任何命名约定更改时，才需要重新编译 DLL 和依赖 .exe 文件。

许多导出指令只能在 .def 文件中创建，例如 ordinals、NONAME 和 PRIVATE，并且没有 .def 文件就无法指定这些属性。 不过，除了使用 .def 文件外还使用 `__declspec(dllexport)` 不会导致生成错误出现。

若要导出函数，`__declspec(dllexport)` 关键字必须出现在调用约定关键字的左侧（如果指定了关键字的话）。 例如：

```
__declspec(dllexport) void __cdecl Function1(void);
```

若要导出类中的所有公共数据成员和成员函数，该关键字必须出现在类名的左侧，如下所示：

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
> `__declspec(dllexport)` 不能应用于采用 `__clrcall` 调用约定的函数。

生成 DLL 时，通常会创建一个包含要导出的函数原型和/或类的头文件，并将 `__declspec(dllexport)` 添加到头文件中的声明内。 为了提高代码的可读性，请为 `__declspec(dllexport)` 定义宏，并对要导出的每个符号使用此宏：

```
#define DllExport   __declspec( dllexport )
```

`__declspec(dllexport)` 将函数名称存储在 DLL 的导出表中。 如果要优化表的大小，请参阅[按序号而不是按名称从 DLL 导出函数](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用 .def 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)

- [使用 AFX_EXT_CLASS 导出和导入](exporting-and-importing-using-afx-ext-class.md)

- [导出 C++ 函数以用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [导出 C 函数以用于 C 或 C++ 语言可执行文件](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 导入到应用程序中](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [__declspec 关键字](../cpp/declspec.md)

- [导入和导出内联函数](importing-and-exporting-inline-functions.md)

- [相互导入](mutual-imports.md)

## <a name="see-also"></a>请参阅

[从 DLL 导出](exporting-from-a-dll.md)
