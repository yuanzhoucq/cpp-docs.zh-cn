---
title: 编译器错误 C2474
ms.date: 11/04/2016
f1_keywords:
- C2474
helpviewer_keywords:
- C2474
ms.assetid: 64e6c61e-6e77-480e-bcf0-b30a2fc482ac
ms.openlocfilehash: ed2ba0d80ffcf2ef83abd551026bc6df4939ffbd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743726"
---
# <a name="compiler-error-c2474"></a>编译器错误 C2474

“keyword”: 缺少相邻的分号，可能是关键字或标识符。

编译器需要找到一个分号，因此不能确定你的意图。 增加一个分号以解决此问题。

## <a name="example"></a>示例

以下示例生成 C2474。

```cpp
// C2474.cpp
// compile with: /clr /c

ref class A {
   ref class B {}
   property int i;   // C2474 error
};

// OK
ref class B {
   ref class D {};
   property int i;
};

ref class E {
   ref class F {} property;
   int i;
};
```
