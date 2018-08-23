---
title: 如何： 使用 gcnew 创建值类型和使用隐式装箱 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- gcnew keyword [C++], creating value types
- boxing, implicit
- value types, creating
ms.assetid: ceb48841-d6bd-47be-a167-57f44c961603
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6d50b36b69d8be5c1e6311b257de4c31ce1ab0bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33128792"
---
# <a name="how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing"></a>如何：使用 gcnew 创建值类型并使用隐式装箱
使用[gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)对值类型将创建装箱的值类型，然后可以在托管的垃圾回收堆放置。  
  
## <a name="example"></a>示例  
  
```  
// vcmcppv2_explicit_boxing4.cpp  
// compile with: /clr  
public value class V {  
public:  
   int m_i;  
   V(int i) : m_i(i) {}  
};  
  
public ref struct TC {  
   void do_test(V^ v) {  
      if (v != nullptr)  
         ;  
      else  
         ;  
   }  
};  
  
int main() {  
   V^ v = gcnew V(42);  
   TC^ tc = gcnew TC;  
   tc->do_test(v);  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [装箱](../windows/boxing-cpp-component-extensions.md)