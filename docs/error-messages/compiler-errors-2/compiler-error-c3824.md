---
title: 编译器错误 C3824 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3824
dev_langs:
- C++
helpviewer_keywords:
- C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e5202ff0236fca8d14c87bd55f1d314baa6bb2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268887"
---
# <a name="compiler-error-c3824"></a>编译器错误 C3824
member： 此类型不能出现在此上下文 （函数参数、 返回类型或静态成员）  
  
 钉住指针不能为函数参数、 返回类型，或声明`static`。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3824:  
  
```  
// C3824a.cpp  
// compile with: /clr /c  
void func() {  
   static pin_ptr<int> a; // C3824  
   pin_ptr<int> b; // OK  
}  
```  
