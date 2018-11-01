---
title: 编译器错误 C2665
ms.date: 11/04/2016
f1_keywords:
- C2665
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
ms.openlocfilehash: 63817c4181edb942f43f41c24fb10278d14f397e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474719"
---
# <a name="compiler-error-c2665"></a>编译器错误 C2665

function: number1 重载没有可以从类型 type 转换参数数字 2

重载函数的参数不能转换为所需的类型。  可能的解决方法：

- 提供转换运算符。

- 使用显式转换。

## <a name="example"></a>示例

下面的示例生成 C2665。

```
// C2665.cpp
void func(short, char*){}
void func(char*, char*){}

int main() {
   func(0, 1);   // C2665
   func((short)0, (char*)1);   // OK
}
```