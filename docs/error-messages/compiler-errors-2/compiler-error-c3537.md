---
title: "编译器错误 C3537 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3537
dev_langs: C++
helpviewer_keywords: C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f425ee0d93a277bac5dc1f0a798c1a7cc3ed3bac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3537"></a>编译器错误 C3537
type： 你不能强制转换为包含 auto 的类型  
  
 不能强制转换为指定的类型的变量，因为该类型包含`auto`关键字和默认值[/zc: auto](../../build/reference/zc-auto-deduce-variable-type.md)编译器选项将生效。  
  
## <a name="example"></a>示例  
 下面的代码会产生 C3537，因为变量强制转换为包含的类型`auto`关键字。  
  
```  
// C3537.cpp  
// Compile with /Zc:auto  
int main()  
{  
   int value = 123;  
   auto(value);                        // C3537  
   (auto)value;                        // C3537  
   auto x1 = auto(value);              // C3537  
   auto x2 = (auto)value;              // C3537  
   auto x3 = static_cast<auto>(value); // C3537  
   return 0;  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)