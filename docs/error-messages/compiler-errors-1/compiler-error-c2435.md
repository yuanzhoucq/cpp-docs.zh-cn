---
title: "编译器错误 C2435 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2435
dev_langs:
- C++
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
caps.latest.revision: 12
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
ms.openlocfilehash: dbc2045eae70cacd42e13ddb7cc8ecb3d60b8596
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2435"></a>编译器错误 C2435
var︰ 动态初始化需要托管的 CRT，而不能使用 /clr: safe 编译  
  
 **/Clr: pure**和**/clr: safe**编译器选项不推荐使用 Visual Studio 2015 中。  
  
 每个 – 应用程序域的全局变量的初始化，需要使用编译的 CRT `/clr:pure`，这不会产生可验证映像。  
  
 有关详细信息，请参阅[appdomain](../../cpp/appdomain.md)和[过程](../../cpp/process.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2435:  
  
```  
// C2435.cpp  
// compile with: /clr:safe /c  
int globalvar = 0;   // C2435  
  
__declspec(process)  
int globalvar2 = 0;  
```
