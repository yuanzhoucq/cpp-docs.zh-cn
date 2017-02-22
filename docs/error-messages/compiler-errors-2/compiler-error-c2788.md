---
title: "编译器错误 C2788 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2788"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2788"
ms.assetid: 8688fc5c-e652-43b4-b407-9c488c76f2db
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2788
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 与此对象关联的 GUID 不止一个  
  
 [\_\_uuidof](../../cpp/uuidof-operator.md) 运算符采用附加了 GUID 的用户定义类型，或采用这种用户定义类型的对象。  当参数是具有多个 GUID 的对象时，发生此错误。  
  
 下面的示例生成 C2788：  
  
```  
// C2788.cpp  
#include <windows.h>  
struct __declspec(uuid("00000001-0000-0000-0000-000000000000")) A {};  
struct __declspec(uuid("{00000002-0000-0000-0000-000000000000}")) B {};  
template <class T, class U> class MyClass {};  
  
typedef MyClass<A,B> MyBadClass;  
typedef MyClass<A,A> MyGoodClass;  
  
int main() {  
   __uuidof(MyBadClass);    // C2788  
   // try the following line instead  
   __uuidof(MyGoodClass);  
}  
```