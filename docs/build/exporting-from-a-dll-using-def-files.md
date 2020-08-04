---
title: 使用 DEF 文件从 DLL 导出
ms.date: 05/06/2019
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: 8fdbb060502f339eb748306eef582d2f296b1f60
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229826"
---
# <a name="exporting-from-a-dll-using-def-files"></a>使用 DEF 文件从 DLL 导出

模块定义或 DEF 文件 (*.def) 文件是文本文件，其中包含一个或多个描述 DLL 的各种特性的模块语句。 如果没有使用 `__declspec(dllexport)` 关键字来导出 DLL 的函数，则 DLL 需要 DEF 文件。

最小的 DEF 文件必须包含以下模块定义语句：

- 文件中的第一个语句必须是 LIBRARY 语句。 此语句将 DEF 文件标识为属于 DLL。 LIBRARY 语句后跟 DLL 的名称。 链接器将此名称放置在 DLL 的导入库中。

- EXPORTS 语句列出 DLL 导出的函数的名称和（可选）序号值。 可以通过在函数名称后加一个 at 符号 (@) 和一个数字，为函数分配序号值。 指定序号值时，它们必须在 1 到 N 的范围内，其中 N 是 DLL 导出的函数的数量。 如果要按序号导出函数，请参阅[按序号而不是按名称从 DLL 导出函数](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)以及本主题。

例如，包含用于实现二进制搜索树的代码的 DLL 可能如下所示：

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

如果使用 [MFC DLL 向导](../mfc/reference/mfc-dll-wizard.md)创建 MFC DLL，则向导将为你创建主干 DEF 文件，并自动将它添加到项目中。 添加要导出到此文件的函数的名称。 对于非 MFC DLL，请自己创建 DEF 文件并将它添加到项目。 然后转到“项目”   > “属性”   > “连接器”   > “输入”   > “模块定义文件”  ，并输入 DEF 文件的名称。 为每个配置和平台重复此步骤，或者通过选择“配置 = 所有配置”  和“平台 = 所有平台”  ，对所有配置和平台同时执行此步骤。

如果要导出 C++ 文件中的函数，则必须将修饰名放置在 DEF 文件中，或使用 extern "C" 通过标准 C 链接定义导出函数。 如果需要将修饰名放入 DEF 文件，则可以使用 [DUMPBIN](../build/reference/dumpbin-reference.md) 工具或链接器 [/MAP](../build/reference/map-generate-mapfile.md) 选项来获取这些修饰名。 请注意，编译器生成的修饰名特定于编译器。 如果将 Microsoft C++ 编译器 (MSVC) 生成的修饰名放入 DEF 文件，则链接到 DLL 的应用程序也必须使用相同版本的 MSVC 生成，以便让调用应用程序中的修饰名与 DLL 的 DEF 文件中的导出名称相匹配。

> [!NOTE]
> 使用 Visual Studio 2015 生成的 DLL 可由使用 Visual Studio 2017 或 Visual Studio 2019 生成的应用程序使用。

如果要生成[扩展 DLL](../build/extension-dlls-overview.md) 并使用 DEF 文件导出，请将以下代码放置在包含导出类的头文件的开头和结尾：

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

这些行可确保从 MFC 扩展 DLL 导出（或导入）在内部使用或添加到类的 MFC 变量。 例如，使用 `DECLARE_DYNAMIC` 派生类时，宏会进行扩展以向类添加 `CRuntimeClass` 成员变量。 省略这四行代码可能会导致 DLL 无法正确编译或链接，或是在客户端应用程序链接到 DLL 时导致错误。

生成 DLL 时，链接器使用 DEF 文件创建导出 (.exp) 文件和导入库 (.lib) 文件。 然后，链接器使用导出文件生成 DLL 文件。 隐式链接到 DLL 的可执行文件会在生成时链接到导入库。

请注意，MFC 本身使用 DEF 文件从 MFCx0.dll 导出函数和类。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用 __declspec(dllexport) 从 DLL 导出](exporting-from-a-dll-using-declspec-dllexport.md)

- [使用 AFX_EXT_CLASS 导出和导入](exporting-and-importing-using-afx-ext-class.md)

- [导出 C++ 函数以用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [导出 C 函数以用于 C 或 C++ 语言可执行文件](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 导入到应用程序中](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [.def 文件](reference/module-definition-dot-def-files.md)

- [模块定义语句的规则](reference/rules-for-module-definition-statements.md)

- [修饰名](reference/decorated-names.md)

- [导入和导出内联函数](importing-and-exporting-inline-functions.md)

- [相互导入](mutual-imports.md)

## <a name="see-also"></a>请参阅

[从 DLL 导出](exporting-from-a-dll.md)
