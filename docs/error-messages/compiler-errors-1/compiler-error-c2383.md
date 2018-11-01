---
title: 编译器错误 C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: 06d4c19208bd242169e1cd07a71e8a568f46f7b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466087"
---
# <a name="compiler-error-c2383"></a>编译器错误 C2383

'*符号*： 此符号上不允许使用默认自变量

C + + 编译器不允许函数指针的默认自变量。

此代码在 Visual Studio 2005 之前, 的版本中，Visual c + + 编译器已接受，但现在会导致错误。 有关适用于所有版本的 Visual c + + 的代码，现在将默认值分配给指针到函数参数。

## <a name="example"></a>示例

下面的示例生成 C2383，并显示了可能的解决方案：

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```