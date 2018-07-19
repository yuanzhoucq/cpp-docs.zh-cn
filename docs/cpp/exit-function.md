---
title: exit 函数 |Microsoft Docs
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
ms.openlocfilehash: d08ac1375fa383543eaafb5b3ce49cd2bbfbc4da
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941075"
---
# <a name="exit-function"></a>exit 函数
`exit`函数，在标准包含文件中声明\<stdlib.h >，将终止 c + + 程序。  
  
 作为参数提供的值`exit`返回给程序的返回代码或退出代码作为操作系统。 按照约定，返回代码为零表示该程序已成功完成。  
  
> [!NOTE]
>  可以使用 EXIT_FAILURE 和 EXIT_SUCCESS 中定义的常量\<stdlib.h >，以指示成功或失败的程序。  
  
 发出**返回**从语句`main`函数相当于调用`exit`作为其参数的返回值的函数。  
  
 有关详细信息，请参阅[退出](../c-runtime-library/reference/exit-exit-exit.md)中*运行时库参考*。  
  
## <a name="see-also"></a>请参阅  
 [程序终止](../cpp/program-termination.md)