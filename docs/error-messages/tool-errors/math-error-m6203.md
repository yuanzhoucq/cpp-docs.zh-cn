---
title: 数学错误 M6203
ms.date: 11/04/2016
f1_keywords:
- M6203
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
ms.openlocfilehash: 4433a024d461ee1bc43aa5fa82344190377243b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431130"
---
# <a name="math-error-m6203"></a>数学错误 M6203

function: _OVERFLOW 错误

给定的函数的结果已太大而无法表示。

此错误调用`_matherr`函数名称、 其参数与错误类型的函数。 您可以重写`_matherr`函数以自定义某些运行时浮点数学错误处理。