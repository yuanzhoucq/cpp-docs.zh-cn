---
title: "编译器错误 C2435 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 53a3144fe8e87f36a1a5149d292130a9913b646a
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="compiler-error-c2435"></a>编译器错误 C2435
var︰ 动态初始化需要托管的 CRT，不能使用 /clr: safe 编译  
  
 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
 每个应用程序域全局变量的初始化要求使用编译的 CRT `/clr:pure`，这不会生成可验证的映像。  
  
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
