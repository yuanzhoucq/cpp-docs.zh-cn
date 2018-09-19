---
title: 编译器错误 C2212 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2212
dev_langs:
- C++
helpviewer_keywords:
- C2212
ms.assetid: 3fdab304-272c-4d07-bfd4-fad75170e536
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 773dff4c731830d300c97f1960b24923d2b7d67f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089874"
---
# <a name="compiler-error-c2212"></a>编译器错误 C2212

identifier: __based 不可用于指向函数的指针

不能声明为指向函数的指针`__based`。 如果需要基于代码的数据，请使用`__declspec`关键字或`data_seg`杂注。