---
title: 编译器错误 C2581 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2581
dev_langs:
- C++
helpviewer_keywords:
- C2581
ms.assetid: 24a4e4c1-24d3-4e42-b760-7dcaf9740b16
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3cb826519ad9137a0e980fd1734b57e8a715f438
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231189"
---
# <a name="compiler-error-c2581"></a>编译器错误 C2581
type： 静态运算符 = 是非法的函数  
  
 分配 (`=`) 运算符未正确声明为`static`。 赋值运算符不能为`static`。 有关详细信息，请参阅[用户定义的运算符 (C + + /cli CLI)](../../dotnet/user-defined-operators-cpp-cli.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2581。  
  
```  
// C2581.cpp  
// compile with: /clr /c  
ref struct Y {  
   static Y ^ operator = (Y^ me, int i);   // C2581  
   Y^ operator =(int i);   // OK  
};  
```