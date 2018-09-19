---
title: 编译器警告 （等级 1） C4167 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4167
dev_langs:
- C++
helpviewer_keywords:
- C4167
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c154a91c21bf0b35493bb8033e5453ef1c536267
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082178"
---
# <a name="compiler-warning-level-1-c4167"></a>编译器警告（等级 1）C4167

函数：仅可用作内部函数

**#pragma 函数** 尝试强制编译器对必须以内部形式使用的函数使用常规调用。 将忽略杂注。

若要避免此警告，请删除 **#pragma 函数**。

## <a name="example"></a>示例

```
// C4167.cpp
// compile with: /W1
#include <malloc.h>
#pragma function(_alloca )   // C4167: _alloca() is intrinsic only
int main(){}
```