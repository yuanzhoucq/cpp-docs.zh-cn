---
title: 编译器错误 C2825
ms.date: 11/04/2016
f1_keywords:
- C2825
helpviewer_keywords:
- C2825
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
ms.openlocfilehash: 6a51901477958056356a96d71adde4241d60a2ac
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750580"
---
# <a name="compiler-error-c2825"></a>编译器错误 C2825

var：在后跟 "：：" 时必须为类或命名空间

试图形成限定名称的尝试失败。

例如，确保你的代码不包含函数名称以：：开头的函数声明。

## <a name="example"></a>示例

下面的示例生成 C2825：

```cpp
// C2825.cpp
typedef int i;
int main() {
   int* p = new int;
   p->i::i();   // C2825
   // try the following line instead
   // p->i::~i();
}
```
