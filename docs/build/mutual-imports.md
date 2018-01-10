---
title: "相互导入 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- mutual DLL imports [C++]
- AFX_DATA
- importing DLLs [C++], mutual imports
- mutually importing executable files [C++]
- AFX_EXT_CLASS macro
- circular imports
- _AFXEXT preprocessor symbol
- DLLs [C++], importing
- executable files [C++], importing
- extension DLLs [C++], mutual imports
- exporting DLLs [C++], mutual imports
ms.assetid: 2cc29537-92ee-4d92-af39-8b8b3afd808f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bfd31cd4e5776555137daf002c076e14d4031f89
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mutual-imports"></a>相互导入
当导入是相互 （或循环） 时，导出或导入到另一个可执行文件比较复杂。 例如，两个 Dll 导入相互，类似于相互递归函数的符号。  
  
 相互导入可执行文件 (通常是 Dll) 的问题是都可以生成而不生成其他第一个。 作为输入，每个生成过程需要由其他生成过程产生的导入库。  
  
 解决方案是使用带 /DEF 选项，而不生成可执行文件生成导入库 LIB 实用工具。 使用此实用工具，可以生成你需要的所有导入库涉及无论多少 Dll 或有多复杂依赖关系。  
  
 用于处理相互导入常规解决方法是：  
  
1.  反过来需要每个 DLL。 （任意顺序是可行的但某些顺序更优。）如果所有所需的导入库存在，并且是最新，运行 LINK 生成的可执行文件 (DLL)。 这将生成导入库。 否则，运行 LIB 生成导入库。  
  
     运行 LIB 带 /DEF 选项，将生成具有的其他文件。EXP 扩展。 。EXP 文件必须在稍后用于生成可执行文件。  
  
2.  之后使用链接或 LIB 生成所有导入库，请返回并运行 LINK 生成上一步中没有生成任何可执行文件。 请注意，必须在链接行上指定相应的.exp 文件。  
  
     如果你具有运行 LIB 实用工具前面为 DLL1 生成导入库，LIB 将会产生文件 DLL1.exp 以及。 生成 DLL1.dlll 时，你必须使用 DLL1.exp 作为链接的输入。  
  
 下图显示了两个相互导入 Dll、 DLL1 和 DLL2 的解决方案。 步骤 1 是运行 LIB，与上 DLL1 的 /DEF 选项集。 步骤 1 生成 DLL1.lib、 导入库和 DLL1.exp。在步骤 2 中，导入库用于生成 DLL2，反过来生成导入库 DLL2 的符号。 步骤 3 生成 DLL1，通过使用 DLL1.exp 和 DLL2.lib 作为输入。 请注意，DLL2 了.exp 文件是不必要因为 LIB 未用于生成 DLL2 的导入库。  
  
 ![使用相互导入链接两个 Dll](../build/media/vc37yj1.gif "vc37YJ1")  
用相互导入链接两个 DLL  
  
## <a name="limitations-of-afxext"></a>_AFXEXT 的限制  
 你可以使用`_AFXEXT`MFC 扩展 Dll，只要你没有 MFC 扩展 Dll 的多个层的预处理器符号。 如果你有 MFC 扩展 Dll 可调用或派生自中你自己的 MFC 扩展 Dll，后者又派生自 MFC 类，类必须使用你自己的预处理器符号以避免多义性。  
  
 问题在于该在 Win32，所以必须显式声明为任何数据**__declspec （dllexport)**如果它是从 DLL，导出和**__declspec （dllimport)**是否要从 DLL 导入它。 在定义`_AFXEXT`，MFC 标头确保**AFX_EXT_CLASS**正确定义。  
  
 如果你具有多个层、 一个符号如**AFX_EXT_CLASS**是不够的因为 MFC 扩展 DLL 可能会导出新类，以及从另一个 MFC 扩展 DLL 导入其他类。 若要解决此问题，请使用特殊的预处理器符号，该值指示要生成 DLL 本身还是使用该 DLL。 例如，假设两个 MFC 扩展 Dll、 A.dll 和 B.dll。 每个分别导出 A.h 和 B.h 中的某些类。 B.dll 使用 A.dll 类。 标头文件将如下所示：  
  
```  
/* A.H */  
#ifdef A_IMPL  
   #define CLASS_DECL_A   __declspec(dllexport)  
#else  
   #define CLASS_DECL_A   __declspec(dllimport)  
#endif  
  
class CLASS_DECL_A CExampleA : public CObject  
{ ... class definition ... };  
  
// B.H  
#ifdef B_IMPL  
   #define CLASS_DECL_B   __declspec(dllexport)  
#else  
   #define CLASS_DECL_B   __declspec(dllimport)  
#endif  
  
class CLASS_DECL_B CExampleB : public CExampleA  
{ ... class definition ... };  
...  
```  
  
 A.dll 生成时，它用生成`/D A_IMPL`和 B.dll 生成时，它用生成`/D B_IMPL`。 每个 DLL，使用单独的符号`CExampleB`导出和`CExampleA`时生成 B.dll，导入。 `CExampleA`导出时生成 A.dll 和导入由 B.dll （或某些其他客户端）。  
  
 使用内置时，无法完成这种类型的分层**AFX_EXT_CLASS**和`_AFXEXT`预处理器符号。 上面所述的技术可解决此问题的机制 MFC 本身使用其 Active 技术、 数据库和网络 MFC 扩展 Dll 进行生成时的方式与在。  
  
## <a name="not-exporting-the-entire-class"></a>不会导出整个类  
 当不导出整个类时，你必须确保正确导出由 MFC 宏创建的必需数据项目。 这可以通过重新定义完成`AFX_DATA`对特定类的宏。 每当不导出整个类的时候，你应进行此操作。  
  
 例如:  
  
```  
/* A.H */  
#ifdef A_IMPL  
   #define CLASS_DECL_A  _declspec(dllexport)  
#else  
   #define CLASS_DECL_A  _declspec(dllimport)  
#endif  
  
#undef  AFX_DATA  
#define AFX_DATA CLASS_DECL_A  
  
class CExampleA : public CObject  
{  
   DECLARE_DYNAMIC()  
   CLASS_DECL_A int SomeFunction();  
   //... class definition ...  
};  
  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
### <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [从 DLL 导出](../build/exporting-from-a-dll.md)  
  
-   [从 DLL 使用导出。DEF 文件](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport） 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [导出和导入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [导出 C 语言可执行文件中使用的 c + + 函数](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [导入使用 __declspec （dllimport） 的应用程序](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [LIB 实用工具和 /DEF 选项](../build/reference/lib-reference.md)  
  
## <a name="see-also"></a>请参阅  
 [导入和导出](../build/importing-and-exporting.md)