---
title: 编译器错误 C2435
ms.date: 11/04/2016
f1_keywords:
- C2435
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
ms.openlocfilehash: 7ef22711884dabb83efa8c7ebfdb7648316c12ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205408"
---
# <a name="compiler-error-c2435"></a>编译器错误 C2435

> "*var*"：动态初始化需要托管的 CRT，不能通过/clr： safe 进行编译

## <a name="remarks"></a>备注

**/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

全局每个应用程序域变量的初始化要求使用 `/clr:pure`编译 CRT，此功能不会生成可验证的映像。

有关详细信息，请参见 [应用程序域](../../cpp/appdomain.md) 和 [过程](../../cpp/process.md)。

## <a name="example"></a>示例

下面的示例生成 C2435：

```cpp
// C2435.cpp
// compile with: /clr:safe /c
int globalvar = 0;   // C2435

__declspec(process)
int globalvar2 = 0;
```
