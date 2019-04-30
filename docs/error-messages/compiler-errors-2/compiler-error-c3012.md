---
title: 编译器错误 C3012
ms.date: 11/04/2016
f1_keywords:
- C3012
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
ms.openlocfilehash: 9fe0ac7d3637cad3a5571c4631345dac1a0021bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386728"
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