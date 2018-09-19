---
title: 编译器错误 C3550 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3550
dev_langs:
- C++
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08c22d7e371fda7a229b541f78d4385f2943ee54
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047780"
---
# <a name="compiler-error-c3550"></a>编译器错误 C3550

此上下文只允许纯“decltype(auto)”

如果 `decltype(auto)` 用作函数的返回类型的占位符，则它必须被其自身使用。 它无法用作指针声明 (`decltype(auto*)`)、引用声明 (`decltype(auto&)`) 或其他此类限定的一部分。

## <a name="see-also"></a>请参阅

[auto](../../cpp/auto-cpp.md)