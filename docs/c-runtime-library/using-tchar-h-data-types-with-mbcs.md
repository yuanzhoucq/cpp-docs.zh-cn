---
title: "将 TCHAR.H 数据类型用于 _MBCS | Microsoft Docs"
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
  - "_mbcs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_MBCS 数据类型"
  - "MBCS 数据类型"
  - "TCHAR.H 数据类型"
ms.assetid: 48f471e7-9d2b-4a39-b841-16a0e15c0a18
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 将 TCHAR.H 数据类型用于 _MBCS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 正如在一般文本例程映射表指示 \(参见 [一般文本映射](../c-runtime-library/generic-text-mappings.md)\)，当清单常数 `_MBCS` 被定义时，给定的一般文本例程映射到下列例程之一：  
  
-   正确处理多字节字节、字符和字符串的 SBCS 例程。  在这种情况下，字符串参数应为 `char*` 类型。  例如，`_tprintf` 映射到 `printf`；`printf` 的字符串参数应是 `char*` 类型。  如果使用 `_TCHAR`一般文本数据类型作为字符串类型，由于  `_TCHAR*`映射到`char*`，所以 `printf` 的形参和实参类型匹配。  
  
-   MBCS 特定的例程。  在这种情况下，字符串参数应为 `unsigned char*` 类型。  例如，`_tcsrev`  映射到 `_mbsrev`，后者希望且返回 `unsigned char*`类型的字符串。  如果使用 `_TCHAR` 一般文本数据类型作为字符串类型，因为 `_TCHAR` 映射到`char` 类型，所以可能存在潜在的类型冲突。  
  
 下面是防止此类型冲突（及其所导致的 C 编译器警告或 C\+\+ 编译器错误）的三个解决方案。  
  
-   使用默认行为。  TCHAR.H 为运行库中的例程提供一般文本例程原型，如下面的示例所示。  
  
    ```  
    char *_tcsrev(char *);  
    ```  
  
     默认情况下，`_tcsrev` 的原型通过LIBC.LIB中的形式转换映射到 `_mbsrev`。  这将`_mbsrev`传入参数的类型和输出的返回值类型从 `_TCHAR *`（即 `char *`）更改为`unsigned char **`）。  当使用 `_TCHAR` 时，此方法确保类型匹配，但由于函数调用系统开销，因此速度相对较慢。  
  
-   通过在代码中包含下列预处理器语句来使用函数内联。  
  
    ```  
    #define _USE_INLINING  
    ```  
  
     此方法造成TCHAR.H 中的内联函数形式转换，直接将一般文本例程映射到适当的 MBCS 例程。  从 TCHAR.H 中摘录的下列代码提供了如何实现此方法的示例。  
  
    ```  
    __inline char *_tcsrev(char *_s1)  
    {return (char *)_mbsrev((unsigned char *)_s1);}  
    ```  
  
     如果可以使用内联，这将是最好的解决方案，因为它保证类型匹配并且不另外消耗时间。  
  
-   通过在代码中合并以下预处理器报表来实现“直接映射”。  
  
    ```  
    #define _MB_MAP_DIRECT  
    ```  
  
     如果不希望使用默认行为或无法使用内联，则此方法提供另一种快速解决方案。  它使一般文本例程由宏直接映射到例程的 MBCS 版本，如TCHAR.H中的以下示例所示。  
  
    ```  
    #define _tcschr _mbschr  
    ```  
  
 采用此方法时，必须注意确保字符串参数和字符串返回值使用适当数据类型。  可以使用类型强制转换以确保正确的类型匹配，或者可以使用 `_TXCHAR` 一般文本数据类型。  在SBCS 代码中,`_TXCHAR` 映射到`char` 类型，而在 MBCS 代码中映射到 `unsigned char`  类型。  有关一般文本宏的更多信息，请参见 [一般文本映射](../c-runtime-library/generic-text-mappings.md)。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [国际化](../c-runtime-library/internationalization.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)