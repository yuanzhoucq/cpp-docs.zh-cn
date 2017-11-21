---
title: "编译器警告 C4867 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4867
dev_langs: C++
helpviewer_keywords: C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 352b38744d83b3dc163125ff5ec8d80165f60c9a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4867"></a>编译器警告 C4867
function： 函数调用缺少自变量列表;使用调用创建指向成员的指针  
  
 指向成员函数的未正确初始化。  
  
 此警告可以来自于为 Visual c + + 2005年执行的编译器一致性工作： 增强的指针到成员一致性。  Visual c + + 2005年之前的版本编译的代码现在将生成 C4867。  
  
 始终作为错误发出此警告。 请使用 [警告](../../preprocessor/warning.md) 杂注禁用此警告。 有关 C4867 和 MFC/ATL 的详细信息，请参阅[_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4867。  
  
```  
// C4867.cpp  
// compile with: /c  
class A {  
public:  
   void f(int) {}  
  
   typedef void (A::*TAmtd)(int);  
  
   struct B {  
      TAmtd p;  
   };  
  
   void g() {  
      B b = {f};   // C4867  
      B b2 = {&A::f};   // OK  
   }  
};  
```