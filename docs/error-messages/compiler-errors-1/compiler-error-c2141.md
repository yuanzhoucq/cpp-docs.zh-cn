---
title: 编译器错误 C2141
ms.date: 11/04/2016
f1_keywords:
- C2141
helpviewer_keywords:
- C2141
ms.assetid: 10cf770f-0500-4220-ac90-a863b7ea5fe6
ms.openlocfilehash: 89395fa3419d79fa4dec3fecf9acfc681590d825
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593981"
---
# <a name="compiler-error-c2141"></a>编译器错误 C2141

数组大小溢出

数组超过 2 GB 的限制。 减少数组的大小。

## <a name="example"></a>示例

下面的示例生成 C2141。

```
// C2141.cpp
// processor: IPF
class A {
   short m_n;
};

int main()
{
   A* pA = (A*)(-1);
   pA = new A[0x8000000000000001];   // C2141

   A* pA2 = (A*)(-1);
   pA2 = new A[0x80000000000000F];   // OK
}
```