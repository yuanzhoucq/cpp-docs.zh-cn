---
title: 编译器错误 C3540 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3540
dev_langs:
- C++
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27bae73d387612be41d8462bf0e5e0d82516ba1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256039"
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
  
## <a name="see-also"></a>请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)   
 [/Zc: auto （推导变量类型）](../../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof 运算符](../../cpp/sizeof-operator.md)