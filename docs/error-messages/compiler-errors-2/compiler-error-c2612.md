---
title: 编译器错误 C2612
ms.date: 11/04/2016
f1_keywords:
- C2612
helpviewer_keywords:
- C2612
ms.assetid: 6faacfd6-4455-41a2-808e-0f6799f84d6d
ms.openlocfilehash: 630e5b1cc6e99ffda28f50c09bccbbc2fea07172
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737694"
---
# <a name="compiler-error-c2612"></a>编译器错误 C2612

基/成员初始值设定项列表中的尾随 "char" 非法

初始值设定项列表中的最后一个基或成员后会出现一个字符。

下面的示例生成 C2612：

```cpp
// C2612.cpp
class A {
public:
   int i;
   A( int ia ) : i( ia ) + {};   // C2612
};
```
