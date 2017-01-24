---
title: "自 Visual C++ 6.0 以来 DLL 延迟加载 Helper 函数所做的更改 | Microsoft Docs"
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
  - "__delayLoadHelper2 函数"
  - "DLL 的延迟加载, 更改了什么"
  - "Helper 函数, 更改了什么"
  - "PFromRva 方法"
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 自 Visual C++ 6.0 以来 DLL 延迟加载 Helper 函数所做的更改
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果您的计算机上有多个 Visual C\+\+ 版本，或者您定义了自己的 Helper 函数，对 DLL 延迟加载 Helper 函数所做的更改对您可能会有所影响。  例如：  
  
-   **\_\_delayLoadHelper** 现在为 **\_\_delayLoadHelper2**  
  
-   **\_\_pfnDliNotifyHook** 现在为 **\_\_pfnDliNotifyHook2**  
  
-   **\_\_pfnDliFailureHook** 现在为 **\_\_pfnDliFailureHook2**  
  
-   **\_\_FUnloadDelayLoadedDLL** 现在为 **\_\_FUnloadDelayLoadedDLL2**  
  
> [!NOTE]
>  如果正在使用默认 Helper 函数，则不会受这些更改的影响。  调用链接器的方法没有更改。  
  
## 多个 Visual C\+\+ 版本  
 如果您的计算机上有多个 Visual C\+\+ 版本，请确保链接器与 delayimp.lib 匹配。  如果不匹配，您会收到一条链接器错误，向您报告 `___delayLoadHelper2@8` 或 `___delayLoadHelper@8` 是无法解析的外部符号。  前者意味着新链接器遇到旧 delayimp.lib，后者意味着旧链接器遇到新 delayimp.lib。  
  
 如果得到了一条未解析的链接器错误，请对您认为应包含该 Helper 函数的 delayimp.lib 运行 [dumpbin \/linkermember](../../build/reference/linkermember.md):1 以查看实际上定义的 Helper 函数。  Helper 函数也可在对象文件中定义；运行 [dumpbin \/symbols](../../build/reference/symbols.md) 并查找 `delayLoadHelper(2)`。  
  
 如果知道有 Visual C\+\+ 6.0 链接器，那么：  
  
-   对延迟加载帮助程序的 .lib 文件或 .obj 文件运行 dumpbin，确定它是否定义 **\_\_delayLoadHelper2**。  如果没有，链接将失败。  
  
-   在延迟加载 Helper 的 .lib 文件或 .obj 文件中定义 **\_\_delayLoadHelper**。  
  
## 用户定义的 Helper 函数  
 如果您定义了自己的 Helper 函数，并且正使用 Visual C\+\+ 的当前版本，请执行下列操作：  
  
-   将 Helper 函数重命名为 **\_\_delayLoadHelper2**。  
  
-   因为延迟描述符（delayimp.h 中的 ImgDelayDescr）中的指针已经从绝对地址 \(VA\) 更改为相对地址 \(RVA\)，以便按预期那样在 32 位和 64 位程序中都有效，所以需要将这些转换回指针。  已经介绍过在 delayhlp.cpp 中找到的一个新函数：PFromRva。  可以在描述符的每个字段上使用该函数以将它们转换回 32 位或 64 位指针。  默认延迟加载 Helper 函数仍是用作示例的好模板。  
  
## 加载延迟加载的 DLL 的所有导入  
 链接器可以加载指定为要延迟加载的 DLL 的所有导入。  有关更多信息，请参见[加载被延迟加载的 DLL 的所有导入](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)。  
  
## 请参阅  
 [Understanding the Helper Function](http://msdn.microsoft.com/zh-cn/6279c12c-d908-4967-b0b3-cabfc3e91d3d)