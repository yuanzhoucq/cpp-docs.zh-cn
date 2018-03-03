---
title: "编译器错误 C3288 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3288
dev_langs:
- C++
helpviewer_keywords:
- C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 138afdc77c6631b2699ec645e65032217f9e18d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3288"></a>编译器错误 C3288
type： 非法的取消引用的句柄类型  
  
 编译器检测到句柄类型非法取消引用。 你可以取消引用句柄类型，并将其分配为引用。 有关详细信息，请参阅[跟踪引用运算符](../../windows/tracking-reference-operator-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3288。  
  
```  
// C3288.cpp  
// compile with: /clr  
ref class R {};  
int main() {  
   *(System::Object^) nullptr;   // C3288  
  
// OK  
   (System::Object^) nullptr;   // OK  
   R^ r;  
   R% pr = *r;  
}  
```