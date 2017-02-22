---
title: "使用 DEF 文件从 DLL 导出 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".def 文件 [C++], 从 DLL 导出"
  - "def 文件 [C++], 从 DLL 导出"
  - "导出 DLL [C++], DEF 文件"
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用 DEF 文件从 DLL 导出
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模块定义 \(.def\) 文件是包含一个或多个描述 DLL 各种特性的 Module 语句的文本文件。  如果不使用 **\_\_declspec\(dllexport\)** 关键字导出 DLL 的函数，则 DLL 需要 .def 文件。  
  
 .def 文件必须至少包含下列模块定义语句：  
  
-   文件中的第一个语句必须是 LIBRARY 语句。  此语句将 .def 文件标识为属于 DLL。  LIBRARY 语句的后面是 DLL 的名称。  链接器将此名称放到 DLL 的导入库中。  
  
-   EXPORTS 语句列出名称，可能的话还会列出 DLL 导出函数的序号值。  通过在函数名的后面加上 @ 符和一个数字，给函数分配序号值。  当指定序号值时，序号值的范围必须是从 1 到 N，其中 N 是 DLL 导出函数的个数。  如果希望按序号导出函数，请参见[按序号而不是按名称从 DLL 导出函数](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)以及本主题。  
  
 例如，包含实现二进制搜索树的代码的 DLL 看上去可能像下面这样：  
  
```  
LIBRARY   BTREE  
EXPORTS  
   Insert   @1  
   Delete   @2  
   Member   @3  
   Min   @4  
```  
  
 如果使用 [MFC DLL 向导](../mfc/reference/mfc-dll-wizard.md)创建 MFC DLL，则向导将为您创建主干 .def 文件并将其自动添加到项目中。  添加要导出到此文件的函数名。  对于非 MFC DLL，必须亲自创建 .def 文件并将其添加到项目中。  
  
 如果导出 C\+\+ 文件中的函数，必须将修饰名放到 .def 文件中，或者通过使用外部“C”定义具有标准 C 链接的导出函数。  如果需要将修饰名放到 .def 文件中，则可以通过使用 [DUMPBIN](../build/reference/dumpbin-reference.md) 工具或 [\/MAP](../build/reference/map-generate-mapfile.md) 链接器选项来获取修饰名。  请注意，编译器产生的修饰名是编译器特定的。  如果将 Visual C\+\+ 编译器产生的修饰名放到 .def 文件中，则链接到 DLL 的应用程序必须也是用相同版本的 Visual C\+\+ 生成的，这样调用应用程序中的修饰名才能与 DLL 的 .def 文件中的导出名相匹配。  
  
 如果生成[扩展 DLL](../build/extension-dlls-overview.md) 并使用 .def 文件导出，则将下列代码放在包含导出类的头文件的开头和结尾：  
  
```  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
 这些代码行确保内部使用的 MFC 变量或添加到类的变量是从扩展 DLL 导出（或导入）的。  例如，当使用 `DECLARE_DYNAMIC` 派生类时，该宏扩展以将 `CRuntimeClass` 成员变量添加到类。  省去这四行代码可能会导致不能正确编译或链接 DLL，或在客户端应用程序链接到 DLL 时导致错误。  
  
 当生成 DLL 时，链接器使用 .def 文件创建导出 \(.exp\) 文件和导入库 \(.lib\) 文件。  然后，链接器使用导出文件生成 DLL 文件。  隐式链接到 DLL 的可执行文件在生成时链接到导入库。  
  
 请注意，MFC 本身使用 .def 文件从 MFCx0.dll 导出函数和类。  
  
## 你希望做什么？  
  
-   [使用 \_\_declspec\(dllexport\) 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [使用 AFX\_EXT\_CLASS 导出和导入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [导出 C\+\+ 函数以用于 C 语言可执行文件](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [导出 C 函数以用于 C 或 C\+\+ 语言可执行文件](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [使用 \_\_declspec\(dllimport\) 导入到应用程序中](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您想进一步了解什么？  
  
-   [.def 文件](../build/reference/module-definition-dot-def-files.md)  
  
-   [模块定义语句的规则](../build/reference/rules-for-module-definition-statements.md)  
  
-   [修饰名](../build/reference/decorated-names.md)  
  
-   [导入和导出内联函数](../build/importing-and-exporting-inline-functions.md)  
  
-   [相互导入](../build/mutual-imports.md)  
  
## 请参阅  
 [从 DLL 导出](../build/exporting-from-a-dll.md)