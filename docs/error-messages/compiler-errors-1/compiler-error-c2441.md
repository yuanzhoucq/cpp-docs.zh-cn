---
title: "编译器错误 C2441 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2441
dev_langs:
- C++
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
caps.latest.revision: 6
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
ms.openlocfilehash: 1b98c85df0db4e947ceb5722715f5d020e1ecbec
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2441"></a>编译器错误 C2441
variable: __declspec(process) 用声明的符号必须是在 /clr: pure 模式  
  
 **/Clr: pure**和**/clr: safe**编译器选项不推荐使用 Visual Studio 2015 中。  
  
 默认情况下，变量是为每个应用程序域下**/clr: pure**。 一个变量标记为`__declspec(process)`下**/clr: pure**很容易导致错误，如果在一个应用程序域中修改和读取在另一个。  
  
 编译器因此，每个进程变量是强制实施`const`下**/clr: pure**，仅在所有应用程序域中的进行读取它们。  
  
 有关详细信息，请参阅[过程](../../cpp/process.md)和[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2441。  
  
```  
// C2441.cpp  
// compile with: /clr:pure /c  
__declspec(process) int i;   // C2441  
__declspec(process) const int j = 0;   // OK  
```
