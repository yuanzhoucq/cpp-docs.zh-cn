---
title: "区域设置和代码页 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字符集 [C++], 代码页"
  - "字符集 [C++], 区域设置"
  - "代码页 [C++]"
  - "代码页 [C++], 动态地更改"
  - "代码页 [C++], 区域设置"
  - "约定 [C++], 国际字符支持"
  - "区域设置 ID [C++]"
  - "区域设置 [C++]"
  - "区域设置 [C++], 关于区域设置"
  - "本地化 [C++], 代码页"
  - "本地化 [C++], 区域设置"
  - "多字节代码页 [C++]"
ms.assetid: bd937361-b6d3-4c98-af95-beb7c903187b
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# 区域设置和代码页
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

区域设置 ID 反映特定地理区域的当地约定和语言。  可能有一个以上的国家\/地区说某种特定的语言，例如，巴西和葡萄牙都说葡萄牙语。  反之，一个国家\/地区可能有一种以上的官方语言。  例如，加拿大有两种官方语言：英语和法语。  因此，加拿大有两个不同的区域设置：加拿大英语和加拿大法语。  一些与区域设置相关的类别包括日期的格式设置和货币值的显示格式。  
  
 语言确定文本和数据的格式约定，而国家\/地区则确定本地约定。  每种语言都有一个由代码页表示的唯一映射，包括字母表中的字符以外的字符（如标点符号和数字）。  代码页是一个字符集并且与语言相关。  因此，[区域设置](../c-runtime-library/locale.md)就成为语言、国家\/地区和代码页的唯一组合。  可以通过调用 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 函数在运行时更改区域设置和代码页设置。  
  
 不同的语言可能使用不同的代码页。  例如，ANSI 代码页 1252 用于英语和大多数欧洲语言，而 ANSI 代码页 932 则用于日本汉字。  实际上，所有代码页都共享 ASCII 字符集中最低的 128 个字符（0x00 到 0x7F）。  
  
 任何单字节代码页都可使用一个包含 256 项的表来表示，在该表中表示为字节值到字符（包括数字和标点符号）或标志符号的映射。  任何多字节代码页也可以表示为一个非常大的表（有 64K 项），包含双字节值到字符的映射。  但实际上，对于前 256 个（单字节）字符，它通常用表表示；对于双字节值，则用范围表示。  
  
 有关代码页的更多信息，请参见 [代码页](../c-runtime-library/code-pages.md)。  
  
 C 运行库有两类内部代码页：区域设置和多字节。  在程序执行期间可以更改当前代码页（有关 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 和 [\_setmbcp](../c-runtime-library/reference/setmbcp.md) 函数的信息，请参见文档）。  而且，运行库可以获取并使用操作系统代码页的值。  在 Windows 2000 中，操作系统代码页是“系统默认 ANSI”代码页。  此代码页在程序的执行期间保持不变。  
  
 更改区域设置代码页后，与区域设置相关的函数集的行为更改为由选定的代码页指示的行为。  默认情况下，所有与区域设置相关的函数使用对于“C”区域设置唯一的区域设置代码页开始执行过程。  可以通过调用 `setlocale` 函数来更改内部区域设置代码页（以及其他区域设置特定的属性）。  对 `setlocale`\(LC\_ALL, ""\) 的调用将区域设置设置为由操作系统用户区域设置指示的那个区域设置。  
  
 同样，更改多字节代码页时，多字节函数的行为更改为由选定的代码页指示的行为。  默认情况下，所有多字节函数使用与操作系统默认代码页相对应的多字节代码页开始执行过程。  可以通过调用 `_setmbcp` 函数来更改内部多字节代码页。  
  
 C 运行时函数 `setlocale` 设置、更改或查询部分或全部当前程序的区域设置信息。  [\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 例程是 `setlocale` 的宽字符版本；`_wsetlocale` 的参数和返回值是宽字符字符串。  
  
## 请参阅  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [字符集可迁移性的好处](../text/benefits-of-character-set-portability.md)