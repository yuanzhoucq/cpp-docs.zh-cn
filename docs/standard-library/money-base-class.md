---
title: "money_base 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- locale/std::money_base
- money_base
dev_langs:
- C++
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
caps.latest.revision: 19
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 4af0f51a820fc0011285b6c5a690f496e8fd4afe
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="moneybase-class"></a>money_base 类
此类会描述常用于所有模板类 [moneypunct](../standard-library/moneypunct-class.md) 专用化的枚举和结构。  
  
## <a name="syntax"></a>语法  
```    
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};  
```  
## <a name="remarks"></a>备注  
 枚举 **part** 描述结构模式中数组字段元素中的可能值。 **part** 的值为：  
  
- **none** - 用于匹配零个或多个空格，或不生成任何内容。  
  
- **sign** - 用于匹配或生成正负号。  
  
- **space** - 用于匹配零个或多个空格，或生成空格。  
  
- **symbol** - 用于匹配或生成货币符号。  
  
- **value** - 用于匹配或生成货币值。  
  
## <a name="requirements"></a>要求  
 **标头：**\<locale>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




