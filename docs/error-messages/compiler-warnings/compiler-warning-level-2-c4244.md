---
title: 编译器警告 （等级 2） C4244 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4244
dev_langs:
- C++
helpviewer_keywords:
- C4244
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c6dd4b15fe3bda6468f8d5bebcf7cb0926ba69e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084791"
---
# <a name="compiler-warning-level-2-c4244"></a>编译器警告（等级 2）C4244

参数： 从 type1 到 type2，可能丢失数据的转换

一个浮点类型转换为整数类型。  可能发生了数据丢失。

如果收到 C4244，则应将程序更改为使用兼容类型，或向代码添加一些逻辑，以确保可能值的范围将始终与你使用的类型兼容。

C4244 也会激发在级别 3 和 4;请参阅[编译器警告 （等级 3 和 4） C4244](../../error-messages/compiler-warnings/compiler-warning-levels-3-and-4-c4244.md)有关详细信息。

## <a name="example"></a>示例

下面的示例生成 C4244：

```
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