---
title: 编译器警告（等级2） C4244
ms.date: 11/04/2016
f1_keywords:
- C4244
helpviewer_keywords:
- C4244
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
ms.openlocfilehash: 43d8a992801d556ce85577f5f9da1bec584cb173
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052130"
---
# <a name="compiler-warning-level-2-c4244"></a>编译器警告（等级2） C4244

"argument"：从 "type1" 转换到 "type2"，可能丢失数据

浮点类型已转换为整数类型。  可能发生了数据丢失。

如果收到 C4244，则应将程序更改为使用兼容类型，或向代码添加一些逻辑，以确保可能值的范围将始终与你使用的类型兼容。

C4244 也可以在第3级和第4级激发;有关详细信息，请参阅[编译器警告（等级3和4） C4244](../../error-messages/compiler-warnings/compiler-warning-levels-3-and-4-c4244.md) 。

## <a name="example"></a>示例

下面的示例生成 C4244：

```cpp
// C4244_level2.cpp
// compile with: /W2

int f(int x){ return 0; }
int main() {
   double x = 10.1;
   int i = 10;
   return (f(x));   // C4244
   // try the following line instead
   // return (f(i));
}
```