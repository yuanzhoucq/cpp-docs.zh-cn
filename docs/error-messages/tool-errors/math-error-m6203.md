---
title: 数学错误 M6203 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6203
dev_langs:
- C++
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7660284f9e5e69b53f3289eaa1aa424944bbecb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319307"
---
# <a name="math-error-m6203"></a>数学错误 M6203
function: _OVERFLOW 错误  
  
 太大而无法表示给定的函数的结果。  
  
 此错误调用`_matherr`函数名称、 其参数与错误类型的函数。 您可以重新编写`_matherr`函数以自定义的某些运行时浮点数学错误处理。