---
title: "编译器错误 C2581 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2581
dev_langs:
- C++
helpviewer_keywords:
- C2581
ms.assetid: 24a4e4c1-24d3-4e42-b760-7dcaf9740b16
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 205d972237a71a05839dbc4236d248a11e6ee53d
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

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
