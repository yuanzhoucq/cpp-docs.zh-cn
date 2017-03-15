---
title: "char、wchar_t、char16_t、char32_t | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "char_cpp"
  - "char16_t_cpp"
  - "whchar_t_cpp"
  - "char32_t_cpp"
dev_langs: 
  - "C++"
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# char、wchar_t、char16_t、char32_t
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

类型 char、wchar\_t、char16\_t 和 char32\_t 是内置类型，可表示字母数字字符，以及非字母数字的标志符号和非打印字符。  大小方面，char 是 8 位、wchar\_t 和 char16\_t 是 16 位，而 char32\_t 是 32 位。  
  
## 语法  
  
```vb  
char     ch1{ 'a' };  
wchar_t  ch2{ 'a' }; // or {L'a'}  
char16_t ch3{ L'a' };// or {L'a'}  
char32_t ch4{ L'a' };// or {L'a'}  
```  
  
## 备注  
 `char` 类型是 C 和 C\+\+ 中的原始字符类型。  它可以用于存储 ASCII 字符集或所有 ISO\-8859 字符集或 UTF\-8 字符集中的字符。  类型 `unsigned char` 通常用于表示不是 C\+\+ 中的内置类型的*字节*。  Char 类型不适用于很多语言的文本。  一般情况下，现代程序应使用一种宽字符类型来表示文本。  Unicode 是  
  
 在 C\+\+ 标准库中，basic\_string 类型专用于窄字符串和宽字符串。  当字符类型为 char 时，使用 std::string，字符类型为 wchar\_t 时，则使用 std::wstring。  其他表示文本的类型，包括 std::stringstream 和 std::cout 均可专用于窄字符串和宽字符串。  
  
## 要求