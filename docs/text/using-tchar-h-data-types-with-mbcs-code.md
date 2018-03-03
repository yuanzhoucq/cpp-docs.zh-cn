---
title: "使用 TCHAR。H 数据类型与 _MBCS 代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tchar.h
- TCHAR
dev_langs:
- C++
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28255b2e47c48b89b0bd6aea044fe0c15c1f2a08
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-tcharh-data-types-with-mbcs-code"></a>将 TCHAR.H 数据类型用于 _MBCS 代码
当清单常量**_MBCS**是定义，给定的一般文本例程映射到例程的以下类型之一：  
  
-   可恰当处理多字节字节、字符和字符串的 SBCS 例程。 在这种情况下，字符串参数应为类型**char\***。 例如，`_tprintf`映射到`printf`; 的字符串自变量`printf`属于类型**char\***。 如果你使用**_TCHAR**一般文本数据类型为你的字符串类型的形参和实参类型`printf`与匹配，因为**_TCHAR** \*映射到**char\***.  
  
-   MBCS 专用例程。 在这种情况下，字符串参数应为类型`unsigned` **char\***。 例如，`_tcsrev`映射到`_mbsrev`，其需要并返回类型的字符串`unsigned` **char\***。 如果你使用**_TCHAR**一般文本数据类型为字符串类型，存在是潜在的类型冲突，因为**_TCHAR**图来键入`char`。  
  
 以下是防止此类型冲突（以及可能导致的 C 编译器警告或 C++ 编译器错误）的三个解决方案：  
  
-   使用默认行为。 Tchar.h 中的运行时库，如以下示例所示的例程提供一般文本例程的原型。  
  
    ```  
    char * _tcsrev(char *);  
    ```  
  
     默认情况下，该原型以供`_tcsrev`映射到`_mbsrev`通过在 Libc.lib 转换 （thunk）。 这将更改的类型`_mbsrev`传入的参数和出站返回值从**_TCHAR \***  (即， `char`  **\*** ) 到`unsigned``char` **\***. 此方法可确保当你使用匹配类型**_TCHAR**，但由于函数调用开销相对较慢。  
  
-   通过在代码中包含以下预处理器语句来使用函数内联。  
  
    ```  
    #define _USE_INLINING  
    ```  
  
     此方法会导致内联函数转换 （thunk），在 Tchar.h 中的一般文本例程直接映射到相应的 MBCS 例程中提供。 下面的代码摘录从 Tchar.h 举例说明如何完成此操作。  
  
    ```  
    __inline char *_tcsrev(char *_s1)  
    {return (char *)_mbsrev((unsigned char *)_s1);}  
    ```  
  
     如果可以使用内联，这是最好的解决方案，因为它保证了类型匹配，并且不会产生额外的时间成本。  
  
-   通过将合并你的代码中的以下预处理器语句使用直接映射。  
  
    ```  
    #define _MB_MAP_DIRECT  
    ```  
  
     如果不想使用默认行为或无法使用内联，则此方法提供了一种快速替代方法。 它会导致的一般文本例程映射由宏直接到 MBCS 版本的例程，如 Tchar.h 中的以下示例所示。  
  
    ```  
    #define _tcschr _mbschr  
    ```  
  
     采用此方法时，您必须小心以确保使用适当的数据类型的字符串自变量和字符串返回值。 你可以使用类型强制转换来确保正确的类型匹配，或者可以使用**_TXCHAR**一般文本数据类型。 **_TXCHAR**图来键入`char`在 SBCS 代码，但图来键入`unsigned` `char` MBCS 代码中。 有关一般文本宏的详细信息，请参阅[一般文本映射](../c-runtime-library/generic-text-mappings.md)中*运行时库参考*。  
  
## <a name="see-also"></a>请参阅  
 [Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)