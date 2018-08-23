---
title: 编译器错误 C3611 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3611
dev_langs:
- C++
helpviewer_keywords:
- C3611
ms.assetid: 42f3e320-41de-420a-bd05-8924cab765aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdd09d86eac5e6182adb9f012c0e450b92d410b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252007"
---
# <a name="compiler-error-c3611"></a>编译器错误 C3611
function： 密封的函数不能有纯说明符  
  
 未正确声明密封的函数。  有关详细信息，请参阅[密封](../../windows/sealed-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3611。  
  
```  
// C3611.cpp  
// compile with: /clr /c  
  
ref struct V {  
   virtual void Test() sealed = 0;   // C3611  
   virtual void Test2() sealed;   // OK  
   virtual void Test3() = 0;   // OK  
};  
```