---
title: 编译器警告 C4936 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4936
dev_langs:
- C++
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0be4a565dd251da77174c401c23b8ed8bfc531b0
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703934"
---
# <a name="compiler-warning-c4936"></a>编译器警告 C4936

> 只有使用 /clr 或 /clr:pure 编译时，才支持此 __declspec

## <a name="remarks"></a>备注

**/Clr: pure**编译器选项是在 Visual Studio 2015 中已过时，并在 Visual Studio 2017 中不支持。

使用了 `__declspec` 修饰符，但只有在编译时使用 `__declspec` /clr [选项之一的情况下](../../build/reference/clr-common-language-runtime-compilation.md) 修饰符方才有效。

有关详细信息，请参见 [应用程序域](../../cpp/appdomain.md) 和 [过程](../../cpp/process.md)。

始终发出 C4936 错误。  可以使用 [warning](../../preprocessor/warning.md) 杂注来禁用 C4936。

## <a name="example"></a>示例

下面的示例生成 C4936：

```cpp
// C4936.cpp
// compile with: /c
// #pragma warning (disable : 4936)
__declspec(process) int i;   // C4936
__declspec(appdomain) int j;   // C4936
```