---
title: "编译器警告 C4957 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4957"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4957"
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# 编译器警告 C4957
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“cast”：从“cast\_from”到“cast\_to”的显式强制转换是不可验证的  
  
 强制转换会导致不可验证的映像。  
  
 某些转换是安全的（例如，触发用户定义的转换的 `static_cast` 和一个 `const_cast`）。 确保 [safe\_cast](../../windows/safe-cast-cpp-component-extensions.md) 生成可验证的代码。  
  
 有关详细信息，请参阅[纯代码和可验证代码](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
 此警告作为错误发出，可通过 [warning](../../preprocessor/warning.md) 杂注或 [\/wd](../../build/reference/compiler-option-warning-level.md) 编译器选项禁用该警告。  
  
 以下示例生成 C4957：  
  
```  
// C4957.cpp // compile with: /clr:safe // #pragma warning( disable : 4957 ) using namespace System; int main() { Object ^ o = "Hello, World!"; String ^ s = static_cast<String^>(o);   // C4957 String ^ s2 = safe_cast<String^>(o);   // OK }  
```