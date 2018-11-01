---
title: 编译器错误 C2812
ms.date: 11/04/2016
f1_keywords:
- C2812
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
ms.openlocfilehash: 88b071f38cf41db9c929d25ffd526b3f2b7ca468
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531815"
---
# <a name="compiler-error-c2812"></a>编译器错误 C2812

> \#导入不支持 /clr: pure 和 /clr: safe

## <a name="remarks"></a>备注

**/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

[#import 指令](../../preprocessor/hash-import-directive-cpp.md)不支持 **/clr: pure**并 **/clr: safe**因为`#import`需要本机编译器支持库使用。

## <a name="example"></a>示例

下面的示例生成 C2812。

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```