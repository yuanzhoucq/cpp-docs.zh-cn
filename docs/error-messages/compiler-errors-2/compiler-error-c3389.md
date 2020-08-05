---
title: 编译器错误 C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: 8a040e649074e115b1b86ea56db6c9ef48f4c0d0
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520468"
---
# <a name="compiler-error-c3389"></a>编译器错误 C3389

> __declspec (*关键字*) 不能与/clr： pure 或/clr： safe 一起使用

## <a name="remarks"></a>备注

**`/clr:pure`** 和 **`/clr:safe`** 编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

[`__declspec`](../../cpp/declspec.md)使用的修饰符隐含每个进程的状态。  [`/clr:pure`](../../build/reference/clr-common-language-runtime-compilation.md)表示每个 [`appdomain`](../../cpp/appdomain.md) 状态。  因此，不允许使用*关键字* **`__declspec`** 修饰符和编译来声明变量 **`/clr:pure`** 。

## <a name="example"></a>示例

下面的示例生成 C3389：

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
