---
title: 编译器错误 C2825
ms.date: 11/04/2016
f1_keywords:
- C2825
helpviewer_keywords:
- C2825
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
ms.openlocfilehash: 1e2f8e8cd38b90a698994743609892896ef0d1a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625870"
---
# <a name="compiler-error-c2825"></a>编译器错误 C2825

var： 必须是类或命名空间时后跟::

不成功尝试窗体的限定的名称。

例如，请确保你的代码不包含函数名称的开头的函数声明::。

## <a name="example"></a>示例

下面的示例生成 C2825:

```
// C2825.cpp
typedef int i;
int main() {
   int* p = new int;
   p->i::i();   // C2825
   // try the following line instead
   // p->i::~i();
}
```