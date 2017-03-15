---
title: "编译器错误 C2393 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2393
dev_langs:
- C++
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 078454c9824a734863796ab5810056147d17879c
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2393"></a>编译器错误 C2393
symbol︰ 不能在段领域中分配每个 appdomain 符号  
  
 **/Clr: pure**和**/clr: safe**编译器选项不推荐使用 Visual Studio 2015 中。  
  
 使用[appdomain](../../cpp/appdomain.md)变量意味着您用编译**/clr: pure**或**/clr: safe**，并且安全或纯映像不能包含数据段。  
  
 请参阅[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)有关详细信息。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2393。  
  
```  
// C2393.cpp  
// compile with: /clr:pure /c  
#pragma data_seg("myseg")  
int n = 0;   // C2393  
```
