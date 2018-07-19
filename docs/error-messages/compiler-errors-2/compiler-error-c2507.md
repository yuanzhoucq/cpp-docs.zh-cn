---
title: 编译器错误 C2507 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2507
dev_langs:
- C++
helpviewer_keywords:
- C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82bd4fb028712093a44ada4ae58e97c2fbcf7eed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230530"
---
# <a name="compiler-error-c2507"></a>编译器错误 C2507
identifier： 基的类上的虚拟修饰符太多  
  
 类或结构声明为`virtual`不止一次。 只有一个`virtual`修饰符可以出现在列表中每个类的基类，这些类。  
  
 下面的示例生成 C2507:  
  
```  
// C2507.cpp  
// compile with: /c  
class A {};  
class B : virtual virtual public A {};   // C2507  
class C : virtual public A {};   // OK  
```