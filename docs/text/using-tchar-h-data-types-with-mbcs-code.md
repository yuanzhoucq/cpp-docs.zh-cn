---
title: "将 TCHAR.H 数据类型用于 _MBCS 代码 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ""tchar.h""
  - "TCHAR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "一般文本数据类型 [C++]"
  - "一般文本映射 [C++]"
  - "映射一般文本"
  - "映射 [C++], TCHAR.H"
  - "MBCS [C++], 一般文本映射"
  - "TCHAR.H 数据类型, 映射"
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
caps.latest.revision: 7
caps.handback.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 将 TCHAR.H 数据类型用于 _MBCS 代码
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果定义了 **\_MBCS** 清单常数，则给定的一般文本例程映射到下列例程之一：  
  
-   正确处理多字节字节、字符和字符串的 SBCS 例程。  在这种情况下，字符串参数应为 **char\*** 类型。  例如，`_tprintf` 映射到 `printf`；`printf` 的字符串参数应是 **char\*** 类型。  如果使用 **\_TCHAR** 一般文本数据类型作为字符串类型，由于 **\_TCHAR**\* 映射到 **char\***，所以 `printf` 的形参和实参类型匹配。  
  
-   MBCS 特定的例程。  在这种情况下，字符串参数应为 `unsigned` **char\*** 类型。  例如，`_tcsrev` 映射到 `_mbsrev`，后者需要且返回 `unsigned` **char\*** 类型的字符串。  如果使用 **\_TCHAR** 一般文本数据类型作为字符串类型，由于 **\_TCHAR** 映射到 `char` 类型，所以可能存在类型冲突。  
  
 下面是防止此类型冲突（及其所导致的 C 编译器警告或 C\+\+ 编译器错误）的三个解决方案。  
  
-   使用默认行为。  Tchar.h 为运行库中的例程提供一般文本例程原型，如下面的示例所示。  
  
    ```  
    char * _tcsrev(char *);  
    ```  
  
     默认情况下，`_tcsrev` 的原型通过 Libc.lib 中的形式转换 \(thunk\) 映射到 `_mbsrev`。  这将把 `_mbsrev` 传入参数的类型和输出的返回值类型从 **\_TCHAR \***（即 `char` **\***）更改为 `unsigned` `char` **\***。  使用 **\_TCHAR** 时此方法确保类型匹配，但由于函数调用系统开销，因此速度相对较慢。  
  
-   通过在代码中包含下列预处理器语句来使用函数内联。  
  
    ```  
    #define _USE_INLINING  
    ```  
  
     此方法使 Tchar.h 中提供的内联函数 thunk 将一般文本例程直接映射到适当的 MBCS 例程。  从 Tchar.h 中摘录的下列代码提供了如何实现此方法的示例。  
  
    ```  
    __inline char *_tcsrev(char *_s1)  
    {return (char *)_mbsrev((unsigned char *)_s1);}  
    ```  
  
     如果可以使用内联，这将是最好的解决方案，因为它保证类型匹配并且不另外消耗时间。  
  
-   通过在代码中包含以下预处理器语句来实现直接映射。  
  
    ```  
    #define _MB_MAP_DIRECT  
    ```  
  
     如果不希望使用默认行为或无法使用内联，则此方法提供另一种快速解决方案。  它使一般文本例程由宏直接映射到例程的 MBCS 版本，如 Tchar.h 中的以下示例所示。  
  
    ```  
    #define _tcschr _mbschr  
    ```  
  
     采用此方法时，必须注意确保使用适当数据类型的字符串参数和字符串返回值。  可以使用类型强制转换以确保正确的类型匹配，或者可以使用 **\_TXCHAR** 一般文本数据类型。  **\_TXCHAR** 在 SBCS 代码中映射到 `char` 类型，而在 MBCS 代码中映射到 `unsigned` `char` 类型。  有关一般文本宏的更多信息，请参见“运行库参考”中的[一般文本映射](../c-runtime-library/generic-text-mappings.md)。  
  
## 请参阅  
 [Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)