---
title: "编译器警告 （等级 3） C4373 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4373
dev_langs:
- C++
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 36d4491f8a621f1ee97de9682faf94a26a89fa70
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-3-c4373"></a>编译器警告（等级 3）C4373
“%$S”: 虚函数重写“%$pS”，当参数只在 const/volatile 限定符上有差异时，早期版本的编译器未进行重写  
  
 你的应用程序包含一个重写基类中的虚拟方法的派生类中的方法和中重写方法的参数仅相差[const](../../cpp/const-cpp.md)或[易失性](../../cpp/volatile-cpp.md)限定符与虚拟方法的参数。 这就意味着编译器必须将函数引用绑定到基类或派生类中的方法。  
  
 版本的编译器之前[!INCLUDE[cpp_orcas_long](../../cpp/includes/cpp_orcas_long_md.md)]将函数绑定到的方法中的基类，然后发出一条警告消息。 后续版本的编译器忽略 `const` 或 `volatile` 限定符，将函数绑定到派生类中的方法，然后发出警告 `C4373`。 后一种行为符合 C++ 标准。  
  
## <a name="example"></a>示例  
 下面的代码示例将生成警告 C4373。  
  
```  
// c4373.cpp  
// compile with: /c /W3  
#include <stdio.h>  
struct Base  
{  
    virtual void f(int i) {  
        printf("base\n");  
    }  
};  
struct Derived : Base  
{  
    void f(const int i) {  // C4373  
        printf("derived\n");  
    }  
};  
void main()  
{  
    Derived d;  
    Base* p = &d;  
    p->f(1);  
}  
```  
  
```Output  
derived  
```
