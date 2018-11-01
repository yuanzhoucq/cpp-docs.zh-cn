---
title: 编译器错误 C2393
ms.date: 11/04/2016
f1_keywords:
- C2393
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
ms.openlocfilehash: 39ca693aed3f08e7b2df3d687f94d93384393f23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566850"
---
# <a name="compiler-error-c2393"></a>编译器错误 C2393

> '*符号*： 不能在段中分配 per-appdomain 符号*段*

## <a name="remarks"></a>备注

**/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

使用[appdomain](../../cpp/appdomain.md)变量表示正在使用编译 **/clr: pure**或 **/clr: safe**，并且安全或纯映像不能包含数据段。

请参阅[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)有关详细信息。

## <a name="example"></a>示例

下面的示例生成 C2393。 若要解决此问题，不要创建的数据段。

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```