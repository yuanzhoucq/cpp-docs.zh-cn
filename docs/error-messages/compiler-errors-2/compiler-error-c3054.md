---
title: 编译器错误 C3054
ms.date: 11/04/2016
f1_keywords:
- C3054
helpviewer_keywords:
- C3054
ms.assetid: 6f4b7ac5-0d12-474b-b611-76ff26ee41ac
ms.openlocfilehash: 1dd6450d661700d9b2f7f94e625abd9ecc64ed08
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58772990"
---
# <a name="compiler-error-c3054"></a>编译器错误 C3054

当前在泛型类或函数中不支持“#pragma omp parallel”

有关详细信息，请参阅[泛型](../../extensions/generics-cpp-component-extensions.md)并[OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md)。

## <a name="example"></a>示例

下面的示例生成 C3054。

```
// C3054.cpp
// compile with: /openmp /clr /c
#include <omp.h>

ref struct MyBaseClass {
   // Delete the following 7 lines to resolve.
   generic <class ItemType>
   void Test(ItemType i) {   // C3054
      #pragma omp parallel num_threads(4)
      {
         int i = omp_get_thread_num();
      }
   }

   // OK
   void Test2() {
      #pragma omp parallel num_threads(4)
      {
         int i = omp_get_thread_num();
      }
   }
};
```