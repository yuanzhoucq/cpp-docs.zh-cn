---
title: 自 Visual C++ 6.0 以来 DLL 延迟加载 Helper 函数所做的更改
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
ms.openlocfilehash: 536729e27c89d068957ea451355957e4a35348ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320613"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>自 Visual C++ 6.0 以来 DLL 延迟加载 Helper 函数所做的更改

如果计算机上有多个版本的 Visual C++，或者如果您定义了自己的帮助程序功能，则可能会受到对 DLL 延迟加载帮助程序功能所做的更改的影响。 例如：

- **__delayLoadHelper**现在 **__delayLoadHelper2**

- **__pfnDliNotifyHook**现在 **__pfnDliNotifyHook2**

- **__pfnDliFailureHook**正在 **__pfnDliFailureHook2**

- **__FUnloadDelayLoadedDLL**现在 **__FUnloadDelayLoadedDLL2**

> [!NOTE]
> 如果使用默认帮助器函数，这些更改不会影响您。 对于调用链接器的方式，没有更改。

## <a name="multiple-versions-of-visual-c"></a>可视化C++的多个版本

如果计算机上有多个版本的 Visual C++，请确保链接器与 delayimp.lib 匹配。 如果不匹配，您将获得链接器错误报告或`___delayLoadHelper2@8``___delayLoadHelper@8`作为未解析的外部符号。 前者意味着一个新的链接器与旧的delayimp.lib，后者意味着一个旧链接器与一个新的delayimp.lib。

如果收到未解析的链接器错误，则在 delayimp.lib 上运行[转储bin/linker成员](linkermember.md)：1，您希望该函数包含帮助器函数，以查看定义哪个帮助器函数。 帮助器函数也可以在对象文件中定义;也可以在对象文件中定义帮助器函数。运行[转储 bin /符号](symbols.md)并查找`delayLoadHelper(2)`。

如果您知道您具有 Visual C++ 6.0 链接器，则：

- 在延迟加载帮助器的 .lib 或 .obj 文件上运行转储bin，以确定它是否定义 **__delayLoadHelper2**。 如果没有，链接将失败。

- 在延迟加载帮助器的 .lib 或 .obj 文件中定义 **__delayLoadHelper。**

## <a name="user-defined-helper-function"></a>用户定义的帮助器功能

如果您定义了自己的帮助器功能并使用当前版本的 Visual C++，请执行以下操作：

- 将帮助器函数重命名为 **__delayLoadHelper2**。

- 由于延迟描述符中的指针（delayimp.h 中的 ImgDelayDescr）已经从绝对地址 （VA） 更改为相对地址 （RVA），在 32 位和 64 位程序中按预期方式工作，因此您需要将这些指针转换回指针。 引入了一项新功能：PFromRva，在 delayhlp.cpp中发现。 可以在描述符中的每个字段上使用此函数将它们转换回 32 位或 64 位指针。 默认延迟加载帮助器函数仍然是一个很好的模板，用作示例。

## <a name="load-all-imports-for-a-delay-loaded-dll"></a>加载延迟加载 DLL 的所有导入

链接器可以从指定的延迟加载 DLL 加载所有导入。 有关详细信息[，请参阅加载所有导入以了解延迟加载 DLL。](loading-all-imports-for-a-delay-loaded-dll.md)

## <a name="see-also"></a>另请参阅

[了解 Helper 函数](understanding-the-helper-function.md)
