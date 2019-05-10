---
title: 使用 __declspec(dllexport) 从 DLL 导出
ms.date: 05/06/2019
f1_keywords:
- dllexport
- __declspec
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
ms.openlocfilehash: 167060d0270004b8648d32af206865bfe66c3b4b
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220793"
---
# <a name="exporting-from-a-dll-using-declspecdllexport"></a>使用 __declspec(dllexport) 从 DLL 导出

可以从 DLL 使用导出数据、 函数、 类或类成员函数 **__declspec （dllexport)** 关键字。 **__declspec （dllexport)** 将导出指令添加到对象文件，因此不需要使用.def 文件。

这种便利是最明显时尝试导出修饰C++函数名。 由于没有对名称修饰没有标准规范，导出函数的名称可能会更改不同的编译器版本。 如果您使用 **__declspec （dllexport)**，重新编译的 DLL 和依赖.exe 文件是仅对帐户的任何命名约定更改是必需的。

许多导出指令，如序号、 NONAME 和私有，可为仅在.def 文件中，并没有方法来指定这些特性.def 文件。 但是，使用 **__declspec （dllexport)** 除了在.def 文件不会导致生成错误。

若要导出函数， **__declspec （dllexport)** 关键字必须出现左侧的调用约定关键字，如果指定了关键字。 例如：

```
__declspec(dllexport) void __cdecl Function1(void);
```

若要导出的所有公共数据成员和成员函数在类中，关键字必须出现类名的左边，如下所示：

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
>  `__declspec(dllexport)` 不能应用于具有函数`__clrcall`调用约定。

在生成 DLL 时，通常创建包含的函数原型和/或要导出并添加的类的标头文件 **__declspec （dllexport)** 到标头文件中的声明。 若要使代码更具可读性，定义为宏 **__declspec （dllexport)** ，要导出的每个符号将使用该宏：

```
#define DllExport   __declspec( dllexport )
```

**__declspec （dllexport)** 存储函数的 DLL 导出表中的名称。 如果你想要优化的表的大小，请参阅[从按序号而不是按名称的 DLL 导出函数](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用.def 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)

- [导出和导入使用 AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [导出C++函数以用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [导出 C 函数以用于 C 或C++-语言可执行文件](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 导入到应用程序中](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [__Declspec 关键字](../cpp/declspec.md)

- [导入和导出内联函数](importing-and-exporting-inline-functions.md)

- [相互导入](mutual-imports.md)

## <a name="see-also"></a>请参阅

[从 DLL 导出](exporting-from-a-dll.md)
