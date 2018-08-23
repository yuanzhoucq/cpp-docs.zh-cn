---
title: 编译器错误 C3394 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3394
dev_langs:
- C++
helpviewer_keywords:
- C3394
ms.assetid: 4e025d79-27ba-43c8-b0d9-839ecef98126
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66d99ff65ba7fa6fd463a1266cdc506d7fd0a11b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251672"
---
# <a name="compiler-error-c3394"></a>编译器错误 C3394
constraint 子句有语法错误：应为类型却发现“identifier”  
  
 约束格式不正确。  有关详细信息，请参阅[泛型类型参数的约束 (C + + /cli CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3394：  
  
```  
// C3394.cpp  
// compile with: /clr /c  
ref class MyClass {};  
ref class R {  
   generic<typename T>  
   where T : static   // C3394  
   // try the following line instead  
   // where T : MyClass  
   void f() {}  
};  
```