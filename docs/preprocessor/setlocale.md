---
title: "setlocale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "setlocale_CPP"
  - "vc-pragma.setlocale"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "杂注, setlocale"
  - "setlocale 杂注"
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# setlocale
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义要在转换宽字符常量和字符串时使用的区域设置（国家\/地区和语言）。  
  
## 语法  
  
```  
  
#pragma setlocale( "[locale-string]" )  
```  
  
## 备注  
 由于将多字节字符转换为宽字符的算法可能因区域设置而异，并且编译可能在不同于运行可执行文件的区域设置中进行，因此此杂注提供了在编译时指定目标区域设置的方法。  这将确保宽字符字符串以正确的格式存储。  
  
 默认 *locale\-string* 为 ""。  
  
 “C”区域设置会将字符串中的每个字符作为 `wchar_t` \(unsigned short\) 映射到“C”区域设置的值。  对 `setlocale` 有效的其他值是在[语言字符串](../c-runtime-library/language-strings.md)列表中找到的项。  例如，您可以发出：  
  
```  
#pragma setlocale("dutch")  
```  
  
 能否发出语言字符串取决于计算机上是否支持相应的代码页和语言 ID。  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)