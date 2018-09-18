---
title: 数学错误 M6108 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6108
dev_langs:
- C++
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1624a89b472733b4adb5563c8ba52e0b03dcaa2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048612"
---
# <a name="math-error-m6108"></a>数学错误 M6108

平方根

平方根操作中的操作数为负。

程序终止，退出代码为 136。

> [!NOTE]
>  `sqrt`中的 C 运行时库和 FORTRAN 内部函数的函数**SQRT**不会生成此错误。 C`sqrt`函数在执行该操作之前检查参数和返回一个错误值，如果操作数为负。 FORTRAN **SQRT**函数生成域错误[M6201](../../error-messages/tool-errors/math-error-m6201.md)而不是此错误。