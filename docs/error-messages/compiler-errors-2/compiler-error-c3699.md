---
title: "编译器错误 C3699 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3699
dev_langs: C++
helpviewer_keywords: C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: caabe5d8d9e956081211ef23546f0d720ecdcbd6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3699"></a>编译器错误 C3699
operator： 不能使用类型 type 的此间接寻址  
  
 尝试使用不允许的间接寻址`type`。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3699。  
  
```  
// C3699.cpp  
// compile with: /clr /c  
using namespace System;  
int main() {  
   String * s;   // C3699  
   // try the following line instead  
   // String ^ s2;  
}  
```  
  
## <a name="example"></a>示例  
 Trivial 属性不能具有引用类型。 有关更多信息，请参见 [property](../../windows/property-cpp-component-extensions.md) 。 下面的示例生成 C3699。  
  
```  
// C3699_b.cpp  
// compile with: /clr /c  
ref struct C {  
   property System::String % x;   // C3699  
   property System::String ^ y;   // OK  
};  
```  
  
## <a name="example"></a>示例  
 "指向的指针"语法的等价内容是跟踪引用的句柄。 下面的示例生成 C3699。  
  
```  
// C3699_c.cpp  
// compile with: /clr /c  
using namespace System;  
void Test(String ^^ i);   // C3699  
void Test2(String ^% i);  
```