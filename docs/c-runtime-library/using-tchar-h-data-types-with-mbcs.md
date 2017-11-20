---
title: "将 TCHAR.H 数据类型用于 _MBCS | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mbcs
dev_langs: C++
helpviewer_keywords:
- TCHAR.H data types
- MBCS data type
- _MBCS data type
ms.assetid: 48f471e7-9d2b-4a39-b841-16a0e15c0a18
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3c015c8ff7481f0d5ba25eba023b21f4877deaa4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="using-tcharh-data-types-with-mbcs"></a>将 TCHAR.H 数据类型用于 _MBCS
**Microsoft 专用**  
  
 如一般文本例程映射表所示（参阅[一般文本映射](../c-runtime-library/generic-text-mappings.md)），定义清单常量 `_MBCS` 后，给定的一般文本例程会映射到以下其中一种例程中：  
  
-   可恰当处理多字节字节、字符和字符串的 SBCS 例程。 在这种情况下，字符串参数类型应为 `char*`。 例如，`_tprintf` 映射到 `printf`；`printf` 的字符串参数类型为 `char*`。 如果将 `_TCHAR` 一般文本数据类型用于字符串类型，`printf` 的形参和实参类型将匹配，因为 `_TCHAR*` 映射到 `char*`。  
  
-   MBCS 专用例程。 在这种情况下，字符串参数类型应为 `unsigned char*`。 例如，`_tcsrev` 映射到 `_mbsrev`，这应该并且会返回的类型为 `unsigned char*` 的字符串。 同样，如果将 `_TCHAR` 一般文本数据类型用于字符串类型，则会出现潜在的类型冲突，因为 `_TCHAR` 映射到类型 `char`。  
  
 以下是防止此类型冲突（以及可能导致的 C 编译器警告或 C++ 编译器错误）的三个解决方案：  
  
-   使用默认行为。 TCHAR.H 为运行时库中的例程提供一般文本例程原型，如下例所示。  
  
    ```  
    char *_tcsrev(char *);  
    ```  
  
     默认情况下，`_tcsrev` 的原型通过 LIBC.LIB 中的 thunk 映射到 `_mbsrev`。 这将 `_mbsrev` 传入参数和传出返回值的类型从 `_TCHAR *`（例如 `char *`）更改为 `unsigned char *`。 这种方法可以确保在使用 `_TCHAR` 时进行类型匹配，但该过程由于函数调用产生系统开销而相对较慢。  
  
-   通过在代码中包含以下预处理器语句来使用函数内联。  
  
    ```  
    #define _USE_INLINING  
    ```  
  
     此方法会导致 TCHAR.H 中提供的内联函数 thunk 将一般文本例程直接映射到相应的 MBCS 例程。 摘自 TCHAR.H 的以下代码提供了一个如何完成此操作的示例。  
  
    ```  
    __inline char *_tcsrev(char *_s1)  
    {return (char *)_mbsrev((unsigned char *)_s1);}  
    ```  
  
     如果可以使用内联，这是最好的解决方案，因为它保证了类型匹配，并且不会产生额外的时间成本。  
  
-   通过在代码中包含以下预处理器语句来使用“直接映射”。  
  
    ```  
    #define _MB_MAP_DIRECT  
    ```  
  
     如果不想使用默认行为或无法使用内联，则此方法提供了一种快速替代方法。 它使一般文本例程由宏直接映射到例程的 MBCS 版本，如以下 TCHAR.H 中的示例所示。  
  
    ```  
    #define _tcschr _mbschr  
    ```  
  
 在采用此方法时，必须小心以确保将适当的数据类型用于字符串参数和字符串返回值。 可以使用类型强制转换来确保类型匹配正确，也可以使用 `_TXCHAR` 一般文本数据类型。 `_TXCHAR` 映射到 SBCS 代码中的类型 `char`，但映射到 MBCS 代码中的类型 `unsigned char`。 有关一般文本宏的详细信息，请参阅[一般文本映射](../c-runtime-library/generic-text-mappings.md)。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [国际化](../c-runtime-library/internationalization.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)