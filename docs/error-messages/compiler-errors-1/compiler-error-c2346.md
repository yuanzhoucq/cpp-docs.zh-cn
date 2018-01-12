---
title: "编译器错误 C2346 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2346
dev_langs: C++
helpviewer_keywords: C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 769d5addc47ead8ffb338d5fbef313cd46735d31
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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