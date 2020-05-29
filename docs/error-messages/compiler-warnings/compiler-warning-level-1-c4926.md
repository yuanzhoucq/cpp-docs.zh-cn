---
title: 编译器警告（等级 1）C4926
ms.date: 11/04/2016
f1_keywords:
- C4926
helpviewer_keywords:
- C4926
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
ms.openlocfilehash: 090b0b005c9374ad409ee580b3c726ce60db258f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174617"
---
# <a name="compiler-warning-level-1-c4926"></a>编译器警告（等级 1）C4926

“identifier”：已定义符号：忽略特性

已找到前向声明，但已存在具有相同名称的特性化的构造。 忽略前向声明的特性。

下面的示例生成 C4926：

```cpp
// C4926.cpp
// compile with: /W1
[module(name="MyLib")];

[coclass]
struct a {
};

[coclass]
struct a;   // C4926

int main() {
}
```
