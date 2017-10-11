---
title: "编译器错误 C3753 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3753
dev_langs:
- C++
helpviewer_keywords:
- C3753
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 93150c018159a649e772406a5a9a96836b87da8a
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3753"></a>编译器错误 C3753
不允许泛型属性。  
  
 泛型参数列表只能出现在托管的类、 结构或函数。  
  
 有关详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)和[属性](../../windows/property-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3753。  
  
```  
// C3753.cpp  
// compile with: /clr /c  
ref struct A {  
   generic <typename T>  
   property int i;   // C3753 error  
};  
```
