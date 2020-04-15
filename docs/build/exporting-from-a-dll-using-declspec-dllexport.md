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
ms.openlocfilehash: 075962758773660085ae0b98b668c264524cc6aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328596"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>使用 __declspec(dllexport) 从 DLL 导出

您可以使用 **__declspec（dllexport）** 关键字从 DLL 导出数据、函数、类或类成员函数。 **__declspec（dllexport）** 将导出指令添加到对象文件，因此无需使用 .def 文件。

在尝试导出修饰C++函数名称时，这种便利性最为明显。 由于没有名称修饰的标准规范，导出函数的名称可能会在编译器版本之间更改。 如果使用 **__declspec（dllexport），** 则重新编译 DLL 和从属 .exe 文件仅需要考虑任何命名约定更改。

许多导出指令（如指令指令、NONAME 和 PRIVATE）只能在 .def 文件中进行，并且没有 .def 文件无法指定这些属性。 但是，除了使用 .def 文件外，使用 **__declspec（dllexport）** 不会导致生成错误。

要导出函数，如果指定了关键字，**则__declspec（dllexport）** 关键字必须显示在调用约定关键字的左侧。 例如：

```
__declspec(dllexport) void __cdecl Function1(void);
```

要导出类中的所有公共数据成员和成员函数，关键字必须显示在类名称的左侧，如下所示：

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
> `__declspec(dllexport)`不能应用于具有调用约定的`__clrcall`函数。

构建 DLL 时，通常会创建包含要导出的函数原型和/或类的标头文件，并将 **__declspec（dllexport）** 添加到标头文件中的声明。 要使代码更具可读性，请为 **__declspec（dllexport）** 定义宏，并将宏与要导出的每个符号一起使用：

```
#define DllExport   __declspec( dllexport )
```

**__declspec（dllexport）** 在 DLL 导出表中存储函数名称。 如果要优化表的大小，请参阅[按 Ordinal 而不是按名称 从 DLL 导出函数](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。

## <a name="what-do-you-want-to-do"></a>您希望做什么？

- [使用 .def 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)

- [使用AFX_EXT_CLASS导出和导入](exporting-and-importing-using-afx-ext-class.md)

- [导出C++函数，用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [导出 C 函数，用于 C 或C++语言可执行文件](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 导入到应用程序中](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [__declspec关键字](../cpp/declspec.md)

- [导入和导出内联函数](importing-and-exporting-inline-functions.md)

- [相互导入](mutual-imports.md)

## <a name="see-also"></a>另请参阅

[从 DLL 导出](exporting-from-a-dll.md)
