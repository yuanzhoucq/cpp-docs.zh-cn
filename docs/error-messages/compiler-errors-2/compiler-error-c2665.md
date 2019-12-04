---
title: 编译器错误 C2665
ms.date: 11/04/2016
f1_keywords:
- C2665
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
ms.openlocfilehash: 95ca5ea846f9cd45bdb1e9706ae377589d37a285
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756014"
---
# <a name="compiler-error-c2665"></a>编译器错误 C2665

"function"：非数字重载都不能从类型 "type" 转换参数数字2

重载函数的参数不能转换为所需的类型。  可能的解决方法：

- 提供一个转换运算符。

- 使用显式转换。

## <a name="example"></a>示例

下面的示例生成 C2665。

```cpp
// C2665.cpp
void func(short, char*){}
void func(char*, char*){}

int main() {
   func(0, 1);   // C2665
   func((short)0, (char*)1);   // OK
}
```
