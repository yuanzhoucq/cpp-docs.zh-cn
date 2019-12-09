---
title: 编译器错误 C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 515e2e151d27dd2eb84fc1dc71b9197b36b14cbb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745039"
---
# <a name="compiler-error-c2390"></a>编译器错误 C2390

"identifier"：不正确的存储类 "说明符"

存储类对于全局范围的标识符无效。 默认存储类用于代替无效类。

可能的解决方法：

- 如果该标识符是一个函数，则使用 `extern` 存储来声明它。

- 如果标识符是形参或局部变量，则使用自动存储来声明它。

- 如果标识符是全局变量，请在不使用存储类（自动存储）的情况下对其进行声明。

## <a name="example"></a>示例

- 下面的示例生成 C2390：

```cpp
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```
