---
title: 强制转换运算符 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cast operators
- type casts, operators
- operators [C++], cast
- type conversion, cast operators
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fe1001c4a35e40b10abefd60faedcbcb6398445
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381767"
---
# <a name="cast-operators"></a>强制转换运算符
在特定情况下，类型强制转换提供了用于显式转换对象类型的方法。  
  
## <a name="syntax"></a>语法  
 *cast-expression*：  
 *unary-expression*  
  
 **(**  *type-name*  **)**  *cast-expression*  
  
 在进行类型强制转换后，编译器将 cast-expression 视为类型 type-name。 强制转换可用于在任意标量类型的对象与任何其他标量类型之间进行来回转换。 显式类型强制转换受到确定隐式转换效果的相同规则的约束，如[赋值转换](../c-language/assignment-conversions.md)中所述。 有关强制转换的其他约束可能来源于特定类型的实际大小或表示形式。 有关整型类型的实际大小的信息，请参阅[基本类型的存储](../c-language/storage-of-basic-types.md) 。 有关类型强制转换的详细信息，请参阅[类型强制转换](../c-language/type-cast-conversions.md)。  
  
## <a name="see-also"></a>请参阅  
 [强制转换运算符：()](../cpp/cast-operator-parens.md)