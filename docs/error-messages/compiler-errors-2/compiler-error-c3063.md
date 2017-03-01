---
title: "编译器错误 C3063 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3063
dev_langs:
- C++
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
caps.latest.revision: 9
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
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: ce6a597e0246cee5c62dd6612d48fe4946505e77
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3063"></a>编译器错误 C3063
运算符 operator︰ 所有操作数必须都具有相同的枚举类型  
  
当在枚举器上使用运算符，这两个操作数必须是枚举类型。 有关详细信息，请参阅[如何︰ 定义和使用枚举在 C + + /cli CLI](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)。  
  
## <a name="example"></a>示例  
下面的示例生成 C3063 并演示如何修复此错误︰  
  
```  
// C3063.cpp  
// compile with: /clr  
enum class E { a, b } e, mask;  
int main() {  
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)  
  
   if ( ( e & mask ) != E() )   // OK  
      ;  
}  
```
