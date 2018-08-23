---
title: 编译器错误 C3633 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3633
dev_langs:
- C++
helpviewer_keywords:
- C3633
ms.assetid: 7d65babf-2191-4d67-a69f-f5c4c2ddf946
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 341123f51a065cc8dcd43425f65b21edaf00abbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267018"
---
# <a name="compiler-error-c3633"></a>编译器错误 C3633
不能定义为托管的 type 的成员 member  
  
CLR 引用类数据成员不能是非 POD c + + 类型。  仅可以实例化 POD 本机类型中的 CLR 类型。  例如，POD 类型不能包含复制构造函数或赋值运算符。  
  
## <a name="example"></a>示例  
下面的示例生成 C3633。  
  
```  
// C3633.cpp  
// compile with: /clr /c  
#pragma warning( disable : 4368 )  
  
class A1 {  
public:  
   A1() { II = 0; }  
   int II;  
};  
  
ref class B {  
public:  
   A1 a1;   // C3633  
   A1 * a2;   // OK  
   B() : a2( new A1 ) {}  
    ~B() { delete a2; }  
};  
```  
