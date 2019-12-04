---
title: 编译器错误 C2153
ms.date: 11/04/2016
f1_keywords:
- C2153
helpviewer_keywords:
- C2153
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
ms.openlocfilehash: 1f03b196b7ddaae80dac1941cdde5be16acace5f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748679"
---
# <a name="compiler-error-c2153"></a>编译器错误 C2153

十六进制常量必须至少有一个十六进制数字

十六进制常量0x、0X 和 \x 无效。 至少一个十六进制数字必须在 x 或 X 之后。

下面的示例生成 C2153：

```cpp
// C2153.cpp
int main() {
   int a= 0x;    // C2153
   int b= 0xA;   // OK
}
```
