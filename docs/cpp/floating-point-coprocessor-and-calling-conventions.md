---
title: 浮点协处理器和调用约定 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46cf9c937453894ed37ad434ad94609d0744be24
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>浮点协处理器和调用约定
如果要为浮点例程点协处理器编写程序集，你必须保留浮点控制字和清理协处理器堆栈，除非您在返回**float**或**double**值 （您的函数应返回 ST(0)) 中。  
  
## <a name="see-also"></a>请参阅  
 [调用约定](../cpp/calling-conventions.md)