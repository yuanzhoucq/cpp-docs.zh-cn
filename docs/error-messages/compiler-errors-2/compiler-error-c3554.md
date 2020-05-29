---
title: 编译器错误 C3554
ms.date: 11/04/2016
f1_keywords:
- C3554
helpviewer_keywords:
- C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
ms.openlocfilehash: ecdb90e845714e046ed21cf5a200ef4548487df6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200598"
---
# <a name="compiler-error-c3554"></a>编译器错误 C3554

“decltype”不能与任何其他类型说明符组合

不可用任何类型说明符来限定 `decltype()` 关键字。 例如，下述代码片段产生错误 C3554。

```
int x;
unsigned decltype(x); // C3554
```
