---
title: 浮点协处理器和调用约定 |Microsoft Docs
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
ms.openlocfilehash: 66ccd54c4abb1d8d9761d5ded88beba76bfae043
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401349"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>浮点协处理器和调用约定
如果你正在编写程序集的浮点例程点协处理器，则必须保留浮点控制字和清理协处理器堆栈，除非您在返回**float**或**double**值 （其中 st(0 应返回您的函数。  
  
## <a name="see-also"></a>请参阅  
 [调用约定](../cpp/calling-conventions.md)