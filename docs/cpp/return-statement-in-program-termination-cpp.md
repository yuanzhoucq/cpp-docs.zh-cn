---
title: return 语句在程序终止 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61d09c1b3aaea799c227686436486efa48fc7857
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="return-statement-in-program-termination-c"></a>程序终止中的 return 语句 (C++)
发出`return`语句从**主要**功能上等效于调用**退出**函数。 请看下面的示例：  
  
```  
// return_statement.cpp  
#include <stdlib.h>  
int main()  
{  
    exit( 3 );  
    return 3;  
}  
```  
  
 **退出**和`return`前面的示例中的语句是功能相同。 但是，C++ 需要具有 `void` 之外的返回类型的函数返回一个值。 `return`语句可以返回一个介于**主要**。  
  
## <a name="see-also"></a>请参阅  
 [程序终止](../cpp/program-termination.md)