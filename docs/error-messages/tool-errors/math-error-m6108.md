---
title: 数学错误 M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: c6bd403437ee5e55eaf4add288995d0e4aa76c3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361976"
---
# <a name="math-error-m6108"></a>数学错误 M6108

平方根

平方根操作中的操作数为负数。

程序终止与退出代码 136。

> [!NOTE]
> C`sqrt`运行时库中的函数和 FORTRAN 内部函数**SQRT**不会生成此错误。 在执行操作`sqrt`之前，C 函数会检查参数，如果操作数为负数，则返回错误值。 FORTRAN **SQRT**函数生成域错误[M6201](../../error-messages/tool-errors/math-error-m6201.md)而不是此错误。
