---
title: "Visual C++ 中的文本和字符串 | Microsoft Docs"
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
  - "ASCII 字符 [C++]"
  - "字符集 [C++]"
  - "字符集 [C++], 关于字符集"
  - "字符集 [C++], 非欧洲的"
  - "全球化 [C++]"
  - "全球化 [C++], 字符集"
  - "国际应用程序 [C++], 关于国际化应用程序"
  - "日语字符 [C++]"
  - "日文汉字字符支持 [C++]"
  - "本地字符集 [C++]"
  - "本地化 [C++]"
  - "本地化 [C++], 字符集"
  - "MBCS [C++], 国际化编程"
  - "多语言支持 [C++]"
  - "非欧洲字符 [C++]"
  - "可迁移性 [C++]"
  - "可迁移性 [C++], 字符集"
  - "编程 [C++], 国际化"
  - "翻译代码 [C++]"
  - "翻译 [C++], 字符集"
  - "Unicode [C++]"
ms.assetid: a1bb27ac-abe5-4c6b-867d-f761d4b93205
caps.latest.revision: 12
caps.handback.revision: 12
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Visual C++ 中的文本和字符串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为国际市场开发应用程序的一个重要方面就是要适当地表示本地字符集。  ASCII 字符集在 0x00 到 0x7F 的范围内定义字符。  还有其他一些字符集（主要是欧洲字符），它们在 0x00 到 0x7F 的范围内定义与 ASCII 字符集相同的字符，还在 0x80 到 0xFF 的范围内定义了扩展字符集。  因此，8 位的单字节字符集 \(SBCS\) 足以表示 ASCII 字符集以及许多欧洲语言的字符集。  但是，一些非欧洲字符集（如日文汉字）包含许多单字节代码方案无法表示的字符，因此要求使用多字节字符集 \(MBCS\) 编码。  
  
## 本节内容  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)  
 讨论 Visual C\+\+ 对 Unicode 和 MBCS 编程的支持。  
  
 [支持 Unicode](../text/support-for-unicode.md)  
 描述 Unicode，它是支持所有字符集（包括无法以单个字节表示的字符集）的规范。  
  
 [对多字节字符集 \(MBCS\) 的支持](../text/support-for-multibyte-character-sets-mbcss.md)  
 讨论 MBCS，它可以替换 Unicode 以用于支持无法以单个字节表示的字符集（如日语和中文）。  
  
 [Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)  
 为许多数据类型、例程和其他对象提供特定于 Microsoft 的一般文本映射。  
  
 [如何：在各种字符串类型之间进行转换](../text/how-to-convert-between-various-string-types.md)  
 演示如何将各种 Visual C\+\+ 字符串类型转换为其他字符串。  
  
## 相关章节  
 [国际化](../c-runtime-library/internationalization.md)  
 讨论 C 运行库中的国际支持。  
  
 [国际示例](http://msdn.microsoft.com/zh-cn/aa8d390c-cf4c-4dd8-9dea-74d81f93f2f8)  
 提供指向演示 Visual C\+\+ 中的国际化的示例的链接。  
  
 [语言和国家\/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)  
 提供 C 运行库中的语言和国家\/地区字符串。