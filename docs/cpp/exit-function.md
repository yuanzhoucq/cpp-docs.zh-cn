---
title: exit 函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5767f6b08b4adcd3d1a8d367c6286a746eeecec3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="exit-function"></a>exit 函数
**退出**在标准包含文件中声明的函数\<stdlib.h >，将终止 C++ 程序。  
  
 提供作为的自变量的值**退出**返回到操作系统作为程序的返回代码或退出代码。 按照约定，返回代码为零表示该程序已成功完成。  
  
> [!NOTE]
>  你可以使用常量`EXIT_FAILURE`和`EXIT_SUCCESS`在中定义\<stdlib.h >，以指示成功或失败的程序。  
  
 发出`return`语句从**主要**函数等效于调用**退出**作为其自变量返回值的函数。  
  
 有关详细信息，请参阅[退出](../c-runtime-library/reference/exit-exit-exit.md)中*运行时库参考*。  
  
## <a name="see-also"></a>请参阅  
 [程序终止](../cpp/program-termination.md)