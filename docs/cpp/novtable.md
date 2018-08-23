---
title: novtable |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- novtable_cpp
dev_langs:
- C++
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5deee0209866580afd038fbce068a9275f5b5874
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406963"
---
# <a name="novtable"></a>novtable
## <a name="microsoft-specific"></a>Microsoft 专用  
 这是 **__declspec**扩展的特性。  
  
 这种形式的 **__declspec**可应用于任何类声明，但只应用于纯接口类，即，永远不会将其自身实例化的类。 **__Declspec**将阻止编译器生成用于初始化的构造函数和类的析构函数中的 vfptr 的代码。 在许多情况下，这将移除对与类关联的 vtable 的唯一引用，因此链接器将移除它。 使用这种形式的 **__declspec**可能会导致代码大小的显著降低。  
  
 如果你尝试实例化类标记有**novtable** ，然后访问类成员，您将收到访问冲突 (AV)。  
  
## <a name="example"></a>示例  
  
```cpp 
// novtable.cpp  
#include <stdio.h>  
  
struct __declspec(novtable) X {  
   virtual void mf();  
};  
  
struct Y : public X {  
   void mf() {  
      printf_s("In Y\n");  
   }  
};  
  
int main() {  
   // X *pX = new X();  
   // pX->mf();   // Causes a runtime access violation.  
  
   Y *pY = new Y();  
   pY->mf();  
}  
```  
  
```Output  
In Y  
```  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [__declspec](../cpp/declspec.md)   
 [关键字](../cpp/keywords-cpp.md)