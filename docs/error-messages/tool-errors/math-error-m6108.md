---
title: 数学错误 M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: 68e6ae823613d87eb01c443b564b46746259cd7b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173720"
---
# <a name="math-error-m6108"></a>数学错误 M6108

平方根

平方根运算中的操作数为负数。

程序终止，退出代码为136。

> [!NOTE]
>  C 运行时库中的 `sqrt` 函数和 FORTRAN 内部函数**SQRT**不会生成此错误。 在执行操作之前，C `sqrt` 函数将检查参数，并在操作数为负数时返回错误值。 FORTRAN **SQRT**函数生成域错误[M6201](../../error-messages/tool-errors/math-error-m6201.md) ，而不是此错误。
