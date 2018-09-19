---
title: 相互导入 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7aee01e72fb8386b6aee7e6a505424b4138f45d7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704834"
---
# <a name="mutual-imports"></a>相互导入

当导入是相互的 （或循环） 时，导出或导入到另一个可执行文件比较复杂。 例如，两个 Dll 导入彼此，类似于相互递归函数的符号。

相互导入可执行文件 (通常为 Dll) 的问题是不可以生成而无需构建其他第一个。 作为输入，每个生成过程需要的其他生成过程生成的导入库。

解决方案是使用带 /DEF 选项，而无需构建可执行文件生成导入库 LIB 实用工具。 使用此实用程序，您可以构建所需的所有导入库不论涉及多少 Dll 或依赖项有多复杂。

用于处理相互导入通用的解决方案是：

1. 每个 DLL 我们依次来看。 （按任意顺序是可行的但某些顺序更优。）如果所有所需的导入库存在并且是当前的运行来生成可执行文件 (DLL) 的链接。 这会生成导入库。 否则，运行 LIB 生成导入库。

   运行 LIB 使用 /DEF 选项将生成具有的其他文件。EXP 扩展。 。EXP 文件必须用于更高版本生成的可执行文件。

1. 使用链接或 LIB 将生成所有的导入库后, 回过头来运行用于生成上一步中没有生成任何可执行文件链接。 请注意，必须在链接行上指定相应的.exp 文件。

   如果您有运行 LIB 实用工具更低，以便为 DLL1 生成导入库，LIB 将会生成文件 DLL1.exp 也。 生成 DLL1.dlll 时，必须使用 DLL1.exp 作为链接的输入。

下图显示了两个相互导入 Dll、 DLL1 和 DLL2 解决方案。 步骤 1 是运行 LIB，与上 DLL1 的 /DEF 选项集。 步骤 1 会产生 DLL1.lib、 导入库和 DLL1.exp。在步骤 2 中的导入库用于生成 DLL2，进而生成导入库 DLL2 的符号。 步骤 3 生成 DLL1，通过使用 DLL1.exp 和 DLL2.lib 作为输入。 请注意，DLL2.exp 文件不必要因为 LIB 未用于生成 DLL2 的导入库。

![通过相互导入链接两个 Dll](../build/media/vc37yj1.gif "通过相互导入链接两个 Dll")<br/>
用相互导入链接两个 DLL

## <a name="limitations-of-afxext"></a>_AFXEXT 的限制

可以使用`_AFXEXT`MFC 扩展 Dll，只要不具有多个层的 MFC 扩展 Dll 的预处理器符号。 如果具有 MFC 扩展 Dll 的调用或派生类中自己的 MFC 扩展 Dll，后者又派生自 MFC 类，必须使用你自己的预处理器符号以避免多义性。

问题是，在 Win32，必须显式声明任何数据作为 **__declspec （dllexport)** 如果从 DLL 导出和 **__declspec （dllimport)** 如果要从 DLL 导入。 在定义`_AFXEXT`，MFC 标头，确保**AFX_EXT_CLASS**已正确定义。

当你具有多个层、 一个符号等**AFX_EXT_CLASS**是不够的因为 MFC 扩展 DLL 可能要导出新类，以及从另一个 MFC 扩展 DLL 导入其他类。 若要解决此问题，使用特殊的预处理器符号，指示要构建 DLL 本身还是使用 DLL。 例如，假设两个 MFC 扩展 Dll，A.dll 和 B.dll。 它们分别导出 A.h 和 B.h 中的某些类。 B.dll 使用 A.dll 中的类。 标头文件将如下所示：

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

A.dll 生成时，它用生成`/D A_IMPL`和 B.dll 生成时，它用生成`/D B_IMPL`。 通过为每个 DLL，使用单独的符号`CExampleB`导出和`CExampleA`时构建 B.dll 导入。 `CExampleA` 导出时构建 A.dll 和 B.dll （或其他某个客户端） 使用时导入。

使用内置时，无法完成这种类型的分层**AFX_EXT_CLASS**和`_AFXEXT`预处理器符号。 上面所述的技术解决了在构建其 Active 技术、 数据库和网络 MFC 扩展 Dll 时，使用 MFC 本身的机制的方式与此问题。

## <a name="not-exporting-the-entire-class"></a>不会导出整个类

当不导出整个类时，您必须确保正确导出由 MFC 宏创建的必需数据项目。 这可以通过重新定义`AFX_DATA`到您的特定类的宏。 每当不导出整个类，就应进行此操作。

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

- [从 DLL 导出](../build/exporting-from-a-dll.md)

- [导出从 DLL 使用。DEF 文件](../build/exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport） 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [导出和导入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [导出 c + + 函数以用于 C 语言可执行文件](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)

- [导入到使用 __declspec （dllimport） 的应用程序](../build/importing-into-an-application-using-declspec-dllimport.md)

### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [LIB 实用工具和 /DEF 选项](../build/reference/lib-reference.md)

## <a name="see-also"></a>请参阅

[导入和导出](../build/importing-and-exporting.md)