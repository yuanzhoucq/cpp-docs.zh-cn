---
title: "DLL 中的更改延迟加载 Helper 函数自 Visual c + + 6.0 以来 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b3123a722e0e95119a4b04f5c060bd947b987cdf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>自 Visual C++ 6.0 以来 DLL 延迟加载 Helper 函数所做的更改
如果计算机上有多个版本的 Visual c + + 或如果您定义您自己的 helper 函数，你可能会受更改对该 DLL 延迟加载 helper 函数。 例如:  
  
-   **__delayLoadHelper**现**__delayLoadHelper2**  
  
-   **__pfnDliNotifyHook**现**__pfnDliNotifyHook2**  
  
-   **__pfnDliFailureHook**现**__pfnDliFailureHook2**  
  
-   **__FUnloadDelayLoadedDLL**现**__FUnloadDelayLoadedDLL2**  
  
> [!NOTE]
>  如果你正在使用默认 helper 函数，这些更改不会影响你。 不有关于如何调用链接器的任何更改。  
  
## <a name="multiple-versions-of-visual-c"></a>多个版本的 Visual c + +  
 如果您的计算机上有多个版本的 Visual c + +，请确保链接器匹配 delayimp.lib。 如果存在不匹配，将获得一个链接器错误报告`___delayLoadHelper2@8`或`___delayLoadHelper@8`为未解析的外部符号。 这意味着与旧的 delayimp.lib，新链接器，后者表示与新 delayimp.lib 旧链接器。  
  
 如果你遇到无法解析链接器错误，运行[dumpbin /linkermember](../../build/reference/linkermember.md)： 上你希望其中包含要查看改为定义的帮助器函数的帮助器函数 delayimp.lib 1。 Helper 函数也可以定义中的对象文件;运行[dumpbin /symbols](../../build/reference/symbols.md)并查找`delayLoadHelper(2)`。  
  
 如果你知道你有 Visual c + + 6.0 链接器，然后：  
  
-   在延迟加载 helper 的.lib 或.obj 文件，以确定是否它定义上运行 dumpbin **__delayLoadHelper2**。 如果没有，则链接将失败。  
  
-   定义**__delayLoadHelper**在延迟加载 helper 的.lib 或.obj 文件。  
  
## <a name="user-defined-helper-function"></a>用户定义的帮助器函数  
 如果您定义您自己的 helper 函数，并使用 Visual c + + 的当前版本，请执行以下操作：  
  
-   重命名的帮助器函数**__delayLoadHelper2**。  
  
-   由于延迟描述符 (ImgDelayDescr 中 delayimp.h) 中的指针已从绝对地址 (VAs) 更改为相对地址 (Rva)，在这两个 32 位和 64 位程序中按预期工作，你需要将它们转换回为指针。 引入了新的函数： PFromRva，delayhlp.cpp 中找到。 可以在每个描述符中的字段上使用此函数可将它们转换为任一 32 位或 64 位指针。 默认延迟加载 helper 函数仍然是一个很好的模板来使用作为示例。  
  
## <a name="load-all-imports-for-a-delay-loaded-dll"></a>加载被延迟加载的 DLL 的所有导入  
 链接器可以从你指定为要延迟加载的 DLL 加载所有导入。 请参阅[加载的延迟加载的 DLL 的所有导入](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)有关详细信息。  
  
## <a name="see-also"></a>请参阅  
 [了解 Helper 函数](understanding-the-helper-function.md)