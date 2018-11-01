---
title: 使用 DEF 文件从 DLL 导出
ms.date: 11/04/2016
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: e4351d8eca6c6c580430aa8988344bf7f57e0a9f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553902"
---
# <a name="exporting-from-a-dll-using-def-files"></a>使用 DEF 文件从 DLL 导出

模块定义 (.def) 文件是包含一个或多个描述 DLL 各种特性的 module 语句的文本文件。 如果不使用 **__declspec （dllexport)** 关键字导出 DLL 的函数，则 DLL 需要.def 文件。

.Def 文件必须包含以下模块定义语句：

- 在文件中的第一个语句必须是 LIBRARY 语句。 此语句将.def 文件标识为属于 DLL。 LIBRARY 语句后跟的 DLL 的名称。 链接器将此名称放在 DLL 的导入库中。

- EXPORTS 语句列出名称和 DLL 导出的函数的序号值 （可选）。 按照函数的名称加上分配函数的序号值 at 符号 (@) 和一个数字。 当指定序号值时，它们必须是介于 1 到 N，其中 N 是 DLL 导出函数的数目。 如果你想要按序号导出函数，请参阅[从按序号而不是按名称的 DLL 导出函数](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)以及本主题。

例如，包含用于实现二进制搜索树的代码的 DLL 可能看上去如下所示：

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

如果您使用[MFC DLL 向导](../mfc/reference/mfc-dll-wizard.md)若要创建非 MFC DLL，该向导将为您创建主干.def 文件并自动将其添加到你的项目。 添加到此文件导出的函数的名称。 对于非 MFC Dll，您必须亲自创建.def 文件并将其添加到你的项目。

如果导出 c + + 文件中的函数，您必须将修饰的名放到.def 文件中或通过使用 extern"C"定义具有标准 C 链接的导出的函数。 如果你需要将修饰的名放到.def 文件中，你可以通过使用获取它们[DUMPBIN](../build/reference/dumpbin-reference.md)工具或通过使用链接器[/map](../build/reference/map-generate-mapfile.md)选项。 请注意，由编译器产生的修饰的名特定的编译器。 如果您将放入.def 文件由 Visual c + + 编译器产生的修饰的名，也必须使用相同版本的 Visual c + +，以便调用应用程序中的修饰的名匹配的导出的名在 DLL 的.de 生成链接到 DLL 的应用程序f 文件。

如果您正在构建[扩展 DLL](../build/extension-dlls-overview.md)，并导出使用.def 文件，将以下代码放在开头和末尾包含导出的类的头文件：

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

这些代码行确保内部使用，或添加到您的类的 MFC 变量从 MFC 扩展 DLL 导出 （或导入）。 例如，在派生类使用`DECLARE_DYNAMIC`，该宏扩展以添加`CRuntimeClass`到您的类的成员变量。 省去这四行代码可能会导致您的 DLL 要编译或链接不正确或客户端应用程序链接到 DLL 时导致错误。

当生成 DLL 时，链接器使用.def 文件以创建一个导出 (.exp) 文件和导入库 (.lib) 文件。 链接器然后使用该导出文件生成 DLL 文件。 在生成时隐式链接导入库的 DLL 链接到可执行文件。

请注意，MFC 本身使用.def 文件从 MFCx0.dll 导出函数和类。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用 __declspec （dllexport） 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [导出和导入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [导出 c + + 函数以用于 C 语言可执行文件](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [导出 C 函数以用于 C 或 c + + 语言可执行文件](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)

- [导入到使用 __declspec （dllimport） 的应用程序](../build/importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [.def 文件](../build/reference/module-definition-dot-def-files.md)

- [模块定义语句的规则](../build/reference/rules-for-module-definition-statements.md)

- [修饰的名](../build/reference/decorated-names.md)

- [导入和导出内联函数](../build/importing-and-exporting-inline-functions.md)

- [相互导入](../build/mutual-imports.md)

## <a name="see-also"></a>请参阅

[从 DLL 导出](../build/exporting-from-a-dll.md)