---
title: 编译器错误 C2435
ms.date: 11/04/2016
f1_keywords:
- C2435
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
ms.openlocfilehash: 5cd7a83575da7ab2a30401406d0c2ccf6c1b603e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166641"
---
# <a name="compiler-error-c2435"></a>编译器错误 C2435

> '*var*： 动态初始化需要托管的 CRT，不能使用 /clr: safe 进行编译

## <a name="remarks"></a>备注

**/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

每个应用程序域的全局变量的初始化要求使用编译的 CRT `/clr:pure`，这不会生成可验证映像。

有关详细信息，请参见 [应用程序域](../../cpp/appdomain.md) 和 [过程](../../cpp/process.md)。

## <a name="example"></a>示例

下面的示例生成 C2435:

```cpp
// C2435.cpp
// compile with: /clr:safe /c
int globalvar = 0;   // C2435

__declspec(process)
int globalvar2 = 0;
```