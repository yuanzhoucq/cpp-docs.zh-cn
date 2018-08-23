---
title: 编译器错误 C2393 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2393
dev_langs:
- C++
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 057537c8efcf6e827d9ac9aaf36c0eace6d24156
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704025"
---
# <a name="compiler-error-c2393"></a>编译器错误 C2393

> *符号*： 不能在段中分配每个 appdomain 符号*段*

## <a name="remarks"></a>备注

**/Clr: pure**和 **/clr: safe**编译器选项是在 Visual Studio 2015 中已过时，在 Visual Studio 2017 中不支持。

使用[appdomain](../../cpp/appdomain.md)变量表示您正在用编译 **/clr: pure**或 **/clr: safe**，和的安全或纯映像不能包含数据段。

请参阅[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)有关详细信息。

## <a name="example"></a>示例

下面的示例生成 C2393。 若要解决此问题，不要创建的数据段。

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```