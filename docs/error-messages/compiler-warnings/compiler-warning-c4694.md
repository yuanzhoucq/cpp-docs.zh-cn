---
title: "编译器警告 C4694 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4694
dev_langs:
- C++
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: dd8b88c06a24b0f4cfa029a8558a0fc890bba57f
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-c4694"></a>编译器警告 C4694
“class_1”：密封的抽象类不能有基类“base_class”  
  
 一个抽象密封类不能继承自引用类型；一个密封抽象类既不能实现基类函数，也不能用作基类。  
  
 有关详细信息，请参阅[抽象](../../windows/abstract-cpp-component-extensions.md)，[密封](../../windows/sealed-cpp-component-extensions.md)，和[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 以下示例生成 C4694。  
  
```  
// C4694.cpp  
// compile with: /c /clr  
ref struct A {};  
ref struct B sealed abstract : A {};   // C4694  
```
