---
title: 编译器警告（等级 1）C4160
ms.date: 08/27/2018
f1_keywords:
- C4160
helpviewer_keywords:
- C4160
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
ms.openlocfilehash: 988c1fcbe0826582dceaa527811c688711fd8906
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428036"
---
# <a name="compiler-warning-level-1-c4160"></a>编译器警告（等级 1）C4160

> #<a name="pragma-pop--did-not-find-previously-pushed-identifier-identifier"></a>杂注 (pop，...): 未找到先前入栈的标识符*标识符*

## <a name="remarks"></a>备注

源代码中的 pragma 语句试图弹出尚未入栈的标识符。 要避免此警告，请确保要弹出的标识符已正确入栈。

## <a name="example"></a>示例

下面的示例生成 C4160 并演示如何修复此错误：

```cpp
// C4160.cpp
// compile with: /W1
#pragma pack(push)

#pragma pack(pop, id)   // C4160
// use identifier when pushing to resolve the warning
// #pragma pack(push, id)

int main() {
}
```