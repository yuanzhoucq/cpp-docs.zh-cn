---
title: DLL 中的更改延迟加载 Helper 函数自 Visual c + + 6.0 以来 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0caf74f02b005ef65e8ac30750fdf244ddeeed0d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712265"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>自 Visual C++ 6.0 以来 DLL 延迟加载 Helper 函数所做的更改

如果您的计算机上有多个版本的 Visual c + + 或如果定义自己的帮助器函数，您可能会受到对 DLL 所做的更改延迟加载 helper 函数。 例如：

- **__delayLoadHelper**现在 **__delayLoadHelper2**

- **__pfnDliNotifyHook**现在 **__pfnDliNotifyHook2**

- **__pfnDliFailureHook**现在 **__pfnDliFailureHook2**

- **__FUnloadDelayLoadedDLL**现在 **__FUnloadDelayLoadedDLL2**

> [!NOTE]
>  如果使用的默认帮助器函数，这些更改不会影响你。 没有关于如何调用链接器的更改。

## <a name="multiple-versions-of-visual-c"></a>多个版本的 Visual c + +

如果您的计算机上有多个版本的 Visual c + +，请确保链接器与 delayimp.lib 相匹配。 如果存在不匹配，则会报告一个链接器错误`___delayLoadHelper2@8`或`___delayLoadHelper@8`作为无法解析的外部符号。 前者意味着新的链接器使用旧的 delayimp.lib，而后者意味着与新 delayimp.lib 旧链接器。

如果遇到无法解析链接器错误，运行[dumpbin /linkermember](../../build/reference/linkermember.md)： 您希望其中包含帮助器函数，以确定哪个帮助程序函数而定义 delayimp.lib 上的 1。 也可以在对象文件; 中定义的帮助器函数运行[dumpbin /symbols](../../build/reference/symbols.md)并查找`delayLoadHelper(2)`。

如果您有 Visual c + + 6.0 链接器，然后：

- 延迟加载 helper.lib 或.obj 文件，以确定它是否定义运行 dumpbin **__delayLoadHelper2**。 如果没有，链接将失败。

- 定义 **__delayLoadHelper**延迟加载 helper 的.lib 或.obj 文件。

## <a name="user-defined-helper-function"></a>用户定义的帮助器函数

如果您定义自己的帮助器函数，并且正在使用 Visual c + + 的当前版本，执行以下操作：

- 重命名的帮助器函数 **__delayLoadHelper2**。

- 由于延迟描述符 (ImgDelayDescr 中 delayimp.h) 中的指针已从绝对地址 (VAs) 更改为相对地址 (Rva)，以这两个 32 位和 64 位程序中按预期工作，您需要将它们转换回为指针。 引入了新的函数： PFromRva，delayhlp.cpp 中找到。 可以在每个描述符中的字段上使用此函数以将其转换回任一 32 位或 64 位指针。 默认延迟加载 helper 函数仍然是合适的模板使用作为示例。

## <a name="load-all-imports-for-a-delay-loaded-dll"></a>延迟加载的 DLL 加载所有导入

链接器可以从指定为要延迟加载的 DLL 加载所有导入。 请参阅[加载的延迟加载的 DLL 的所有导入](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)有关详细信息。

## <a name="see-also"></a>请参阅

[了解 Helper 函数](understanding-the-helper-function.md)