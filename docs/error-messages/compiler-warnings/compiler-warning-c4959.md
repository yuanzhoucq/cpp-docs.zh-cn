---
title: 编译器警告 C4959 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4959
dev_langs:
- C++
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2819664fa94ca777339156dc9a31da17b991c6da
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705159"
---
# <a name="compiler-warning-c4959"></a>编译器警告 C4959

> 不能定义非托管的结构*类型*在 /clr: safe 因为访问其成员会产生不可验证的代码

## <a name="remarks"></a>备注

访问非托管类型的成员会生成无法验证的 (peverify.exe) 映像。

有关详细信息，请参阅[纯代码和可验证代码 (C + + /cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

**/Clr: safe**编译器选项是在 Visual Studio 2015 中已过时，并在 Visual Studio 2017 中不支持。

此警告作为错误发出，可通过 [warning](../../preprocessor/warning.md) 杂注或 [/wd](../../build/reference/compiler-option-warning-level.md) 编译器选项禁用该警告。

## <a name="example"></a>示例

下面的示例生成 C4959：

```cpp
// C4959.cpp
// compile with: /clr:safe

// Uncomment the following line to resolve.
// #pragma warning( disable : 4959 )
struct X {
   int data;
};

int main() {
   X x;
   x.data = 10;   // C4959
}
```