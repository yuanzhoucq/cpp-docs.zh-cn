---
title: 编译器错误 C3899 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3899
dev_langs:
- C++
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b154941051e1c6887e8e05756befd6a18c62ed72
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091773"
---
# <a name="compiler-error-c3899"></a>编译器错误 C3899

var: initonly 数据成员的左值使用不允许直接在类 class 中的并行区域

[Initonly (C + + CLI)](../../dotnet/initonly-cpp-cli.md)数据成员不能在该部分中的构造函数初始化[并行](../../parallel/openmp/reference/parallel.md)区域。  这样一来，就不再有效构造函数的一部分，这是因为编译器执行该代码，内部重定位。

若要解决，初始化 initonly 数据成员在构造函数中，但并行区域之外。

## <a name="example"></a>示例

下面的示例生成 C3899。

```
// C3899.cpp
// compile with: /clr /openmp
#include <omp.h>

public ref struct R {
   initonly int x;
   R() {
      x = omp_get_thread_num() + 1000;   // OK
      #pragma omp parallel num_threads(5)
      {
         // cannot assign to 'x' here
         x = omp_get_thread_num() + 1000;   // C3899
         System::Console::WriteLine("thread {0}", omp_get_thread_num());
      }
      x = omp_get_thread_num() + 1000;   // OK
   }
};

int main() {
   R^ r = gcnew R;
   System::Console::WriteLine(r->x);
}
```