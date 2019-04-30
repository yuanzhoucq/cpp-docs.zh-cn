---
title: 编译器警告 （等级 1） C4028
ms.date: 11/04/2016
f1_keywords:
- C4028
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
ms.openlocfilehash: bfe54fc40b4d6927a1d75f529ec9b619f9b29226
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397362"
---
# <a name="compiler-warning-level-1-c4028"></a>编译器警告 （等级 1） C4028

形式参数 number 与声明不同

在声明中的对应参数不一致的形式参数的类型。 使用中的原始声明的类型。

此警告才有效的 C 源代码。

## <a name="example"></a>示例

下面的示例生成 C4028。

```
// C4028.c
// compile with: /W1 /Za
void f(int , ...);
void f(int i, int j) {}   // C4028

void g(int , int);
void g(int i, int j) {}   // OK

int main() {}
```