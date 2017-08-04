---
title: "强制转换运算符 | Microsoft Docs"
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
- cast operators
- type casts, operators
- operators [C++], cast
- type conversion, cast operators
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: c1d8315270f6b69629eca55e7aa1c6198f414117
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="cast-operators"></a>强制转换运算符
在特定情况下，类型强制转换提供了用于显式转换对象类型的方法。  
  
## <a name="syntax"></a>语法  
 *cast-expression*：  
 *unary-expression*  
  
 **(**  *type-name*  **)**  *cast-expression*  
  
 在进行类型强制转换后，编译器将 cast-expression 视为类型 type-name。 强制转换可用于在任意标量类型的对象与任何其他标量类型之间进行来回转换。 显式类型强制转换受到确定隐式转换效果的相同规则的约束，如[赋值转换](../c-language/assignment-conversions.md)中所述。 有关强制转换的其他约束可能来源于特定类型的实际大小或表示形式。 有关整型类型的实际大小的信息，请参阅[基本类型的存储](../c-language/storage-of-basic-types.md) 。 有关类型强制转换的详细信息，请参阅[类型强制转换](../c-language/type-cast-conversions.md)。  
  
## <a name="see-also"></a>另请参阅  
 [强制转换运算符：()](../cpp/cast-operator-parens.md)
