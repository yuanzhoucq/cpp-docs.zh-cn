---
title: 编译器错误 C3481 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3481
dev_langs:
- C++
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77fc0f542a74cb077e59882e31dd1acb10c7b7e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3481"></a>编译器错误 C3481
“var”：未找到 lambda 捕获变量  
  
 编译器未找到传递给 lambda 表达式捕获列表的变量的定义。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   从 lambda 表达式的捕获列表中删除该变量。  
  
## <a name="example"></a>示例  
 下面的示例由于未定义变量 `n` 而生成 C3481：  
  
```  
// C3481.cpp  
  
int main()  
{  
   [n] {}(); // C3481  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)