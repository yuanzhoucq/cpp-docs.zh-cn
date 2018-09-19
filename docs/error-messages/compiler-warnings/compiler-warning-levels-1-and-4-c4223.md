---
title: 编译器警告 （等级 1 和 4） C4223 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4223
dev_langs:
- C++
helpviewer_keywords:
- C4223
ms.assetid: 6fc44336-0250-4432-928b-fc5dbe7b7c1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a04ccf80bac123a3d2c6f28a063c274fe40a7e58
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075417"
---
# <a name="compiler-warning-levels-1-and-4-c4223"></a>编译器警告（等级 1 和等级 4）C4223

使用了非标准扩展： 不是 lvalue 的数组转换为指针

在标准 C 中，不能将不是 lvalue 的数组转换为指针。 与默认 Microsoft 扩展 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))，则可以。