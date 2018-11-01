---
title: 编译器错误 C3176
ms.date: 11/04/2016
f1_keywords:
- C3176
helpviewer_keywords:
- C3176
ms.assetid: 6cc8d602-8e15-47a7-b1b5-e93e5d50e271
ms.openlocfilehash: 8c92a49499a18c12807f97cb97b24cc3beaf700b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474420"
---
# <a name="compiler-error-c3176"></a>编译器错误 C3176

type： 不能声明局部值类型

只能在全局范围内的值类型作为声明一个类。

## <a name="example"></a>示例

下面的示例生成 C3176。

```
// C3176.cpp
// compile with: /clr
int main () {
   enum class C {};   // C3176
}
```