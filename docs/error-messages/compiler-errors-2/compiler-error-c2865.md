---
title: "编译器错误 C2865 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2865
dev_langs:
- C++
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: 3bb55d094e00400c57617857aa1ac29677f1b72a
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2865"></a>编译器错误 C2865
function︰ 非法 handle_or_pointer 比较  
  
 可以将对引用进行比较[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md)或被管理的引用仅对相等性类型，以查看它们是否引用相同的对象 （= =） 或不同的对象 (！ =)。  
  
 无法比较它们的排序顺序，因为.NET 运行时可能会将托管的对象移动在任何时候，从而改变测试的结果。
