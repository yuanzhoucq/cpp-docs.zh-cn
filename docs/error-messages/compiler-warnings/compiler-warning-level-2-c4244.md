---
title: 编译器警告（等级 2）C4244
ms.date: 11/04/2016
f1_keywords:
- C4244
helpviewer_keywords:
- C4244
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
ms.openlocfilehash: a07adf37314a11cceb72d6675a66d82f7554bbb6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162057"
---
# <a name="compiler-warning-level-2-c4244"></a>编译器警告（等级 2）C4244

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
