---
title: "编译器错误 C2788 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2788
dev_langs: C++
helpviewer_keywords: C2788
ms.assetid: 8688fc5c-e652-43b4-b407-9c488c76f2db
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3629bb6d9196f8f1f24daea581f581c805d4b542
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2788"></a>编译器错误 C2788
identifier： 与此对象关联的多个 GUID  
  
 [__Uuidof](../../cpp/uuidof-operator.md)运算符采用与附加的 GUID 或用户定义类型的对象的用户定义的类型。 如果参数为具有多个 Guid 的对象，则会发生此错误。  
  
 下面的示例生成 C2788:  
  
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