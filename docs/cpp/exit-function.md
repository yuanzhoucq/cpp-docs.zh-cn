---
title: "exit 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
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
ms.openlocfilehash: 240636bf7b6f10421c5d4ebd202a5fb3473a819d
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="exit-function"></a>exit 函数
**退出**在标准包含文件 STDLIB 中声明的函数。H、 终止 c + + 程序。  
  
 提供作为的自变量的值**退出**返回到操作系统作为程序的返回代码或退出代码。 按照约定，返回代码为零表示该程序已成功完成。  
  
> [!NOTE]
>  可以使用在 STDLIB.H 中定义的常量 `EXIT_FAILURE` 和 `EXIT_SUCCESS` 来指示程序是成功还是失败。  
  
 发出`return`语句从**主要**函数等效于调用**退出**作为其自变量返回值的函数。  
  
 有关详细信息，请参阅[退出](../c-runtime-library/reference/exit-exit-exit.md)中*运行时库参考*。  
  
## <a name="see-also"></a>另请参阅  
 [程序终止](../cpp/program-termination.md)
