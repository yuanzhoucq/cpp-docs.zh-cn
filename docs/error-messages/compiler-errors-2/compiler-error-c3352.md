---
title: "编译器错误 C3352 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3352
dev_langs: C++
helpviewer_keywords: C3352
ms.assetid: f233bed7-474e-425f-aad2-7801578169d4
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 65643abc883cfd0674dbb908c8ab26f274f65cd4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3352"></a>编译器错误 C3352
function： 指定的函数委托类型 type 不匹配  
  
 参数列出`function`和委托不匹配。  
  
 有关详细信息，请参阅[委托 （c + + 组件扩展）](../../windows/delegate-cpp-component-extensions.md)。  
  
 下面的示例生成 C3352:  
  
```  
// C3352.cpp  
// compile with: /clr  
delegate int D( int, int );  
ref class C {  
public:  
   int mf( int ) {  
      return 1;  
   }  
  
   // Uncomment the following line to resolve.  
   // int mf(int, int) { return 1; }  
};  
  
int main() {  
   C^ pC = gcnew C;  
   System::Delegate^ pD = gcnew D( pC, &C::mf );   // C3352  
}  
```  
