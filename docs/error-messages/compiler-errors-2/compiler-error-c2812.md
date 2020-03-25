---
title: 编译器错误 C2812
ms.date: 11/04/2016
f1_keywords:
- C2812
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
ms.openlocfilehash: cec92982646c64e6c5b669df328e4836d4f44df8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202087"
---
# <a name="compiler-error-c2812"></a>编译器错误 C2812

> 不支持将 \#导入/clr： pure 和/clr： safe

## <a name="remarks"></a>备注

**/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

不支持使用 **/clr： pure**和 **/clr： safe** [#import 指令](../../preprocessor/hash-import-directive-cpp.md)，因为 `#import` 需要使用本机编译器支持库。

## <a name="example"></a>示例

下面的示例生成 C2812。

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```
