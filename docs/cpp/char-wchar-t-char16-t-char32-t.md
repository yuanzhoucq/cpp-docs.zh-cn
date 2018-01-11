---
title: "char、 wchar_t、 char16_t、 char32_t |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
dev_langs: C++
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c01d4718bbc1781ea4705945bb90874384e09058
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="char-wchart-char16t-char32t"></a>char、wchar_t、char16_t、char32_t
类型 char、wchar_t、char16_t 和 char32_t 是内置类型，可表示字母数字字符，以及非字母数字的标志符号和非打印字符。 大小方面，char 是 8 位、wchar_t 和 char16_t 是 16 位，而 char32_t 是 32 位。  
  
## <a name="syntax"></a>语法  
  
```cpp  
char     ch1{ 'a' };    
wchar_t  ch2{ 'a' }; // or {L'a'}    
char16_t ch3{ L'a' };// or {L'a'}    
char32_t ch4{ L'a' };// or {L'a'}  
```  
  
## <a name="remarks"></a>备注  
 `char` 类型是 C 和 C++ 中的原始字符类型。 它可以用于存储 ASCII 字符集或所有 ISO-8859 字符集或 UTF-8 字符集中的字符。 类型`unsigned char`通常用于表示*字节*这不是 c + + 中的内置类型。 Char 类型不适用于很多语言的文本。 一般情况下，现代程序应使用一种宽字符类型来表示文本。 Unicode 是  
  
 在 C++ 标准库中，basic_string 类型专用于窄字符串和宽字符串。 当字符类型为 char 时，使用 std::string，字符类型为 wchar_t 时，则使用 std::wstring。 其他表示文本的类型，包括 std::stringstream 和 std::cout 均可专用于窄字符串和宽字符串。  
  
