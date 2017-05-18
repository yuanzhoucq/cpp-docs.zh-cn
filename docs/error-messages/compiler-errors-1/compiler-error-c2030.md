---
title: "编译器错误 C2030 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2030
dev_langs:
- C++
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
caps.latest.revision: 7
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: c76a4fc5de139c2cc9f6802fc66526f291b862a2
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="compiler-error-c2030"></a>编译器错误 C2030
具有“protected private”可访问性的析构函数不能是声明为“sealed”的类的成员  
  
 声明为 `sealed` 的 Windows 运行时类不能具有受保护的私有析构函数。 已密封的类型上只允许使用公共虚拟和私有非虚拟析构函数。 有关详细信息，请参阅[Ref 类和结构](../../cppcx/ref-classes-and-structs-c-cx.md)。  
  
 若要修复此错误，请更改析构函数的可访问性。
