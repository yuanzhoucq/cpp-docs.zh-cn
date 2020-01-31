---
title: 编译器错误 C2346
ms.date: 11/04/2016
f1_keywords:
- C2346
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
ms.openlocfilehash: 91f2bac38166a8972193a7aaa7e84913b941c799
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518317"
---
# <a name="compiler-error-c2346"></a>编译器错误 C2346

"function" 不能编译为本机：原因

编译器无法将函数编译为 MSIL。

有关详细信息，请参阅[托管、非托管](../../preprocessor/managed-unmanaged.md)和[/Clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

### <a name="to-correct-this-error"></a>更正此错误

1. 删除不能编译为 MSIL 的函数中的代码。

1. 请勿用 **/clr**编译模块，或将函数标记为非托管杂注的非托管函数。

## <a name="example"></a>示例

下面的示例生成 C2346。

```cpp
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

int main()
{
   S s;
}
```
