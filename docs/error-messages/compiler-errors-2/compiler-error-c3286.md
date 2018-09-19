---
title: 编译器错误 C3286 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3286
dev_langs:
- C++
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ea2a6dcccd6de6d4fc3081106123f4ab37f71a2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052908"
---
# <a name="compiler-error-c3286"></a>编译器错误 C3286

> '*说明符*： 迭代变量不能包含任何存储类说明符

存储类不能对指定的迭代变量。 有关详细信息，请参阅[存储类 （c + +）](../../cpp/storage-classes-cpp.md)并[对于每个，在](../../dotnet/for-each-in.md)。

## <a name="example"></a>示例

下面的示例生成 c3286:，并还显示了正确的使用。

```cpp
// C3286.cpp
// compile with: /clr
int main() {
   array<int> ^p = { 1, 2, 3 };
   for each (static int i in p) {}   // C3286
   for each (int j in p) {}   // OK
}
```