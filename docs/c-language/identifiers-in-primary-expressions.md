---
title: "主要表达式中的标识符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- identifiers, designating objects
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e507c2b7c05f9ea818f55b10d222592fe0172cc0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="identifiers-in-primary-expressions"></a>主要表达式中的标识符
标识符可具有整数、float、`enum`、`struct`、union、数组、指针或函数类型。 如果已将标识符声明为指定对象（此时为左值）或声明为函数（此时为函数指示符），则它是主函数。 有关左值的定义，请参阅[左值和右值表达式](../c-language/l-value-and-r-value-expressions.md)。  
  
 数组标识符表示的指针值不是一个变量，因此数组标识符不能构成赋值运算的左操作数，因而不是一个可修改的左值。  
  
 声明为函数的标识符表示其值是函数的地址的指针。 该指针为返回指定类型的值的函数寻址。 因此，函数标识符也不能是赋值运算中的左值。 有关详细信息，请参阅[标识符](../c-language/c-identifiers.md)。  
  
## <a name="see-also"></a>请参阅  
 [C 主要表达式](../c-language/c-primary-expressions.md)