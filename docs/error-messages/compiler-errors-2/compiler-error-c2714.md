---
title: 编译器错误 C2714
ms.date: 11/04/2016
f1_keywords:
- C2714
helpviewer_keywords:
- C2714
ms.assetid: 401a5a42-660c-4bad-9d63-1a2d092bc489
ms.openlocfilehash: feba363a7cd15d92bf850e8cba457ff310d15490
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556359"
---
# <a name="compiler-error-c2714"></a>编译器错误 C2714

不允许 __alignof(void)

对运算符传递了无效值。

请参阅[__alignof 运算符](../../cpp/alignof-operator.md)有关详细信息。

## <a name="example"></a>示例

下面的示例生成 C2714。

```
// C2714.cpp
int main() {
   return __alignof(void);   // C2714
   return __alignof(char);   // OK
}
```