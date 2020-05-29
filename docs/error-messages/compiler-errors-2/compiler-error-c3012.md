---
title: 编译器错误 C3012
ms.date: 11/04/2016
f1_keywords:
- C3012
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
ms.openlocfilehash: 69f0544815804e9827631be81bf9735a95bd1a22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176697"
---
# <a name="compiler-error-c3012"></a>编译器错误 C3012

> "*固有*"：并行区域内不允许直接使用内部函数

一个[编译器内部函数](../../intrinsics/compiler-intrinsics.md)中不允许函数`omp parallel`区域。 若要解决此问题，请将内部函数移出区域，或将其替换为非内部等效项。

## <a name="example"></a>示例

下面的示例生成 C3012，并显示修复此问题的一种方法：

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
