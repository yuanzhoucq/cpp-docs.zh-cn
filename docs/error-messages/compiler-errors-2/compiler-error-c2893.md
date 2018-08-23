---
title: 编译器错误 C2893 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2893
dev_langs:
- C++
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db3b71a05ece6b79672d47699dc68e0eb5bb1f60
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246693"
---
# <a name="compiler-error-c2893"></a>编译器错误 C2893
未能特殊化函数模板的模板名称  
  
 编译器未能特殊化函数模板。 可以有多种原因会导致此错误。  
  
 通常情况下，解决 C2893 错误的方法是先查看函数的签名并确保可以实例化每个类型。  
  
## <a name="example"></a>示例  
 C2893 的发生是因为`f`的模板参数`T`推导为`std::map<int,int>`，但`std::map<int,int>`不具备成员`data_type`(`T::data_type`不使用实例化`T = std::map<int,int>`。)。 下面的示例生成 C2893。  
  
```  
// C2893.cpp  
// compile with: /c /EHsc  
#include<map>  
using namespace std;  
class MyClass {};  
  
template<class T>   
inline typename T::data_type  
// try the following line instead  
// inline typename  T::mapped_type  
f(T const& p1, MyClass const& p2);  
  
template<class T>  
void bar(T const& p1) {  
    MyClass r;  
    f(p1,r);   // C2893  
}  
  
int main() {  
   map<int,int> m;  
   bar(m);  
}  
```