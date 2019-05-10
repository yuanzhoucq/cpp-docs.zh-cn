---
title: 数学错误 M6203
ms.date: 11/04/2016
f1_keywords:
- M6203
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
ms.openlocfilehash: 4433a024d461ee1bc43aa5fa82344190377243b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400768"
---
# <a name="math-error-m6203"></a>数学错误 M6203

function: _OVERFLOW 错误

给定的函数的结果已太大而无法表示。

此错误调用`_matherr`函数名称、 其参数与错误类型的函数。 您可以重写`_matherr`函数以自定义某些运行时浮点数学错误处理。