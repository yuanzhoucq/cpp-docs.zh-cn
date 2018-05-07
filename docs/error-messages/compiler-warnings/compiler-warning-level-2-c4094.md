---
title: 编译器警告 （等级 2） C4094 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4094
dev_langs:
- C++
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9deae6a0e21fcb7dd4f09de07e65445dc9595932
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-2-c4094"></a>编译器警告 （等级 2） C4094
未标记 token 未声明符号  
  
 编译器检测到使用标记的结构、 联合或类的空声明。 声明将被忽略。  
  
## <a name="example"></a>示例  
  
```  
// C4094.cpp  
// compile with: /W2  
struct  
{  
};   // C4094  
  
int main()  
{  
}  
```  
  
 这种情况会生成在 ANSI 兼容性错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。