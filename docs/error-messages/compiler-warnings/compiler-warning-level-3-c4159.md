---
title: 编译器警告 （等级 3） C4159 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4159
dev_langs:
- C++
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43e3d63ad1d482222c4ffa7aa7435d0e660f3985
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223313"
---
# <a name="compiler-warning-level-3-c4159"></a>编译器警告 （等级 3） C4159

> #<a name="pragma-pragmapop--has-popped-previously-pushed-identifier-identifier"></a>杂注 pragma(pop,...)： 将先前入栈的标识符*标识符*

## <a name="remarks"></a>备注

你的源代码包含**推送**标识符的杂注指令后, 跟**pop**指令不含标识符。 因此，*标识符*是弹出，并且后续的用法*标识符*可能导致意外的行为。

## <a name="example"></a>示例

若要避免此警告，在中提供的标识符**pop**指令。 例如：

```cpp
// C4159.cpp
// compile with: /W3
#pragma pack(push, f)
#pragma pack(pop)   // C4159

// using the identifier resolves the warning
// #pragma pack(pop, f)

int main()
{
}
```