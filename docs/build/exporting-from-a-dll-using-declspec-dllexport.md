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
ms.openlocfilehash: c84a8eca25c90e0790ec8c4991d9d5a116afa59f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442523"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>使用 __declspec(dllexport) 从 DLL 导出

您可以使用 **__declspec （dllexport）** 关键字从 DLL 中导出数据、函数、类或类成员函数。 **__declspec （dllexport）** 将导出指令添加到对象文件中，因此不需要使用 .def 文件。

尝试导出修饰C++的函数名时，这种便利最明显。 由于名称修饰没有标准规范，因此导出函数的名称在编译器版本之间可能会发生更改。 如果使用 **__declspec （dllexport）** ，则必须重新编译 DLL 和从属 .exe 文件，才能考虑任何命名约定更改。

许多导出指令（如序数、NONAME 和 PRIVATE）只能在 .def 文件中进行，并且无法在没有 .def 文件的情况下指定这些属性。 但是，除了使用 .def 文件以外，使用 **__declspec （dllexport）** 不会导致生成错误。

若要导出函数，如果指定关键字，则 **__declspec （dllexport）** 关键字必须出现在调用约定关键字的左侧。 例如：

```
__declspec(dllexport) void __cdecl Function1(void);
```

若要导出类中的所有公共数据成员和成员函数，关键字必须出现在类名的左侧，如下所示：

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
>  `__declspec(dllexport)` 不能应用于具有 `__clrcall` 调用约定的函数。

生成 DLL 时，通常会创建一个标头文件，其中包含要导出的函数原型和/或类，并将 **__declspec （dllexport）** 添加到标头文件中的声明。 若要使代码更具可读性，请定义 **__declspec （dllexport）** 的宏，并将宏与要导出的每个符号一起使用：

```
#define DllExport   __declspec( dllexport )
```

**__declspec （dllexport）** 将函数名称存储在 DLL 的导出表中。 如果要优化表的大小，请参阅[按序号而不是按名称从 DLL 导出函数](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。

## <a name="what-do-you-want-to-do"></a>要执行什么操作？

- [使用 .def 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)

- [使用 AFX_EXT_CLASS 进行导出和导入](exporting-and-importing-using-afx-ext-class.md)

- [导出C++函数以用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [导出 C 函数以用于 C 或C++语言可执行文件](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 导入到应用程序中](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [__Declspec 关键字](../cpp/declspec.md)

- [导入和导出内联函数](importing-and-exporting-inline-functions.md)

- [相互导入](mutual-imports.md)

## <a name="see-also"></a>另请参阅

[从 DLL 导出](exporting-from-a-dll.md)
