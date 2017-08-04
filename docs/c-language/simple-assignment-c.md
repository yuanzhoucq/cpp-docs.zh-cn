---
title: "简单赋值 (C) | Microsoft Docs"
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
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
caps.latest.revision: 7
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
ms.openlocfilehash: a60ec2f6f6466b579f917d02dabc24736c5a2e92
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="simple-assignment-c"></a>简单赋值 (C)
简单赋值运算符可将其右操作数赋给其左操作数。 右操作数的值将转换为赋值表达式的类型，并替换存储在左侧操作数指定的对象中的值。 用于赋值的转换规则适用（请参阅[赋值转换](../c-language/assignment-conversions.md)）。  
  
```  
double x;  
int y;  
  
x = y;  
```  
  
 在此示例中，将 `y` 的值转换为类型 double 并赋给 `x`。  
  
## <a name="see-also"></a>另请参阅  
 [C 赋值运算符](../c-language/c-assignment-operators.md)
