---
title: "编译器错误 C2144 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2144
dev_langs:
- C++
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0f541465009dcc137b8853351d10ceb9d5db4d05
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2144"></a>编译器错误 C2144
语法错误: type 前面应带有 token  
  
 编译器预期`token`和找到`type`相反。  
  
 缺少右大括号、 右括号或分号可能导致此错误。  
  
 尝试从包含一个空白字符的 CLR 关键字创建的宏时，也会发生 C2144。  
  
 如果你尝试进行类型转发，还可能会看到 C2144。 请参阅[类型转发 (C + + /cli CLI)](../../windows/type-forwarding-cpp-cli.md)有关详细信息。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2144。  
  
```  
// C2144.cpp  
// compile with: /clr /c  
#define REF ref  
REF struct MyStruct0;   // C2144  
  
// OK  
#define REF1 ref struct  
REF1 MyStruct1;  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C2144。  
  
```  
// C2144_2.cpp  
// compile with: /clr /c  
ref struct X {  
  
   property double MultiDimProp[,,] {   // C2144  
   // try the following line instead  
   // property double MultiDimProp[int , int, int] {  
      double get(int, int, int) { return 1; }  
      void set(int i, int j, int k, double l) {}  
   }  
  
   property double MultiDimProp2[] {   // C2144  
   // try the following line instead  
   // property double MultiDimProp2[int] {  
      double get(int) { return 1; }  
      void set(int i, double l) {}  
   }  
};  
```
