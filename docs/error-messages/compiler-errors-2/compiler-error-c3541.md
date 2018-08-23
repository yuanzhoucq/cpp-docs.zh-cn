---
title: 编译器错误 C3541 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3541
dev_langs:
- C++
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2440d1ab91cda00240d99d2188365754bd34fb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255105"
---
# <a name="compiler-error-c3541"></a>编译器错误 C3541
type: typeid 不能应用于包含 auto 的类型  
  
 [Typeid](../../windows/typeid-cpp-component-extensions.md)运算符不能应用于指定的类型，因为它包含`auto`说明符。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3541。  
  
```  
// C3541.cpp  
// Compile with /Zc:auto  
#include <typeinfo>  
int main() {  
    auto x = 123;  
    typeid(x);    // OK  
    typeid(auto); // C3541  
    return 0;  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)   
 [/Zc: auto （推导变量类型）](../../build/reference/zc-auto-deduce-variable-type.md)   
 [typeid](../../windows/typeid-cpp-component-extensions.md)