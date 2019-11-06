---
title: 编译器警告（等级1） C4028
ms.date: 11/04/2016
f1_keywords:
- C4028
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
ms.openlocfilehash: 19bfd2659ee9017d3a304dee2d647da091515876
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623854"
---
# <a name="compiler-warning-level-1-c4028"></a>编译器警告（等级1） C4028

形参 "number" 与声明不同

形参的类型与声明中的相应参数不一致。 使用原始声明中的类型。

此警告仅对 C 源代码有效。

## <a name="example"></a>示例

下面的示例生成 C4028。

```c
// C4028.c
// compile with: /W1 /Za
void f(int , ...);
void f(int i, int j) {}   // C4028

void g(int , int);
void g(int i, int j) {}   // OK

int main() {}
```