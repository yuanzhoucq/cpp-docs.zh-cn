---
title: 使用 DEF 文件从 DLL 导出
ms.date: 05/06/2019
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: 6f7d58bcb42edd89527fff41b08a15321722a6cf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078524"
---
# <a name="exporting-from-a-dll-using-def-files"></a>使用 DEF 文件从 DLL 导出

模块定义或 .DEF 文件（* .def）是一个文本文件，其中包含一个或多个模块语句，这些语句描述了 DLL 的各种属性。 如果不使用 **__declspec （dllexport）** 关键字来导出 dll 的函数，则 DLL 需要使用 DEF 文件。

最小的 .DEF 文件必须包含以下模块定义语句：

- 文件中的第一个语句必须是 LIBRARY 语句。 此语句将定义文件标识为属于 DLL。 LIBRARY 语句后跟 DLL 的名称。 链接器将此名称放在 DLL 的导入库中。

- 导出语句列出了名称和 DLL 导出的函数的序号值（可选）。 您可以通过在函数名称后加一个 at 符号（@）和一个数字，为该函数分配一个序号值。 指定序号值时，它们必须在1到 N 的范围内，其中 N 是 DLL 导出的函数的数目。 如果要按序号导出函数，请参阅[按序号而不是按名称从 DLL 导出函数](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)，以及本主题。

例如，包含用于实现二进制搜索树的代码的 DLL 可能如下所示：

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

如果使用[MFC Dll 向导](../mfc/reference/mfc-dll-wizard.md)创建 mfc dll，则向导将为您创建一个主干定义文件，并自动将其添加到您的项目中。 添加要导出到此文件的函数的名称。 对于非 MFC Dll，请自行创建 .DEF 文件并将其添加到项目。 然后 **，在 "** 链接器" > **属性**" > **链接器** > **输入** > **模块定义文件**中，输入 DEF 文件的名称。 为每个配置和平台重复此步骤，或选择 "配置" = "**所有配置**"，并选择 "**平台 = 所有平台**"，同时执行所有操作。

如果要导出C++文件中的函数，则必须将修饰名放在 .def 文件中，或使用 Extern "c" 将导出函数定义为标准 C 链接。 如果需要将修饰名放在 .DEF 文件中，可以使用[DUMPBIN](../build/reference/dumpbin-reference.md)工具或链接器[/MAP](../build/reference/map-generate-mapfile.md)选项获取它们。 请注意，编译器生成的修饰名是编译器特定的。 如果将 Microsoft C++编译器（MSVC）生成的修饰名放入 .def 文件，则链接到 DLL 的应用程序也必须使用相同版本的 MSVC 生成，以便调用应用程序中的修饰名与 DLL 的 .def 文件中的导出名称匹配。

> [!NOTE]
> 使用 visual studio 2015 生成的 DLL 可由使用 Visual Studio 2017 或 Visual Studio 2019 构建的应用程序使用。

如果要生成[扩展 DLL](../build/extension-dlls-overview.md)，并使用 DEF 文件导出，请将以下代码放置在头文件的开头和结尾，其中包含导出的类：

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

这些行可确保从 MFC 扩展 DLL 中导出（或导入）从内部使用或添加到类的 MFC 变量。 例如，使用 `DECLARE_DYNAMIC`派生类时，宏将展开以向类添加 `CRuntimeClass` 成员变量。 省略这四行代码可能会导致您的 DLL 无法正确编译或链接，或在客户端应用程序链接到 DLL 时导致错误。

生成 DLL 时，链接器使用 DEF 文件创建导出（.exp）文件和导入库（.lib）文件。 然后，链接器使用导出文件生成 DLL 文件。 隐式链接到 DLL 的可执行文件在生成时链接到导入库。

请注意，MFC 本身使用 DEF 文件从 MFCx0 导出函数和类。

## <a name="what-do-you-want-to-do"></a>您希望做什么？

- [使用 __declspec （dllexport）从 DLL 导出](exporting-from-a-dll-using-declspec-dllexport.md)

- [使用 AFX_EXT_CLASS 进行导出和导入](exporting-and-importing-using-afx-ext-class.md)

- [导出C++函数以用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [导出 C 函数以用于 C 或C++语言可执行文件](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 导入到应用程序中](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [.def 文件](reference/module-definition-dot-def-files.md)

- [模块定义语句的规则](reference/rules-for-module-definition-statements.md)

- [修饰名](reference/decorated-names.md)

- [导入和导出内联函数](importing-and-exporting-inline-functions.md)

- [相互导入](mutual-imports.md)

## <a name="see-also"></a>另请参阅

[从 DLL 导出](exporting-from-a-dll.md)
