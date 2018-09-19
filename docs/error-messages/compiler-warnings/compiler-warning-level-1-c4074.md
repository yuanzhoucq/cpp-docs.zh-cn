---
title: 编译器警告 （等级 1） C4074 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4074
dev_langs:
- C++
helpviewer_keywords:
- C4074
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb2fc41820165cee2b76a15abc97ab1e0cb79b81
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116632"
---
# <a name="compiler-warning-level-1-c4074"></a>编译器警告 （等级 1） C4074

初始值设定项放置在编译器保留的初始化区域

编译器初始化区域中，通过指定[#pragma init_seg](../../preprocessor/init-seg.md)，Microsoft 保留。 可能的 C 运行时库初始化之前执行此区域中的代码。

下面的示例生成 C4074:

```
// C4074.cpp
// compile with: /W1
#pragma init_seg( compiler )   // C4074

// try this line to resolve the warning
// #pragma init_seg(user)

int main() {
}
```