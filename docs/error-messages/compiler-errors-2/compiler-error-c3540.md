---
title: "编译器错误 C3540 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3540
dev_langs: C++
helpviewer_keywords: C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0ff7a017ce86e567d0aabcf494e11f48d1cdea05
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3540"></a>编译器错误 C3540
type： 不能 sizeof 应用于包含 auto 的类型  
  
 [Sizeof](../../cpp/sizeof-operator.md)运算符不能应用于指定的类型，因为它包含`auto`说明符。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3540。  
  
```  
// C3540.cpp  
// Compile with /Zc:auto  
int main() {  
    auto x = 123;  
    sizeof(x);    // OK  
    sizeof(auto); // C3540  
    return 0;  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)   
 [/Zc: auto （推导变量类型）](../../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof 运算符](../../cpp/sizeof-operator.md)