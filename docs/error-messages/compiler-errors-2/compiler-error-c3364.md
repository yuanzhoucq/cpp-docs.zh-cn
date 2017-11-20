---
title: "编译器错误 C3364 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3364
dev_langs: C++
helpviewer_keywords: C3364
ms.assetid: 98654741-60fe-4472-a6af-e580f8c0a6e1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6ca9b4d5ca4362e1d728a854bb776573d25969d7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3364"></a>编译器错误 C3364
delegate： 委托构造函数： 参数必须是指向托管类的成员函数或全局函数  
  
 该委托的构造函数的第二个参数采用成员函数的地址或任何类的静态成员函数的地址。 同时将被视为简单的地址。  
  
 下面的示例生成 C3364:  
  
```  
// C3364_2.cpp  
// compile with: /clr  
  
delegate int D( int, int );  
  
ref class C {  
public:  
   int mf( int, int ) {  
      return 1;  
   }  
};  
  
int main() {  
   C^ pC = gcnew C;  
   System::Delegate^ pD = gcnew D( pC,pC->mf( 1, 2 ) ); // C3364  
  
   // try the following line instead  
   // System::Delegate^ pD = gcnew D(pC, &C::mf);  
}  
```  
