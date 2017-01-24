---
title: "确定要使用的导出方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
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
  - "__declspec(dllexport) 关键字 [C++]"
  - "def 文件 [C++], 从 DLL 导出"
  - "导出 DLL [C++], 方法比较"
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 确定要使用的导出方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以通过 .def 文件或 `__declspec(dllexport)` 关键字导出函数。  为了帮助您决定哪种方法对 DLL 更好，请考虑以下问题：  
  
-   您计划以后导出更多函数吗？  
  
-   您的DLL只能被可以重新生成的应用程序使用，还是那些不能重新生成的应用程序使用，例如由第三方创建的应用程序？  
  
## 使用 .DEF 文件的优缺点  
 在 .def 文件中导出函数使您得以控制导出序号。  当将附加的导出函数添加到 DLL 时，可以给它们分配更高的序号值（高于任何其他导出函数）。  当您进行此操作时，使用隐式链接的应用程序不必与包含新函数的导入库重新链接。  这非常方便，如果您设计的 DLL 供多个应用程序使用，因为您可以添加新功能并确保它继续正常被已依赖于它的应用程序使用。  例如，MFC的DLL 使用 .def 文件生成。  
  
 要使用 .def 文件的另一个优点是可以使用 `NONAME` 属性导出函数。  这在 DLL 的导出表仅生成序号。  对具有大量导出函数的 DLL，使用 `NONAME`属性可以减小 DLL 文件的大小。  有关如何编写模块定义语句的信息，请参见 [模块定义语句的规则](../build/reference/rules-for-module-definition-statements.md)。  有关序号导出的信息，请参见 [按序号而不是按名称从 DLL 导出函数](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。  
  
 使用 .def 文件的主要缺点是：在 C\+\+ 文件中导出函数时，必须将修饰名放到 .def 文件中，或者通过使用外部“C”定义导出函数，以避免编译器进行名称修饰。  
  
 如果您将修饰名放到 .def 文件中，则可以通过使用 [DUMPBIN](../build/reference/dumpbin-reference.md) 工具或 [\/MAP](../build/reference/map-generate-mapfile.md) 链接器选项来获取修饰名。  由编译器产生的修饰名是编译器特定的；因此，如果将由某个编译器产生的修饰名放到 .def 文件中，则链接到 DLL 的应用程序必须也使用相同版本的编译器生成，以便使应用程序中的修饰名称与 DLL 的 .def 文件的 EXPORTS 的名称相适应。  
  
## 使用 \_\_declspec\(dllexport\) 的优缺点  
 使用 `__declspec(dllexport)`  非常方便，因为不必考虑维护 .def 文件和获取导出函数的修饰名。  但是，这种优势受限于您想重新生成的链接的应用程序的数目。  如果通过新的导出函数重新生成 DLL，还必须重新生成应用程序，因为如果使用不同版本的编译器进行重新编译，则导出的 C\+\+ 函数的修饰名可能会发生变化。  
  
### 你希望做什么？  
  
-   [使用 .DEF 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [使用 AFX\_EXT\_CLASS 导出和导入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [导出 C\+\+ 函数以用于 C 语言可执行文件](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [导出 C 函数以用于 C 或 C\+\+ 语言可执行文件](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [使用 \_\_declspec\(dllimport\) 导入到应用程序中](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
### 您想进一步了解什么？  
  
-   [导入和导出内联函数](../build/importing-and-exporting-inline-functions.md)  
  
-   [相互导入](../build/mutual-imports.md)  
  
-   [修饰名](../build/reference/decorated-names.md)  
  
## 请参阅  
 [从 DLL 导出](../build/exporting-from-a-dll.md)