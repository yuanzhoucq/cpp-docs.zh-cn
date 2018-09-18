---
title: 数学错误 M6203 |Microsoft Docs
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
ms.openlocfilehash: d8474c91802b4756207676c466fdd28d66d911b3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022664"
---
# <a name="math-error-m6203"></a>数学错误 M6203

function: _OVERFLOW 错误

给定的函数的结果已太大而无法表示。

此错误调用`_matherr`函数名称、 其参数与错误类型的函数。 您可以重写`_matherr`函数以自定义某些运行时浮点数学错误处理。