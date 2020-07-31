---
title: 编译器错误 C2433
ms.date: 11/04/2016
f1_keywords:
- C2433
helpviewer_keywords:
- C2433
ms.assetid: 7079fedd-6059-4125-82ef-ebe275f1f9d1
ms.openlocfilehash: f8cd8d5c165b796dff5260e84a505356f2a74941
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216214"
---
# <a name="compiler-error-c2433"></a>编译器错误 C2433

"identifier"：不允许在数据声明中使用 "修饰符"

**`friend`**、 **`virtual`** 和 **`inline`** 修饰符不能用于数据声明。

## <a name="example"></a>示例

下面的示例生成 C2433。

```cpp
// C2433.cpp
class C{};

int main() {
   inline C c;   // C2433
}
```
