---
title: 编译器错误 C2812 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2812
dev_langs:
- C++
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c5469e4f7be3c164cc63fa30f5069009846be48
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705018"
---
# <a name="compiler-error-c2812"></a>编译器错误 C2812

> \#导入不支持使用 /clr: pure 和 /clr: safe

## <a name="remarks"></a>备注

**/Clr: pure**和 **/clr: safe**编译器选项是在 Visual Studio 2015 中已过时，在 Visual Studio 2017 中不支持。

[#import 指令](../../preprocessor/hash-import-directive-cpp.md)不支持 **/clr: pure**和 **/clr: safe**因为`#import`需要本机编译器支持库的使用。

## <a name="example"></a>示例

下面的示例生成 C2812。

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```