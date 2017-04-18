---
title: "编译器警告 C4957 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4957
dev_langs:
- C++
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 8eb7283942a8a89fc3322983c41c68082b6c5cee
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-c4957"></a>编译器警告 C4957
“cast”：从“cast_from”到“cast_to”的显式强制转换是不可验证的  
  
 强制转换会导致不可验证的映像。  
  
 某些转换是安全的（例如，触发用户定义的转换的 `static_cast` 和一个 `const_cast`）。 A [safe_cast](../../windows/safe-cast-cpp-component-extensions.md)可保证生成可验证代码。  
  
 有关详细信息，请参阅[纯代码和可验证代码 (C + + /cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
 此警告作为错误发出，并且可以禁用，[警告](../../preprocessor/warning.md)杂注或[/wd](../../build/reference/compiler-option-warning-level.md)编译器选项。  
  
 以下示例生成 C4957：  
  
```  
// C4957.cpp  
// compile with: /clr:safe  
// #pragma warning( disable : 4957 )  
using namespace System;  
int main() {  
   Object ^ o = "Hello, World!";  
   String ^ s = static_cast<String^>(o);   // C4957  
   String ^ s2 = safe_cast<String^>(o);   // OK  
}  
```
