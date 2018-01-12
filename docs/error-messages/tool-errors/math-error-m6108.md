---
title: "数学错误 M6108 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: M6108
dev_langs: C++
helpviewer_keywords: M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c6db123d9cb96274848a3edd9f845f86f413d8e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-m6108"></a>数学错误 M6108
平方根  
  
 平方根运算中的操作数为负。  
  
 程序终止，退出代码 136。  
  
> [!NOTE]
>  `sqrt` C 运行时库和 FORTRAN 内部函数中的函数**SQRT**也不会生成此错误。 C`sqrt`函数在执行该操作之前检查自变量并返回一个错误值，如果操作数为负。 FORTRAN **SQRT**函数生成域错误[M6201](../../error-messages/tool-errors/math-error-m6201.md)而不是此错误。