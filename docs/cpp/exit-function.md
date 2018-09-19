---
title: exit 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71bff42495c4b6b7bf4016f0f08e7127c2b278ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075171"
---
# <a name="exit-function"></a>exit 函数

**退出**在标准包含文件中声明的函数\<stdlib.h >，将终止 C++ 程序。

作为参数提供的值**退出**返回给程序的返回代码或退出代码作为操作系统。 按照约定，返回代码为零表示该程序已成功完成。

> [!NOTE]
>  可以使用 EXIT_FAILURE 和 EXIT_SUCCESS 中定义的常量\<stdlib.h >，以指示成功或失败的程序。

发出**返回**从语句`main`函数相当于调用**退出**作为其参数的返回值的函数。

有关详细信息，请参阅[退出](../c-runtime-library/reference/exit-exit-exit.md)中*运行时库参考*。

## <a name="see-also"></a>请参阅

[程序终止](../cpp/program-termination.md)