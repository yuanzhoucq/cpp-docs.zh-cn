---
title: "编译器错误 C3290 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3290
dev_langs: C++
helpviewer_keywords: C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 28f350f8cf522032fbdaad22098508ec8545ee01
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3290"></a>编译器错误 C3290
“type”: 普通属性不能具有引用类型  
  
 未正确声明属性。 当声明普通属性时，编译器创建一个此属性将更新的变量，类中不能有跟踪引用变量。  
  
 请参阅[属性](../../windows/property-cpp-component-extensions.md)和[跟踪引用运算符](../../windows/tracking-reference-operator-cpp-component-extensions.md)有关详细信息。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3290。  
  
```  
// C3290.cpp  
// compile with: /clr /c  
ref struct R {};  
  
ref struct X {  
   R^ mr;  
  
   property R % y;   // C3290  
   property R ^ x;   // OK  
  
   // OK  
   property R% prop {  
      R% get() {   
         return *mr;   
      }  
  
      void set(R%) {}  
   }  
};  
  
int main() {  
   X x;  
   R% xp = x.prop;  
}  
```