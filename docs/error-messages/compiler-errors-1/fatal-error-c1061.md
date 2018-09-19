---
title: 错误 C1061 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1061
dev_langs:
- C++
helpviewer_keywords:
- C1061
ms.assetid: 9366c0bc-96e0-4967-aa7d-4ebf098de806
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21ca27534aa23d0d81ec7fb191c336b35b18391a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083270"
---
# <a name="fatal-error-c1061"></a>错误 C1061

编译器限制 : 块嵌套太深

代码块的嵌套超过 128 嵌套级的限制。 在 32 位和 64 位工具集中，这对于 C 和 C++ 的编译器都是硬性限制。 创建范围或块的任何内容都能增加嵌套级别的计数。 例如，命名空间、使用指令、预处理器扩展、模板扩展、异常处理、循环构造和 else-if 子句都能增加编译器看到的嵌套级别。

若要修复此错误，则必须重构代码。 在任何情况下，深度嵌套的代码都是难以理解和解释的。 重构代码以减少嵌套级别可提高代码质量和简化维护。 将深度嵌套代码分解为从原始上下文调用的函数。 限制块内的循环或链接的 else-if 的子句的数量。