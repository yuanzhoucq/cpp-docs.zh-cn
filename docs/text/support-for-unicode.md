---
title: "支持 Unicode | Microsoft Docs"
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
  - "字符集 [C++], Unicode"
  - "全球化 [C++], 字符集"
  - "本地化 [C++], 字符集"
  - "可迁移数据类型 [MFC]"
  - "Unicode [C++]"
  - "Unicode [C++], 安装支持"
  - "宽字符 [C++], 关于宽字符"
ms.assetid: 180f1d10-8543-4f79-85ce-293d3cb443bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 支持 Unicode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Unicode 是支持所有字符集（包括无法仅以单个字节表示的字符集）的规范。  如果你要为国际市场编程，我们建议你使用 Unicode 或[多字节字符集](../text/support-for-multibyte-character-sets-mbcss.md) \(MBCS\)，或者使程序能够通过更改开关来生成支持两种字符集之一的程序。  
  
 宽字符是双字节多语言字符代码。  在当今的全球计算业内使用的大多数字符（包括技术符号和特殊的发布字符）都可以根据 Unicode 规范表示为宽字符。  无法仅以一个宽字符表示的字符可以通过使用 Unicode 代理项功能以 Unicode 对表示。  由于每个宽字符总是以固定的 16 位大小表示，因此使用宽字符可以简化使用国际字符集进行的编程。  
  
 宽字符字符串表示为一个 **wchar\_t\[\]** 数组并由 `wchar_t*` 指针指向它。  通过使用字母 L 作为该字符的前缀，可将任何 ASCII 字符表示为宽字符。  例如，L'\\0' 是（16 位）**NULL** 终止宽字符。  同样，通过使用字母 L 作为 ASCII 文本的前缀 \(L"Hello"\)，可将任何 ASCII 字符串文本表示为宽字符字符串。  
  
 通常，宽字符在内存中占用的空间比多字节字符多，但处理速度更快。  另外，在多字节编码中一次只能表示一个区域设置，而世界上的所有字符集可以同时以 Unicode 表示形式表示。  
  
 MFC 框架完全支持 Unicode，MFC 通过使用可移植的宏来实现对 Unicode 的支持，如下表所示。  
  
### MFC 中的可移植数据类型  
  
|不可移植的数据类型|替换为此宏|  
|---------------|-----------|  
|`char`|\_**TCHAR**|  
|**char\***，**LPSTR（Win32 数据类型）**|`LPTSTR`|  
|**char\*，LPSTR（Win32 数据类型）**|`LPCTSTR`|  
  
 `CString` 类使用 **\_TCHAR** 作为其基类，并提供构造函数和运算符以方便转换。  通过使用与用于处理 Windows ANSI 字符集相同的逻辑，可编写 Unicode 的大多数字符串操作，但基本操作单位是 16 位字符，而非 8 位字节。  与使用多字节字符集不同，不必（也不应）将 Unicode 字符视为两个不同的字节。  
  
## 你希望做什么？  
  
-   [通过 MFC 安装 Unicode 支持](../mfc/unicode-in-mfc.md)  
  
-   [在我的程序中启用 Unicode](../text/international-enabling.md)  
  
-   [在我的程序中同时启用 Unicode 和 MBCS](../text/internationalization-strategies.md)  
  
-   [使用 Unicode 创建国际化程序](../text/unicode-programming-summary.md)  
  
-   [了解 Unicode 的好处，包括如何利用 Unicode 才可使我的程序在 Windows 2000 上更有效](../text/benefits-of-character-set-portability.md)  
  
-   [使用 wmain 以便我可以将宽字符参数传递给我的程序](../text/support-for-using-wmain.md)  
  
-   [请参阅 Unicode 编程摘要](../text/unicode-programming-summary.md)  
  
-   [了解字节宽度可移植性的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)  
  
## 请参阅  
 [文本和字符串](../text/text-and-strings-in-visual-cpp.md)   
 [支持使用 wmain](../text/support-for-using-wmain.md)