---
title: 表达式计算器错误 CXX0021 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0021
dev_langs:
- C++
helpviewer_keywords:
- CXX0021
- CAN0021
ms.assetid: d6c0c35a-16c2-42c0-a7d2-e910350a47f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ef765286d022b26aeed0ca98c9f43f94f5d17f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025771"
---
# <a name="expression-evaluator-error-cxx0021"></a>表达式计算器错误 CXX0021

结构或联合用作标量

在表达式中，使用结构或联合，但未指定任何元素。

当操作结构或联合变量，变量的名称可能会单独出现，无字段限定符。 如果在表达式中使用的结构或联合，它必须与所需的特定元素进行限定。

指定其值将在表达式中使用的元素。

此错误是与 CAN0021 相同。