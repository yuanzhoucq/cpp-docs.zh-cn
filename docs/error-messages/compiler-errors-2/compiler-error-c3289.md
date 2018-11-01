---
title: 编译器错误 C3289
ms.date: 11/04/2016
f1_keywords:
- C3289
helpviewer_keywords:
- C3289
ms.assetid: 3c1c623b-7fcf-43ab-a89a-8722532a8d29
ms.openlocfilehash: 0ebb56023694b1713bfe88379d07fc621da4d43f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622646"
---
# <a name="compiler-error-c3289"></a>编译器错误 C3289

“property”：无法索引 trivial 属性

未正确声明属性。 必须为索引的属性定义访问器。 有关更多信息，请参见 [property](../../windows/property-cpp-component-extensions.md) 。

## <a name="example"></a>示例

下面的示例生成 C3289。

```
// C3289.cpp
// compile with: /clr
public ref struct C {
   // user-defined simple indexer
   property int indexer1[int];   // C3289

   // user-defined indexer
   property int indexer2[int] {
      int get(int i) { return 0; }
      void set(int i, int j) {}
   }
};

int main() {
   C ^ MyC = gcnew C();
   MyC->indexer2[0] = 1;
}
```