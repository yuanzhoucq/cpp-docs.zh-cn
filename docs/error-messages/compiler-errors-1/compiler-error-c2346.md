---
title: 编译器错误 C2346 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2346
dev_langs:
- C++
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9459d7330738180e92776e93fcba9a07bfd39640
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222288"
---
# <a name="compiler-error-c2346"></a>编译器错误 C2346
function 不能编译为本机： 原因  
  
 编译器无法编译为 MSIL 的函数。  
  
 有关详细信息，请参阅[managed、 unmanaged](../../preprocessor/managed-unmanaged.md)和[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  不能编译为 MSIL 的函数中删除该代码。  
  
2.  请不编译的模块 **/clr**，或将函数标记为非托管与非托管杂注。  
  
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