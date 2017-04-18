---
title: "编译器警告 C4936 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4936
dev_langs:
- C++
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
caps.latest.revision: 12
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
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 58d702067c186eeeea94768a03836b64577961ca
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-c4936"></a>编译器警告 C4936
只有使用 /clr 或 /clr:pure 编译时，才支持此 __declspec  
  
 **/Clr: pure**编译器选项已弃用 Visual Studio 2015 中。  
  
 一个`__declspec`但使用了修饰符`__declspec`修饰符才编译之一时有效[/clr](../../build/reference/clr-common-language-runtime-compilation.md)选项。  
  
 有关详细信息，请参阅[appdomain](../../cpp/appdomain.md)和[过程](../../cpp/process.md)。  
  
 始终发出 C4936 错误。  您可以禁用与 C4936[警告](../../preprocessor/warning.md)杂注。  
  
 下面的示例生成 C4936：  
  
```  
// C4936.cpp  
// compile with: /c  
// #pragma warning (disable : 4936)  
__declspec(process) int i;   // C4936  
__declspec(appdomain) int j;   // C4936  
```
