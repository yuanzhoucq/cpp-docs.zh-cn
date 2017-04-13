---
title: "编译器警告 C4956 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4956
dev_langs:
- C++
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
caps.latest.revision: 9
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
ms.openlocfilehash: 782735be55c043482679740afa9571ba7b29dfc4
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-c4956"></a>编译器警告 C4956
“type”：此类型不可验证  
  
 生成此警告时[/clr: safe](../../build/reference/clr-common-language-runtime-compilation.md)指定而你的代码包含不可验证的类型。  
  
 有关详细信息，请参阅[纯代码和可验证代码 (C + + /cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
 此警告作为错误发出，并且可以禁用，[警告](../../preprocessor/warning.md)杂注或[/wd](../../build/reference/compiler-option-warning-level.md)编译器选项。  
  
 下面的示例生成 C4956：  
  
```  
// C4956.cpp  
// compile with: /clr:safe  
int* p;   // C4956  
```
