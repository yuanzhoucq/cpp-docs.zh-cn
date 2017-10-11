---
title: "编译器错误 C3846 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3846
dev_langs:
- C++
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 58ffd3f240505d173014f1f9b358b4957a41eaf5
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3846"></a>编译器错误 C3846
symbol： 无法导入 assembly2 中的符号： 如 symbol 具有已导入从另一个程序集"1"  
  
 不是从被引用程序集导入符号，因为以前从被引用程序集将它导入。  
  
## <a name="example"></a>示例
下面的示例生成 C3846:  
  
```  
// C3846a.cpp  
// compile with: /LD /clr  
public ref struct G  
{  
};  
```  
  
 然后编译此：  
  
```  
// C3846b.cpp  
// compile with: /clr  
#using "c3846a.dll"  
#using "c3846a.obj"   // C3846  
  
int main()  
{  
}  
```  

