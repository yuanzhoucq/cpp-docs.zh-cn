---
title: "编译器错误 C3084 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3084
dev_langs: C++
helpviewer_keywords: C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eb33859f52cf608c940561cce2562f9c601d2bf4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3084"></a>编译器错误 C3084
“函数”: 终结器/析构函数不能是“关键字”  
  
 未正确声明终结器或析构函数。  
  
 例如，析构函数不应标记为密封。  派生类型无法访问析构函数。  有关详细信息，请参阅[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)和[析构函数和终结器中如何： 定义和使用类和结构 (C + + /cli CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。  
  
## <a name="example"></a>示例  
 以下示例生成 C3084。  
  
```  
// C3084.cpp  
// compile with: /clr /c  
ref struct R {  
protected:  
   !R() sealed;   // C3084  
   !R() abstract;   // C3084  
   !R();  
};  
```