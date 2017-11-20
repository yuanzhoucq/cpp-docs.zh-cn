---
title: "编译器错误 C2753 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2753
dev_langs: C++
helpviewer_keywords: C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bd852023fe4e8cf9b1845ed1a4d53f937b039211
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2753"></a>编译器错误 C2753
*模板*： 部分专用化不能与匹配主模板参数列表  
  
 如果模板自变量列表与匹配参数列表，则编译器会将其视为相同的模板。 不允许两次定义相同的模板。  
  
## <a name="example"></a>示例
 下面的示例生成 C2753，并演示了如何修复此错误：  
  
```cpp  
// C2753.cpp  
// compile with: cl /c C2753.cpp
template<class T>  
struct A {};  
  
template<class T>  
struct A<T> {};   // C2753  
// try the following line instead  
// struct A<int> {};  
  
template<class T, class U, class V, class W, class X>  
struct B {};  
```