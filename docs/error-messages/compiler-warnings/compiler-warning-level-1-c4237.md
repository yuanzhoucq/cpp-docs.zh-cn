---
title: 编译器警告 （等级 1） C4237 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4237
dev_langs:
- C++
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca72e4973c71655bc4a891570c6f686304d07eb0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092890"
---
# <a name="compiler-warning-level-1-c4237"></a>编译器警告（等级 1）C4237

keyword 关键字尚不受支持，但保留供将来使用

Visual c + + 编译器中未实现 c + + 规范中的关键字，但关键字不能作为用户定义的符号。

下面的示例生成 C4237:

```
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```