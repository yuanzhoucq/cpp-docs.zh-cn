---
title: 使用 DEF 文件从 DLL 导出
ms.date: 01/09/2018
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: 35f55ea525bd03c5b0b1b1750d25c1223bc608fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195470"
---
# <a name="exporting-from-a-dll-using-def-files"></a>使用 DEF 文件从 DLL 导出

模块定义或 DEF 文件 (*.def) 是包含一个或多个描述 DLL 各种特性的 module 语句的文本文件。 如果不使用 **__declspec （dllexport)** 关键字导出 DLL 的函数，则 DLL 需要 DEF 文件。

最小的 DEF 文件必须包含以下模块定义语句：

- 在文件中的第一个语句必须是 LIBRARY 语句。 此语句将 DEF 文件标识为属于 DLL。 LIBRARY 语句后跟的 DLL 的名称。 链接器将此名称放在 DLL 的导入库中。

- EXPORTS 语句列出名称和 DLL 导出的函数的序号值 （可选）。 按照函数的名称加上分配函数的序号值 at 符号 (@) 和一个数字。 当指定序号值时，它们必须是介于 1 到 N，其中 N 是 DLL 导出函数的数目。 如果你想要按序号导出函数，请参阅[从按序号而不是按名称的 DLL 导出函数](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)以及本主题。

例如，包含用于实现二进制搜索树的代码的 DLL 可能看上去如下所示：

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

如果您使用[MFC DLL 向导](../mfc/reference/mfc-dll-wizard.md)若要创建非 MFC DLL，该向导将为您创建主干 DEF 文件并自动将其添加到你的项目。 添加到此文件导出的函数的名称。 对于非 MFC Dll，自行创建 DEF 文件，并将其添加到你的项目。 然后转到**项目** > **属性** > **链接器** > **输入** > **模块定义文件**并输入 DEF 文件的名称。 重复此步骤为每个配置和平台，或通过选择一次性执行其操作**配置 = 所有配置**，并**平台都 = 所有平台**。

如果要导出中的函数C++文件中，您必须将修饰的名放在 DEF 文件或使用 extern"C"定义具有标准 C 链接的导出的函数。 如果你需要将修饰的名放在 DEF 文件中，你可以通过使用获取它们[DUMPBIN](../build/reference/dumpbin-reference.md)工具或通过使用链接器[/map](../build/reference/map-generate-mapfile.md)选项。 请注意，由编译器产生的修饰的名特定的编译器。 如果将视觉对象产生的修饰的名C++到 DEF 文件的编译器，链接到 DLL 的应用程序也必须生成使用相同版本的视觉对象C++，以便调用应用程序中的修饰的名与中的导出的名相匹配DLL 的 DEF 文件。

如果您正在构建[扩展 DLL](../build/extension-dlls-overview.md)，并导出使用 DEF 文件，将以下代码放在开头和末尾包含导出的类的头文件：

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

这些代码行确保内部使用，或添加到您的类的 MFC 变量从 MFC 扩展 DLL 导出 （或导入）。 例如，在派生类使用`DECLARE_DYNAMIC`，该宏扩展以添加`CRuntimeClass`到您的类的成员变量。 省去这四行代码可能会导致您的 DLL 要编译或链接不正确或客户端应用程序链接到 DLL 时导致错误。

当生成 DLL 时，链接器使用 DEF 文件以创建一个导出 (.exp) 文件和导入库 (.lib) 文件。 链接器然后使用该导出文件生成 DLL 文件。 在生成时隐式链接导入库的 DLL 链接到可执行文件。

请注意，MFC 本身使用 DEF 文件从 MFCx0.dll 导出函数和类。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用 __declspec （dllexport） 从 DLL 导出](exporting-from-a-dll-using-declspec-dllexport.md)

- [导出和导入使用 AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [导出C++函数以用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [导出 C 函数以用于 C 或C++-语言可执行文件](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 导入到应用程序中](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [.def 文件](reference/module-definition-dot-def-files.md)

- [模块定义语句的规则](reference/rules-for-module-definition-statements.md)

- [修饰的名](reference/decorated-names.md)

- [导入和导出内联函数](importing-and-exporting-inline-functions.md)

- [相互导入](mutual-imports.md)

## <a name="see-also"></a>请参阅

[从 DLL 导出](exporting-from-a-dll.md)
