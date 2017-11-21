---
title: "编译器错误 C3536 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3536
dev_langs: C++
helpviewer_keywords: C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 90db065c9a16e72a396bd1c1ae54bb99cdb97153
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3536"></a>编译器错误 C3536
symbol： 不能在初始化之前  
  
 在初始化之前，不能使用指定的符号。 在实践中，这意味着无法使用变量来初始化自身。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  未初始化变量对其自身。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3536，因为每个变量初始化与其自身。  
  
```  
// C3536.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto a = a;     //C3536  
   auto b = &b;    //C3536  
   auto c = c + 1; //C3536  
   auto* d = &d;   //C3536  
   auto& e = e;    //C3536  
   return 0;  
};  
```  
  
## <a name="see-also"></a>另请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)