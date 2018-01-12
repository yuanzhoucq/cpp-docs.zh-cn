---
title: "编译器错误 C3399 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3399
dev_langs: C++
helpviewer_keywords: C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a55a6d40d6d39b368c31a2716c14d05e0e49a78c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3399"></a>编译器错误 C3399
“type”：创建泛型参数的实例时无法提供变量  
  
 当指定 `gcnew()` 约束时，指定约束类型将具有无参数的构造函数。 因此，尝试实例化此类型并传递参数是错误的。  
  
 请参阅[泛型类型参数的约束 (C + + /cli CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)有关详细信息。  
  
## <a name="example"></a>示例  
 以下示例生成 C3399。  
  
```  
// C3399.cpp  
// compile with: /clr /c  
generic <class T>   
where T : gcnew()  
void f() {  
   T t = gcnew T(1);   // C3399  
   T t2 = gcnew T();   // OK  
}  
```