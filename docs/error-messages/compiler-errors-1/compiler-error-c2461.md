---
title: 编译器错误 C2461 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2461
dev_langs:
- C++
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47aee3122dad3e875cf58d5a41bcadda297e1463
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2461"></a>编译器错误 C2461
  
> *类*： 缺少正式参数的构造函数语法  
  
 类的构造函数不指定任何形式的参数。 构造函数的声明必须指定形参列表。 列表可以为空。  
  
若要解决此问题，添加一对括号的声明后*类*:: **类*。  
  
## <a name="example"></a>示例  
  
下面的示例演示如何修复错误 C2461:  
  
```cpp  
// C2461.cpp  
// compile with: /c  
class C {  
   C::C;     // C2461  
   C::C();   // OK  
};  
```