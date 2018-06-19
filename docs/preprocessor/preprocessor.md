---
title: 预处理器 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3bb5a9740bab3f69ff66a51cd58e6e1378e178f0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33848445"
---
# <a name="preprocessor"></a>预处理器
预处理器是将源文件的文本作为翻译的第一阶段操作的文本处理器。 预处理器不会分析源文本，但会为了查找宏调用而将源文本细分为标记。 尽管编译器一般会在其第一个传递中调用预处理器，但还是可以为了在不进行编译的情况下处理文本而单独调用预处理器。  
  
 预处理器的参考材料包括下列部分：  
  
-   [预处理器指令](../preprocessor/preprocessor-directives.md)  
  
-   [预处理器运算符](../preprocessor/preprocessor-operators.md)  
  
-   [预定义的宏](../preprocessor/predefined-macros.md)  
  
-   [杂注](../preprocessor/pragma-directives-and-the-pragma-keyword.md)  
  
 **Microsoft 专用**  
  
 你可以在源代码预处理后获取列表使用[/E](../build/reference/e-preprocess-to-stdout.md)或[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)编译器选项。 两个选项均调用预处理器并将生成的文本输出到标准输出设备（大多数情况下是控制台）。 两个选项之间的差异在于 /E 包含 `#line` 指令，而 /EP 去除了这些指令。  
  
 **结束 Microsoft 专用**  
  
##  <a name="_predir_special_terminology"></a> 特殊术语  
 在预处理器文档中，术语“自变量”指传递给函数的实体。 在某些情况下，它由“actual”和“formal”修改，二者分别描述函数调用中指定的参数表达式和函数定义中指定的参数声明。  
  
 术语“变量”指简单的 C 类型数据对象。 术语“对象”指 C++ 对象和变量；它是一个非独占术语。  
  
## <a name="see-also"></a>请参阅  
 [C/c + + 预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)   
 [转换阶段](../preprocessor/phases-of-translation.md)