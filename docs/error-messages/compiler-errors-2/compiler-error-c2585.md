---
title: 编译器错误 C2585 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2585
dev_langs:
- C++
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ec7b1e9c1e5e7894740cc80f9c030fa1ee26ec0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028839"
---
# <a name="compiler-error-c2585"></a>编译器错误 C2585

显式转换成 type 不明确

类型转换可以生成多个结果。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 从基于多个继承的类或结构类型转换。 如果该类型不止一次继承相同的基类，转换函数或运算符必须使用范围解析 (`::`) 以指定的要在转换中使用的继承类。

1. 转换运算符和构造函数定义了进行相同的转换。