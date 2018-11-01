---
title: 编译器错误 C2346
ms.date: 11/04/2016
f1_keywords:
- C2346
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
ms.openlocfilehash: a6d75ca671e22203cb40ca18de21606834eeefa8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527356"
---
# <a name="compiler-error-c2346"></a>编译器错误 C2346

function 不能编译为本机： 原因

编译器无法将函数编译为 MSIL。

有关详细信息，请参阅[managed、 unmanaged](../../preprocessor/managed-unmanaged.md)并[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

### <a name="to-correct-this-error"></a>更正此错误

1. 不能编译为 MSIL 的函数中删除的代码。

1. 可以不编译的模块 **/clr**，或将函数标记为非托管与非托管杂注。

## <a name="example"></a>示例

下面的示例生成 C2346。

```
// C2346.cpp
// processor: x86
// compile with: /clr
// C2346 expected
struct S
{
   S()
   {
      { __asm { nop } }
   }
   virtual __clrcall ~S() { }
};

void main()
{
   S s;
}
```