---
title: "表达式语句 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
caps.latest.revision: 6
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: b48bf6d0dfd1c1ce29d1d116a77d3445bd5e1e30
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="expression-statement"></a>表达式语句
表达式语句导致计算表达式。 出于表达式语句的原因，不会发生控制或迭代的传输。  
  
 表达式语句的语法就是  
  
## <a name="syntax"></a>语法  
  
```  
[expression ] ;  
```  
  
## <a name="remarks"></a>备注  
 在执行下一个语句前，将计算表达式语句中的所有表达式并完成所有副作用。 最常用的表达式语句是赋值和函数调用。  由于表达式是可选的单独的分号被视为空表达式语句，称为[null](../cpp/null-statement.md)语句。  
  
## <a name="see-also"></a>另请参阅  
 [ 语句概述](../cpp/overview-of-cpp-statements.md)
