---
title: 编译器错误 C2946
ms.date: 11/04/2016
f1_keywords:
- C2946
helpviewer_keywords:
- C2946
ms.assetid: c86dfbfc-7702-4f09-8a53-d205710e99c2
ms.openlocfilehash: 0f61d047fcd070f3deea662cd3bd193f8e133659
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459080"
---
# <a name="compiler-error-c2946"></a>编译器错误 C2946

显式实例化；“类”不是模板类专用化

不能显式实例化非模板化的类。

## <a name="example"></a>示例

下面的示例生成 C2946。

```
// C2946.cpp
class C {};
template C;  // C2946
int main() {}
```