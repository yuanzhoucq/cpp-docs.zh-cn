---
title: 编译器错误 C2433
ms.date: 11/04/2016
f1_keywords:
- C2433
helpviewer_keywords:
- C2433
ms.assetid: 7079fedd-6059-4125-82ef-ebe275f1f9d1
ms.openlocfilehash: 9edb30e574e212bd30fd60dd3ce5aaddc650dc11
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744428"
---
# <a name="compiler-error-c2433"></a>编译器错误 C2433

"identifier"：不允许在数据声明中使用 "修饰符"

`friend`、`virtual`和 `inline` 修饰符不能用于数据声明。

## <a name="example"></a>示例

下面的示例生成 C2433。

```cpp
// C2433.cpp
class C{};

int main() {
   inline C c;   // C2433
}
```
