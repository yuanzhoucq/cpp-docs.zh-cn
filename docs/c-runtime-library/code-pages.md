---
title: "代码页 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.international
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: dc4480e79931f1ad3c1dc81b9687e82fcb2697a7
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="code-pages"></a>代码页
代码页是一个字符集，可以包括数字、标点符号和其他标志符号。`code page` 不同的语言和区域设置可能使用不同的代码页。 例如，ANSI 代码页 1252 适用于英语和大多数欧洲语言；而 OEM 代码页 932 则适用于日本汉字。  
  
 代码页可以用字符与单字节值或多字节值的映射表来表示。 对于 0x00 - 0x7F 范围的字符，大多数代码页共享 ASCII 字符集。  
  
 Microsoft 运行库使用以下类型的代码页：  
  
-   系统默认的 ANSI 代码页。 默认情况下，启动时运行系统将多字节代码页自动设置为系统默认的 ANSI 代码页（可从操作系统中获得）。 调用：  
  
    ```  
    setlocale ( LC_ALL, "" );  
    ```  
  
     也可将区域设置设置为系统默认 ANSI 代码页。  
  
-   区域设置代码页。 大量运行时例程的行为取决于当前的区域设置（包括区域设置代码页）。 （有关详细信息，请参阅[与区域设置相关的例程](../c-runtime-library/locale.md)。）默认情况下，Microsoft 运行库中的所有与区域设置相关的例程使用对应于“C”区域设置的代码页。 运行时可使用对 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 的调用来更改或查询所使用的区域设置代码页。  
  
-   多字节代码页。 运行库中的大部分多字节字符例程的行为取决于当前的多字节代码页设置。 默认情况下，这些例程使用系统默认的 ANSI 代码页。 运行时可分别使用 [_getmbcp](../c-runtime-library/reference/getmbcp.md) 和 [_setmbcp](../c-runtime-library/reference/setmbcp.md) 查询和更改多字节代码页。  
  
-   ANSI 定义“C”区域设置以与传统上用来执行 C 程序的区域设置相对应。 “C”区域设置的代码页（“C”代码页）对应于 ASCII 字符集。 例如，在“C”区域设置中，只有对于 0x61 - 0x7A 范围的值，`islower` 才会返回 true。 在另一个区域设置中，`islower` 可能会为这些值或其他值（由该区域设置定义）返回 true。  
  
## <a name="see-also"></a>另请参阅  
 [国际化](../c-runtime-library/internationalization.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)
