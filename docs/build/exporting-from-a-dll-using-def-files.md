---
title: "使用 DEF 文件从 DLL 导出 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15806c3e40d45588ec27f1351e583fc5e8e897e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="exporting-from-a-dll-using-def-files"></a>使用 DEF 文件从 DLL 导出
模块定义 (.def) 文件是包含描述的 DLL 的各种属性的一个或多个模块语句的文本文件。 如果你不使用**__declspec （dllexport)**关键字导出的 DLL 函数 DLL 要求的.def 文件。  
  
 最小.def 文件必须包含以下模块定义语句：  
  
-   文件中的第一个语句必须是库语句。 此语句标识为属于 DLL 的.def 文件。 库语句跟 DLL 的名称。 链接器将此名称放在 DLL 导入库。  
  
-   导出语句列出名称和 DLL 导出的函数的序号值，（可选）。 按照函数的名称加上分配函数的序号值 at 符号 (@) 和一个数字。 当指定序号值时，它们必须是介于 1 到 N，其中 N 是 DLL 导出的函数的数量。 如果你想要按序号导出函数，请参阅[从按序号而不是按名称的 DLL 导出函数](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)以及本主题。  
  
 例如，包含用于实现二进制搜索树的代码的 DLL 可能看上去如下所示：  
  
```  
LIBRARY   BTREE  
EXPORTS  
   Insert   @1  
   Delete   @2  
   Member   @3  
   Min   @4  
```  
  
 如果你使用[MFC DLL 向导](../mfc/reference/mfc-dll-wizard.md)若要创建 MFC DLL，该向导将为你创建主干.def 文件并自动将其添加到你的项目。 添加到此文件要导出的函数的名称。 有关非 MFC Dll，你必须自行创建.def 文件，并将其添加到你的项目。  
  
 如果要导出的 c + + 文件中的函数，你必须将修饰的名放入.def 文件或通过使用 extern"C"定义导出的函数与标准 C 链接。 如果你需要将修饰的名放入.def 文件，你可以通过使用获取它们[DUMPBIN](../build/reference/dumpbin-reference.md)工具或通过使用链接器[/映射](../build/reference/map-generate-mapfile.md)选项。 请注意，由编译器生成的修饰的名特定的编译器。 如果你将放入.def 文件由 Visual c + + 编译器生成的修饰的名，也必须使用相同版本的 Visual c + +，以使调用应用程序中的修饰的名相匹配的导出的名在 DLL 的.de 生成链接到 DLL 的应用程序f 文件。  
  
 如果你在构建[扩展 DLL](../build/extension-dlls-overview.md)，并导出使用.def 文件，将下面的代码放在的开头和结尾的头文件包含导出的类：  
  
```  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
 这些代码行确保 MFC 变量，在内部或，它添加到你的类从 MFC 扩展 DLL 导出 （或导入）。 例如，当派生类使用`DECLARE_DYNAMIC`，宏将扩展添加`CRuntimeClass`到您的类的成员变量。 省去这四个行可能会导致 DLL 来编译或链接不正确或在客户端应用程序链接到 DLL 时，会导致错误。  
  
 在生成 DLL 时，链接器将使用.def 文件以创建一个导出 (.exp) 文件和导入库 (.lib) 文件。 然后，链接器使用导出文件来生成 DLL 文件。 在生成时隐式链接导入库的 DLL 链接到可执行文件。  
  
 请注意，MFC 本身使用.def 文件从 MFCx0.dll 中导出的函数和类。  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [使用 __declspec （dllexport） 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [导出和导入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [导出 C 语言可执行文件中使用的 c + + 函数](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [在 C 或 c + + 语言可执行文件中使用的导出 C 函数](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [导入使用 __declspec （dllimport） 的应用程序](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [.def 文件](../build/reference/module-definition-dot-def-files.md)  
  
-   [模块定义语句的规则](../build/reference/rules-for-module-definition-statements.md)  
  
-   [修饰的名](../build/reference/decorated-names.md)  
  
-   [导入和导出内联函数](../build/importing-and-exporting-inline-functions.md)  
  
-   [相互导入](../build/mutual-imports.md)  
  
## <a name="see-also"></a>请参阅  
 [从 DLL 导出](../build/exporting-from-a-dll.md)