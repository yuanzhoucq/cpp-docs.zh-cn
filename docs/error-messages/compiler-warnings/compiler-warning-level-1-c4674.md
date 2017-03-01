---
title: "编译器警告 （等级 1） C4674 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4674
dev_langs:
- C++
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
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
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: ca99a22e6f91f44af58a1421d59151597017cddb
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4674"></a>编译器警告（等级 1）C4674
“方法”应声明为“静态”，而且只能有一个参数  
  
转换运算符的签名不正确。 该方法不被视为用户定义的转换。 定义运算符的详细信息，请参阅[用户定义运算符 (C + + /cli CLI)](../../dotnet/user-defined-operators-cpp-cli.md)和[用户定义的转换 (C + + /cli CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4674。  
  
```  
// C4674.cpp  
// compile with: /clr /WX /W1 /LD  
ref class G {  
   int op_Implicit(int i) {   // C4674  
      return 0;  
   }  
};  
```  

