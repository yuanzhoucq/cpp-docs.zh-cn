---
title: 编译器警告（等级3） C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: ebebfe9994be3dd136e3924cb2aea60c0c901926
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051637"
---
# <a name="compiler-warning-level-3-c4334"></a>编译器警告（等级3） C4334

"operator"：32位移位的结果被隐式转换为64位（是否打算进行64位移位？）

32位移位的结果被隐式转换为64位，并且编译器怀疑需要64位移位。  若要解决此警告，请使用64位 shift，或将移位结果显式转换为64位。

## <a name="example"></a>示例

下面的示例生成 C4334。

```cpp
// C4334.cpp
// compile with: /W3 /c
void SetBit(unsigned __int64 *p, int i) {
   *p |= (1 << i);   // C4334
   *p |= (1i64 << i);   // OK
}
```