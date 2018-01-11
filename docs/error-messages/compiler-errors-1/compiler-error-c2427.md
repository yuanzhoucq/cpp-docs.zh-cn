---
title: "编译器错误 C2427 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2427
dev_langs: C++
helpviewer_keywords: C2427
ms.assetid: a7d421af-6180-40b4-b7a6-9f3bc7dfaaf9
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8d3ff74bcc3be300878a2e0767cd61e4be1c1ce8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2427"></a>编译器错误 C2427
class： 无法在此作用域中定义类  
  
 尝试定义嵌套的类，但嵌套的类是基本类，而不是最包含类的成员。  
  
 下面的示例生成 C2427:  
  
```  
// C2427.cpp  
// compile with: /c  
template <class T>   
struct S {  
   struct Inner;   
};   
  
struct Y : S<int> {};   
  
struct Y::Inner {};   // C2427  
  
// OK  
template<typename T>  
struct S<T>::Inner {};  
```