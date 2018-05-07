---
title: 编译器错误 C3069 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3069
dev_langs:
- C++
helpviewer_keywords:
- C3069
ms.assetid: ca94291b-2bb4-4e3f-9acf-534234b83513
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b68471b866888baf0de11915dd16a150e12a8c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3069"></a>编译器错误 C3069
“operator”: 不允许用于枚举类型  
  
 CLR 枚举不支持运算符。  有关详细信息，请参阅[如何： 定义和使用枚举在 C + + /cli CLI](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3069：  
  
```  
// C3069.cpp  
// compile with: /clr  
enum struct E { e1 };  
enum F { f1 };  
  
int main() {  
   E e = E::e1;  
   bool tf;  
   tf = !e;   // C3069  
  
   // supported for native enums  
   F f = f1;  
   tf = !f;  
}  
```