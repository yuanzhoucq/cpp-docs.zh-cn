---
title: 编译器错误 C2774
ms.date: 11/04/2016
f1_keywords:
- C2774
helpviewer_keywords:
- C2774
ms.assetid: 10f428c6-7f49-489a-92ba-6ef978b7caaf
ms.openlocfilehash: 6197e3da81a9f059c90d15608a939ad4887e526d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586883"
---
# <a name="compiler-error-c2774"></a>编译器错误 C2774

identifier： 没有 put 方法是与此属性相关联

使用声明数据成员[属性](../../cpp/property-cpp.md)没有`put`函数，但表达式尝试将其值设置。

下面的示例生成 C2774:

```
// C2774.cpp
struct A {
   __declspec(property(get=GetProp)) int prop;
   int GetProp(void);

   __declspec(property(get=GetProp2, put=PutProp2)) int prop2;
   int GetProp2(void);
   void PutProp2(int);
};

int main() {
   A* pa = new A;
   int val = 0;
   pa->prop = val;   // C2774
   pa->prop++;   // C2774
}
```