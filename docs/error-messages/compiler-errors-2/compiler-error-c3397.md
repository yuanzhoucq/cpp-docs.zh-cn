---
title: 编译器错误 C3397
ms.date: 11/04/2016
f1_keywords:
- C3397
helpviewer_keywords:
- C3397
ms.assetid: a8536e87-79c4-4ed7-bd96-42704d06391f
ms.openlocfilehash: 3f0b8207f9d6c74ac40510c5acff509f583f95f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434588"
---
# <a name="compiler-error-c3397"></a>编译器错误 C3397

默认参数中不允许进行聚合初始化

未正确声明数组。  请参阅[数组](../../windows/arrays-cpp-component-extensions.md)有关详细信息。

## <a name="example"></a>示例

下面的示例生成 C3397。

```
// C3397.cpp
// compile with: /clr
// /clr /c
void Func(array<int> ^p = gcnew array<int> { 1, 2, 3 });   // C3397
void Func2(array<int> ^p = gcnew array<int> (3));   // OK

int main() {
   array<int> ^p = gcnew array<int> { 1, 2, 3};   // OK
}
```