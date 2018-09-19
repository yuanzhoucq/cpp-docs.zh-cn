---
title: 编译器错误 C3012 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3012
dev_langs:
- C++
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99bdac5ffb75978479ae7ef420a48b3d1b2f8e64
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063666"
---
# <a name="compiler-error-c3012"></a>编译器错误 C3012

> '*内部函数*： 不允许并行区域内直接使用内部函数

一个[编译器内部函数](../../intrinsics/compiler-intrinsics.md)中不允许函数`omp parallel`区域。 若要解决此问题，将内部函数移出该区域，或使用非内部函数的等效信息替换它们。

## <a name="example"></a>示例

下面的示例生成 C3012，并演示一种方法修复此错误：

```cpp
// C3012.cpp
// compile with: /openmp
#ifdef __cplusplus
extern "C" {
#endif
void* _ReturnAddress();
#ifdef __cplusplus
}
#endif

int main()
{
   #pragma omp parallel
   {
      _ReturnAddress();   // C3012
   }
   _ReturnAddress();      // OK
}
```