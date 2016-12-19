---
title: "代码页 | Microsoft Docs"
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
  - "c.international"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "ANSI [C++], 代码页"
  - "字符集 [C++], 代码页"
  - "代码页 [C++], 类型"
  - "区域设置代码页 [C++]"
  - "本地化 [C++], 代码页"
  - "多字节代码页 [C++]"
  - "系统默认的代码页"
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 代码页
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`code page` 是一个字符集，可以包括数字、标点符号和其他标志符号。  不同的语言和区域设置可能使用不同的代码页。  例如，ANSI 代码页 1252 用于英语和大多数欧洲语言，而 OEM 代码页 932 则用于日本汉字。  
  
 代码页可以在从字符映射到单字节值或多字节值的表格中表现。  大多数代码页共享范围为0x00 \- 0x7F字符的 ASCII 字符集。  
  
 Microsoft 运行时库使用以下类型的代码页：  
  
-   系统默认的ANSI代码页。  默认情况下，一开始，运行时系统自动设置多字节代码页为从操作系统获得的系统默认的 ANSI 代码页。  调用：  
  
    ```  
    setlocale ( LC_ALL, "" );  
    ```  
  
     也可以设置区域设置为系统默认 ANSI 代码页。  
  
-   区域设置代码页。  大量运行时程序行为取决于当前区域设置，包括区域设置代码页。\(有关更多信息，请参见 [区域设置相关例程](../c-runtime-library/locale.md)。\)默认情况下，在 Microsoft 运行时库中的所有与区域设置相关例程使用对应“C”区域设置的代码页。  在运行时可以调用 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)来更改或查询使用中的区域设置代码页。  
  
-   多字节代码页。  运行时库中的大多数多字节字符例程的行为依赖于当前的多字节代码页的设置。  默认情况下，这些例程使用系统默认 ANSI 代码页。  在运行时可以利用[\_getmbcp](../c-runtime-library/reference/getmbcp.md) 和 [\_setmbcp](../c-runtime-library/reference/setmbcp.md)查询和更改多字节代码页。  
  
-   ANSI定义的“C”区域设置与传统执行的 C 程序的区域设置对应。  “C”区域设置 \(“C”代码页\) 代码页对应于 ASCII 字符集。  例如，在“C”区域设置中，当值为 0x61 \- 0x7A时`islower` 返回 true 。  在另一个区域设置中，正如该区域设置定义，当为其他值时，`islower` 可能返回 true。  
  
## 请参阅  
 [国际化](../c-runtime-library/internationalization.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)