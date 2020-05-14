---
title: 相互导入
ms.date: 11/04/2016
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
ms.openlocfilehash: f01e69138a6ca1744645a1c2fa8525b7088e260d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295666"
---
# <a name="mutual-imports"></a>相互导入

如果导入是相互的（或循环的），则导出或导入到另一个可执行文件会比较复杂。 例如，两个 DLL 相互导入符号，类似于相互递归函数。

相互导入可执行文件（通常是 DLL）的问题在于，如果不首先生成一个文件，则无法生成另一个文件。 每个生成过程都需要其他生成过程生成的导入库作为输入。

解决方案是使用 LIB 实用工具和 /DEF 选项生成导入库，但不生成可执行文件。 使用此实用工具，你可以生成所需的所有导入库，无论涉及多少 DLL，也不管依赖项有多复杂。

处理相互导入的一般解决方案是：

1. 依次采用每个 DLL。 （任意顺序都是可行的，尽管有些顺序会更好。）如果所有所需的导入库都存在并且都是最新的，请运行 LINK 以生成可执行文件 (DLL)。 这会生成一个导入库。 否则，请运行 LIB 以生成导入库。

   使用 /DEF 选项运行 LIB 将生成具有 .EXP 扩展 的其他文件。 稍后必须使用 .EXP 文件来生成可执行文件。

1. 使用 LINK 或 LIB 生成所有导入库后，返回并运行 LINK 以生成上一步骤中未生成的任何可执行文件。 请注意，必须在 LINK 行上指定相应的 .exp 文件。

   如果之前通过运行 LIB 实用工具已生成 DLL1 的导入库，则 LIB 应也已会生成文件 DLL1.exp。 生成 DLL1.dlll 时，必须使用 DLL1.exp 作为 LINK 的输入。

下图显示了两个相互导入 DLL（DLL1 和 DLL2）的解决方案。 步骤 1 是在 DLL1 上使用 /DEF 选项集运行 LIB。 步骤 1 会生成导入库 DLL1.lib 和 DLL1.exp。在步骤 2 中，导入库用于生成 DLL2，而 DLL2 又为 DLL2 的符号生成导入库。 步骤 3 使用 DLL1.exp 和 DLL2.lib 作为输入生成 DLL1。 请注意，DLL2 的 .exp 文件不是必需的，因为 LIB 不用于生成 DLL2 的导入库。

![使用相互导入链接两个 DLL](media/vc37yj1.gif "Using mutual imports to link two DLLs")<br/>
用相互导入链接两个 DLL

## <a name="limitations-of-_afxext"></a>_AFXEXT 的限制

只要没有多层 MFC 扩展 DLL，就可以对 MFC 扩展 DLL 使用 `_AFXEXT` 预处理器符号。 如果 MFC 扩展 DLL 调用或派生自你自己的 MFC 扩展 DLL 中的类，然后从 MFC 类派生，则必须使用你自己的预处理器符号以避免歧义。

问题在于，在 Win32 中，如果要从 DLL 中导出任何数据，必须显式将其声明为 __declspec(dllexport)，如果要从 DLL 中导入任何数据，则必须显式将其声明为 __declspec(dllimport)   。 定义 `_AFXEXT` 时，MFC 标头确保了正确定义 AFX_EXT_CLASS  。

如果有多个层，则一种符号（如 AFX_EXT_CLASS）是不够的，因为 MFC 扩展 DLL 可能正在导出新类，或者正在从其他 MFC 扩展 DLL 导入其他类  。 若要解决此问题，请使用一个特殊的预处理器符号，指示你正在生成 DLL 本身，而不是正在使用 DLL。 例如，假设两个 MFC 扩展 DLL：A.dll 和 B.dll。 它们各自分别导出 A.h 和 B.h 中的一些类。 B.dll 使用 A.dll 中的类。 头文件类似于以下形式：

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

生成 A.dll 时，它是使用 `/D A_IMPL` 生成的，生成 B.dll 时，它是使用 `/D B_IMPL` 生成的。 通过对每个 DLL 使用单独的符号，在生成 B.dll 时导出 `CExampleB` 并导入 `CExampleA`。 `CExampleA` 在生成 A.dll 时导出，在被 B.dll（或其他客户端）使用时导入。

使用内置 AFX_EXT_CLASS 和 `_AFXEXT` 预处理器符号时，无法执行这种类型的分层  。 上述技术采用了一种不同于 MFC 本身在生成其活动技术、数据库和网络 MFC 扩展 DLL 时使用的机制来解决此问题。

## <a name="not-exporting-the-entire-class"></a>不导出整个类

如果不导出整个类，必须确保正确导出由 MFC 宏创建的必需数据项。 此操作可通过对特定类的宏重新定义 `AFX_DATA` 来完成。 只要不导出整个类，可随时执行此操作。

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

### <a name="what-do-you-want-to-do"></a>你希望做什么？

- [从 DLL 导出](exporting-from-a-dll.md)

- [使用 .DEF 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec(dllexport) 从 DLL 导出](exporting-from-a-dll-using-declspec-dllexport.md)

- [使用 AFX_EXT_CLASS 导出和导入](exporting-and-importing-using-afx-ext-class.md)

- [导出 C++ 函数以用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 导入到应用程序中](importing-into-an-application-using-declspec-dllimport.md)

### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [LIB 实用工具和 /DEF 选项](reference/lib-reference.md)

## <a name="see-also"></a>请参阅

[导入和导出](importing-and-exporting.md)
