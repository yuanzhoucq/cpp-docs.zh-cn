---
title: 编译器警告 （等级 1） C4369 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4369
dev_langs:
- C++
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63445f0713b43ce7fde418ebd9d65403965c07ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276524"
---
# <a name="compiler-warning-level-1-c4369"></a>编译器警告（等级 1）C4369
枚举： 枚举器值 value 不能表示为 type，值为 new_value  
  
 计算的枚举数大于指定的基础类型的最大值。  这会导致溢出，编译器包装类型的最低可能值的枚举器值。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4369。  
  
```  
// C4369.cpp  
// compile with: /W1  
int main() {  
   enum Color: char { red = 0x7e, green, blue };   // C4369  
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK  
}  
```