---
title: 编译器警告 （等级 1） C4103 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4103
dev_langs:
- C++
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1942acc2d9c5c274806e06127f9f98d4bfcb5077
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085532"
---
# <a name="compiler-warning-level-1-c4103"></a>编译器警告 （等级 1） C4103

filename： 包含标头后, 更改了对齐方式可能是由于缺少 #pragma pack （pop）

装箱会影响类的布局和常见的是，如果在标头文件中打包的更改，可能会有问题。

使用 #pragma [pack](../../preprocessor/pack.md)(pop) 标头文件，若要解决此警告在退出之前。

下面的示例生成 C4103:

```
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

然后，

```
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```