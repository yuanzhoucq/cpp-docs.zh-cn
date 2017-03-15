---
title: "相互导入 | Microsoft Docs"
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
  - "_AFXEXT 预处理器符号"
  - "AFX_DATA"
  - "AFX_EXT_CLASS 宏"
  - "循环导入"
  - "DLL [C++], 导入"
  - "可执行文件 [C++], 导入"
  - "导出 DLL [C++], 相互导入"
  - "扩展 DLL [C++], 相互导入"
  - "导入 DLL [C++], 相互导入"
  - "DLL 相互导入 [C++]"
  - "相互导入可执行文件 [C++]"
ms.assetid: 2cc29537-92ee-4d92-af39-8b8b3afd808f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 相互导入
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当导入是相互的（或循环）时，导出或导入到另一个可执行文件比较复杂。  例如，两个 DLL 相互导入符号，类似于相互递归函数。  
  
 相互导入可执行文件（通常是 DLL）的问题是：两个文件中若不先生成一个，就无法生成另一个。  每个生成过程都需要由其他生成过程产生的导入库作为输入。  
  
 解决方案是使用带 \/DEF 选项的 LIB 实用工具，这将产生导入库但不生成可执行文件。  使用此实用工具可以生成需要的所有导入库，而不论涉及多少 DLL 或依赖项有多复杂。  
  
 处理相互导入的一般解决方案是：  
  
1.  轮流采用每个 DLL。（可以使用任何顺序，但某些顺序的性能更优化。）如果所有需要的导入库都存在并且都是当前库，则运行 LINK 生成可执行文件 \(DLL\)。  这将产生导入库。  否则，运行 LIB 产生导入库。  
  
     运行带 \/DEF 选项的 LIB 生成带 .EXP 扩展名的附加文件。  以后必须使用 .EXP 文件生成可执行文件。  
  
2.  使用 LINK 或 LIB 生成了所有导入库后，返回并运行 LINK 以生成上一步中未生成的任何可执行文件。  请注意，必须在 LINK 行上指定相应的 .exp 文件。  
  
     如果以前运行了 LIB 实用工具为 DLL1 产生导入库，则 LIB 应该还产生了 DLL1.exp 文件。  生成 DLL1.dll 时，必须使用 DLL1.exp 作为 LINK 的输入。  
  
 下面的示例演示如何对两个 DLL（DLL1 和 DLL2）进行互相导入。  步骤 1 在 DLL1 上运行带 \/DEF 选项的 LIB。  步骤 1 产生 DLL1.lib（导入库）和 DLL1.exp。  在步骤 2 中，使用导入库生成 DLL2，DLL2 反过来为 DLL2 的符号产生导入库。  步骤 3 通过使用 DLL1.exp 和 DLL2.lib 作为输入来生成 DLL1。  请注意，DLL2 的 .exp 文件不是必需的，因为 LIB 未用于生成 DLL2 的导入库。  
  
 ![通过相互导入链接两个 DLL](../build/media/vc37yj1.png "vc37YJ1")  
用相互导入链接两个 DLL  
  
## \_AFXEXT 的限制  
 只要不具有多层扩展 DLL，就可以对扩展 DLL 使用 `_AFXEXT` 预处理器符号。  如果所具有的扩展 DLL 调用或派生自您自己的扩展 DLL 中的类，而您自己的扩展 DLL 又派生自 MFC 类，则必须使用您自己的预处理器符号以避免多义性。  
  
 问题是，在 Win32 中，必须将任何要从 DLL 导出的数据显式声明为 **\_\_declspec\(dllexport\)**，将任何要从 DLL 导入的数据显式声明为 **\_\_declspec\(dllimport\)**。  当您定义 `_AFXEXT` 时，MFC 头文件确定 **AFX\_EXT\_CLASS** 的定义是正确的。  
  
 当具有多层时，一个符号（如 **AFX\_EXT\_CLASS**）是不够的，因为扩展 DLL 除了从另一个扩展 DLL 导入其他类外，还可能导出新类。  若要解决此问题，请使用一个特殊的预处理器符号来指示是生成 DLL 本身还是使用 DLL。  例如，假设有两个扩展 DLL：A.dll 和 B.dll。  它们分别在 A.h 和 B.h 中导出一些类。  B.dll 使用 A.dll 中的类。  头文件看上去像下面这样：  
  
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
  
 生成 A.dll 时，它是用 `/D A_IMPL` 生成的；而生成 B.dll 时，则是用 `/D B_IMPL` 生成的。  通过对每个 DLL 使用不同的符号，在生成 B.dll 时导出 `CExampleB` 而导入 `CExampleA`。  在生成 A.dll 时导出 `CExampleA`，而当它由 B.dll（或某些其他客户端）使用时则被导入。  
  
 当使用内置 **AFX\_EXT\_CLASS** 和 `_AFXEXT` 预处理器符号时，是无法完成这种分层的。  上面描述的技术解决此问题的方式与 MFC 本身在生成其 Active 技术、数据库和网络扩展 DLL 时所使用的机制不同。  
  
## 不导出整个类  
 当不导出整个类时，需确保正确导出由 MFC 宏创建的必要数据项。  这可以通过将 `AFX_DATA` 重定义为特定类的宏来完成。  每当不导出整个类的时候，就应进行此操作。  
  
 例如：  
  
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
  
### 你希望做什么？  
  
-   [从 DLL 导出](../build/exporting-from-a-dll.md)  
  
-   [使用 .DEF 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [使用 AFX\_EXT\_CLASS 导出和导入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [导出 C\+\+ 函数以用于 C 语言可执行文件](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [使用 \_\_declspec\(dllimport\) 导入到应用程序中](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
### 您想进一步了解什么？  
  
-   [LIB 实用工具和 \/DEF 选项](../build/reference/lib-reference.md)  
  
## 请参阅  
 [导入和导出](../build/importing-and-exporting.md)