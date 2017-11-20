---
title: "编译器错误 C3104 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3104
dev_langs: C++
helpviewer_keywords: C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 837ff564bc3b2795bce6de69caa85e1d1dcf2766
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3104"></a>编译器错误 C3104
非法特性自变量  
  
 指定属性的无效自变量。  
  
 请参阅[特性参数类型](../../windows/attribute-parameter-types-cpp-component-extensions.md)有关详细信息。  
  
 此错误可能来自于为 Visual c + + 2005年执行的编译器一致性工作： 不再将从聚合初始化列表推导时将托管的数组传递给自定义特性，数组的类型。 编译器现在需要你指定的数组初始值设定项列表的类型。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3104。  
  
```  
// C3104a.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::Class)]  
public ref struct ABC : public Attribute {  
   ABC(array<int>^){}  
   array<double> ^ param;  
};  
  
[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104  
// try the following line instead  
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]   
ref struct AStruct{};  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C3104。  
  
```  
// C3104b.cpp  
// compile with: /clr /c  
// C3104 expected  
using namespace System;  
  
int func() {  
   return 0;   
}  
  
[attribute(All)]  
ref class A {  
public:   
   A(int) {}  
};  
  
// Delete the following 2 lines to resolve.  
[A(func())]  
ref class B {};  
  
// OK  
[A(0)]  
ref class B {};  
```  
