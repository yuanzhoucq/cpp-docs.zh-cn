---
title: 编译器错误 C2714
ms.date: 07/22/2020
f1_keywords:
- C2714
helpviewer_keywords:
- C2714
ms.assetid: 401a5a42-660c-4bad-9d63-1a2d092bc489
ms.openlocfilehash: d3f733f065af5b3217dc19d46b46e504d39151f4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225405"
---
# <a name="compiler-error-c2714"></a>编译器错误 C2714

> `alignof(void)`不允许

传递给运算符的值无效。

## <a name="remarks"></a>备注

有关详细信息，请参阅[ `alignof` 运算符](../../cpp/alignof-operator.md)。

## <a name="example"></a>示例

下面的示例生成 C2714。

```cpp
// C2714.cpp
int main() {
   return alignof(void);   // C2714
   return alignof(char);   // OK
}
```
