---
title: "编译器错误 C2346 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2346
dev_langs:
- C++
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: bf0133aba65b8477bd949cd90b51edbd407bcda7
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2346"></a>编译器错误 C2346
function 不能编译为本机： 原因  
  
 编译器无法编译为 MSIL 的函数。  
  
 有关详细信息，请参阅[managed、 unmanaged](../../preprocessor/managed-unmanaged.md)和[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  不能编译为 MSIL 的函数中删除该代码。  
  
2.  请不编译的模块**/clr**，或将函数标记为非托管与非托管杂注。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2346。  
  
```  
// C2346.cpp  
// processor: x86  
// compile with: /clr   
// C2346 expected  
struct S  
{  
   S()  
   {  
      { __asm { nop } }  
   }  
   virtual __clrcall ~S() { }  
};  
  
void main()  
{  
   S s;  
}  
```
