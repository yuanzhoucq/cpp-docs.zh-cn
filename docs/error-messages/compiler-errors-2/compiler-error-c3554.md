---
title: 编译器错误 C3554
ms.date: 11/04/2016
f1_keywords:
- C3554
helpviewer_keywords:
- C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
ms.openlocfilehash: 8bc9c465d16aea4714916fa6aa2942eb81c19015
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582294"
---
# <a name="compiler-error-c3554"></a>编译器错误 C3554

“decltype”不能与任何其他类型说明符组合

不可用任何类型说明符来限定 `decltype()` 关键字。 例如，下述代码片段产生错误 C3554。

```
int x;
unsigned decltype(x); // C3554
```