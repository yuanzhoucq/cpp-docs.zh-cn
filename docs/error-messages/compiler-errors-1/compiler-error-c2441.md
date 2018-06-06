---
title: 编译器错误 C2441 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2441
dev_langs:
- C++
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d4224d9090f3ace43f61a10c599fafa78d21600
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705275"
---
# <a name="compiler-error-c2441"></a>编译器错误 C2441

> *变量*: __declspec 使用声明的符号必须是常量在 /clr: pure 模式

## <a name="remarks"></a>备注

**/Clr: pure**和 **/clr: safe**编译器选项是在 Visual Studio 2015 中已过时，在 Visual Studio 2017 中不支持。

默认情况下，变量是每个应用程序域下 **/clr: pure**。 变量标记`__declspec(process)`下 **/clr: pure**很容易导致错误，如果在一个应用程序域中修改并在另一个中读取。

因此，编译器会强制执行每个进程变量为`const`下 **/clr： 纯**，仅在所有应用程序域中的进行读取它们。

有关详细信息，请参阅[过程](../../cpp/process.md)和[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>示例

下面的示例生成 C2441。

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```