---
title: 编译器错误 C2691
ms.date: 11/04/2016
f1_keywords:
- C2691
helpviewer_keywords:
- C2691
ms.assetid: 6925f8f3-ea60-4909-91e6-b781492c645d
ms.openlocfilehash: 34287b785532394d33e94e37e7a6a9955d935f14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501993"
---
# <a name="compiler-error-c2691"></a>编译器错误 C2691

数据类型： 托管或 WinRTarray 不能具有此元素类型

托管数组元素或 WinRT 数组元素的类型可以是值类型或引用类型。

以下示例生成 C2691：

```
// C2691a.cpp
// compile with: /clr
class A {};

int main() {
   array<A>^ a1 = gcnew array<A>(20);   // C2691
   array<int>^ a2 = gcnew array<int>(20);   // value type OK
}
```
