---
title: "声明摘要 | Microsoft Docs"
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
  - "C"
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 声明摘要
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`declaration`:  
 *declaration\-specifiers attribute\-seq*  opt *init\-declarator\-list* opt**;**  
  
 \/\* *attribute\-seq* 是 Microsoft 专用的 \*\/  
  
 *declaration\-specifiers*:  
 *storage\-class\-specifier declaration\-specifiers* opt  
  
 *type\-specifier declaration\-specifiers* opt  
  
 *type\-qualifier declaration\-specifiers* opt  
  
 *attribute\-seq* :            \/\* *attribute\-seq* 是 Microsoft 专用的 \*\/  
 *attribute attribute\-seq* opt  
  
 *attribute* : 以下项之一      \/\* Microsoft 专用 \*\/  
 ||||  
|-|-|-|  
|[\_\_asm](../assembler/inline/asm.md)|[\_\_clrcall](../cpp/clrcall.md)|[\_\_stdcall](../cpp/stdcall.md)|  
|[\_\_based](../cpp/based-grammar.md)|[\_\_fastcall](../cpp/fastcall.md)|[\_\_thiscall](../cpp/thiscall.md)|  
|[\_\_cdecl](../cpp/cdecl.md)|[\_\_inline](../misc/inline-inline-forceinline.md)|[\_\_vectorcall](../cpp/vectorcall.md)|  
  
 *init\-declarator\-list*:  
 *init\-declarator*  
  
 *init\-declarator\-list*  **,**  *init\-declarator*  
  
 *init\-declarator*:  
 *declarator*  
  
 *declarator*  **\=**  *initializer* \/\* 用于标量初始化 \*\/  
  
 *storage\-class\-specifier*:  
 **auto**  
  
 **register**  
  
 **static**  
  
 **extern**  
  
 **typedef**  
  
 **\_\_declspec \(**  *extended\-decl\-modifier\-seq*  **\)** \/\* Microsoft 专用 \*\/  
  
 *type\-specifier*:  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 `__int8` \/\* Microsoft 专用 \*\/  
  
 `__int16` \/\* Microsoft 专用 \*\/  
  
 `__int32` \/\* Microsoft 专用 \*\/  
  
 `__int64` \/\* Microsoft 专用 \*\/  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **signed**  
  
 **unsigned**  
  
 *struct\-or\-union\-specifier*  
  
 *enum\-specifier*  
  
 *typedef\-name*  
  
 *type\-qualifier*:  
 **const**  
  
 `volatile`  
  
 `declarator`:  
 `pointer` opt *direct\-declarator*  
  
 *direct\-declarator*:  
 *identifier*  
  
 **\(**  *declarator*  **\)**  
  
 *direct\-declarator*  **\[**  *constant\-expression*  opt **\]**  
  
 *direct\-declarator*  **\(**  *parameter\-type\-list*  **\)** \/\* 新样式声明符 \*\/  
  
 *direct\-declarator*  **\(**  *identifier\-list* opt **\)** \/\* 旧样式声明符 \*\/  
  
 `pointer`:  
 **\*** *type\-qualifier\-list* opt  
  
 **\*** *type\-qualifier\-list* opt `pointer`  
  
 *parameter\-type\-list*:                           \/\* 参数列表 \*\/  
 *parameter\-list*  
  
 *parameter\-list* **, ...**  
  
 *parameter\-list*:  
 *parameter\-declaration*  
  
 *parameter\-list*  **,**  *parameter\-declaration*  
  
 *type\-qualifier\-list*:  
 *type\-qualifier*  
  
 *type\-qualifier\-list type\-qualifier*  
  
 *enum\-specifier*:  
 **enum**  *identifier* opt **{** *enumerator\-list* **}**  
  
 **enum**  *identifier*  
  
 *enumerator\-list*:  
 *enumerator*  
  
 *enumerator\-list*  **,**  `enumerator`  
  
 `enumerator`:  
 *enumeration\-constant*  
  
 *enumeration\-constant*  **\=**  *constant\-expression*  
  
 *enumeration\-constant*:  
 *identifier*  
  
 *struct\-or\-union\-specifier*:  
 *struct\-or\-union identifier* opt **{** *struct\-declaration\-list* **}** *struct\-or\-union identifier*  
  
 *struct\-or\-union*:  
 **struct**  
  
 **union**  
  
 *struct\-declaration\-list*:  
 *struct\-declaration*  
  
 *struct\-declaration\-list struct\-declaration*  
  
 *struct\-declaration*:  
 *specifier\-qualifier\-list struct\-declarator\-list*  **;**  
  
 *specifier\-qualifier\-list*:  
 *type\-specifier specifier\-qualifier\-list* opt  
  
 *type\-qualifier specifier\-qualifier\-list* opt  
  
 *struct\-declarator\-list*:  
 *struct\-declarator struct\-declarator\-list*  **,**  *struct\-declarator*  
  
 *struct\-declarator*:  
 *declarator*  
  
 *type\-specifier declarator* opt **:** *constant\-expression*  
  
 *parameter\-declaration*:  
 *declaration\-specifiers declarator* \/\* 命名的声明符 \*\/  
  
 *declaration\-specifiers abstract\-declarator* opt **\/\*** 匿名声明符 **\*\/**  
  
 *identifier\-list*: **\/\*** 用于旧样式声明符 **\* \/**  
 *identifier*  
  
 *identifier\-list*  **,**  *identifier*  
  
 *abstract\-declarator*: **\/\*** 用于匿名声明符 **\*\/**  
 *指针*  
  
 `pointer` opt *direct\-abstract\-declarator*  
  
 *direct\-abstract\-declarator*:  
 **\(**  *abstract\-declarator*  **\)**  
  
 *direct\-abstract\-declarator* opt **\[** *constant\-expression* opt **\]**  
  
 *direct\-abstract\-declarator* opt **\(** *parameter\-type\-list* opt **\)**  
  
 *initializer*:  
 *assignment\-expression*  
  
 **{**  *initializer\-list*  **}** \/\* 用于聚合初始化 \*\/  
  
 **{**  *initializer\-list*  **, }**  
  
 *initializer\-list*:  
 *initializer*  
  
 *initializer\-list*  **,**  *initializer*  
  
 *type\-name*:  
 *specifier\-qualifier\-list abstract\-declarator* opt  
  
 *typedef\-name*:  
 *identifier*  
  
 *extended\-decl\-modifier\-seq*:\/\*    Microsoft 专用 \*\/  
 *extended\-decl\-modifier* opt  
  
 *extended\-decl\-modifier\-seq extended\-decl\-modifier*  
  
 *extended\-decl\-modifier*:   \/\* Microsoft 专用 \*\/  
 **thread**  
  
 **naked**  
  
 **dllimport**  
  
 `dllexport`  
  
## 请参阅  
 [调用约定](../cpp/calling-conventions.md)   
 [短语结构语法](../c-language/phrase-structure-grammar.md)   
 [已过时调用约定](../cpp/obsolete-calling-conventions.md)