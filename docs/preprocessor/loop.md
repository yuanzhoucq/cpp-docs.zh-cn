---
title: 循环 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- loop_CPP
- vc-pragma.loop
dev_langs:
- C++
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9af0e01cd29d6fe89e0cd0d6c5ff4a7030909799
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846527"
---
# <a name="loop"></a>循环
控制自动并行化如何考虑循环代码和/或从自动向量化进行的考虑中排除循环。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma loop( hint_parallel(n) )  
```  
  
```  
  
#pragma loop( no_vector )  
```  
  
```  
  
#pragma loop( ivdep )  
```  
  
#### <a name="parameters"></a>参数  
 `hint_parallel(` `n` `)`  
 对编译器应跨 `n` 个线程并行化此循环的提示（其中 `n` 为正整数文本或零）。 如果 `n` 为零，则在运行时使用最大数量的线程。 这是对编译器的提示而不是命令，并且并不保证会并行化循环。 如果循环具有数据依赖项或结构问题，例如，循环存储到在循环体外使用的标量，则将不会并行化循环。  
  
 编译器将忽略此选项，除非[/Qpar](../build/reference/qpar-auto-parallelizer.md)指定编译器开关。  
  
 `no_vector`  
 默认情况下，自动向量化处于启用状态，并且将尝试向量化其计算为从中受益的所有循环。 请指定此杂注以对杂注后面的循环禁用自动向量化。  
  
 `ivdep`  
 对编译器忽略此循环的向量依赖项的提示。 请将其与 `hint_parallel` 结合使用。  
  
## <a name="remarks"></a>备注  
 若要使用 `loop` 杂注，请将其放在紧靠循环定义之前，而不是放在循环定义中。 杂注对它后面的循环的范围有效。 您可按任意顺序将多个杂注应用于一个循环，但必须在单独的杂注语句中声明每个杂注。  
  
## <a name="see-also"></a>请参阅  
 [自动并行化和自动向量化](../parallel/auto-parallelization-and-auto-vectorization.md)   
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)