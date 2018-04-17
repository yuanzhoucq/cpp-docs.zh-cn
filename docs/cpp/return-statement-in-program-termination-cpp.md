---
title: "return 语句在程序终止 （C++） |Microsoft 文档"
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a9e97c0ee52094cd3f0ccbb36c0da8b3b04c630
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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