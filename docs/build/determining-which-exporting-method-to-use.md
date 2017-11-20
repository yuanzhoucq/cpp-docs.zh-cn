---
title: "确定要使用的导出方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 013620a6353c281b2d60a8c4f847f57c60e5f10c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="determining-which-exporting-method-to-use"></a>确定要使用的导出方法
您可以通过两种方法导出函数 - .def 文件或 `__declspec(dllexport)` 关键字。 为了帮助您决定哪种方法更适合您的 DLL，请考虑以下问题：  
  
-   您是否计划以后导出更多函数？  
  
-   您的 DLL 是只由可以重新生成的应用程序使用，还是由无法重新生成的应用程序使用（例如，由第三方创建的应用程序）？  
  
## <a name="pros-and-cons-of-using-def-files"></a>使用 .def 文件的优缺点  
 通过在 .def 文件中导出函数，您可以控制导出序号。 将导出函数添加到 DLL 后，您可以为其赋予高于任何其他导出函数的序号值。 执行此操作后，使用隐式链接的应用程序不必与包含新函数的导入库重新链接。 如果您要设计由很多应用程序使用的 DLL，那么这非常方便，因为您可以添加新功能，并可以确保该 DLL 可以继续正确地用于已依赖于它的应用程序。 例如，MFC DLL 是使用 .def 文件生成的。  
  
 使用 .def 文件的另一个优点是您可以使用 `NONAME` 特性导出函数。 这只会将序号放入 DLL 中的导出表。 对于具有大量导出函数的 DLL，使用 `NONAME` 特性可以减小 DLL 文件的大小。 有关如何编写的模块定义语句的信息，请参阅[模块定义语句的规则](../build/reference/rules-for-module-definition-statements.md)。 有关序号导出的信息，请参阅[从按序号而不是按名称的 DLL 导出函数](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。  
  
 使用 .def 文件的缺点是：如果在 C++ 文件中导出函数，则必须将修饰名放入 .def 文件，或者使用外部“C”定义导出函数以避免 Visual C++ 编译器进行名称重整。  
  
 如果将修饰的名放.def 文件中，你可以通过使用获取它们[DUMPBIN](../build/reference/dumpbin-reference.md)工具或通过使用链接器[/映射](../build/reference/map-generate-mapfile.md)选项。 编译器生成的修饰名是编译器特定的；因此，如果将编译器生成的修饰名放入.def 文件，则链接到 DLL 的应用程序也必须使用相同版本的编译器生成，以便让调用应用程序中的修饰名与 DLL 的 .def 文件中的导出的名称相匹配。  
  
## <a name="pros-and-cons-of-using-declspecdllexport"></a>使用 __declspec （dllexport） 的利与弊  
 使用 `__declspec(dllexport)` 非常方便，因为您不必为维护 .def 文件和获取导出函数的修饰名操心。 但是，这种效用受限于您要重新生成的链接应用程序的数量。 如果使用新导出重新生成 DLL，则还必须重新生成应用程序，因为如果使用不同版本的编译器重新生成 DLL，导出的 C++ 函数的修饰名可能会发生变化。  
  
### <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [从 DLL 使用导出。DEF 文件](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport） 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [导出和导入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [导出 C 语言可执行文件中使用的 c + + 函数](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [在 C 或 c + + 语言可执行文件中使用的导出 C 函数](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [导入使用 __declspec （dllimport） 的应用程序](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [导入和导出内联函数](../build/importing-and-exporting-inline-functions.md)  
  
-   [相互导入](../build/mutual-imports.md)  
  
-   [修饰的名](../build/reference/decorated-names.md)  
  
## <a name="see-also"></a>另请参阅  
 [从 DLL 导出](../build/exporting-from-a-dll.md)