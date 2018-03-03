---
title: "编译器警告 （等级 1） C4540 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4540
dev_langs:
- C++
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aaaef1edaa6af093ae03fe69231a9686e3d087a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4540"></a>编译器警告（等级 1）C4540
dynamic_cast 用于将转换为无法访问或不明确的基;运行时测试将失败 (如到 type2 的 type1)  
  
 你使用`dynamic_cast`将从一种类型转换为另一个。 编译器确定该强制转换将始终失败 (返回**NULL**) 因为基类不可访问 (`private`，例如) 或不明确 （例如类层次结构中, 出现一次以上）。  
  
 下面显示此警告的示例。 类**B**派生自类**A**。该程序使用`dynamic_cast`将从类强制转换**B** （派生的类） 与类**A**，这始终将失败，因为类**B**是`private`，因此无法访问。 正在更改的访问权限**A**到**公共**将解决此警告。  
  
```  
// C4540.cpp  
// compile with: /W1  
  
struct A {   
   virtual void g() {}  
};  
  
struct B : private A {  
   virtual void g() {}  
};  
  
int main() {  
   B b;  
   A * ap = dynamic_cast<A*>(&b);   // C4540  
}  
```