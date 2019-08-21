---
title: 编译器警告 C4984
ms.date: 08/19/2019
f1_keywords:
- C4984
helpviewer_keywords:
- C4984
ms.openlocfilehash: 91ae30018c7de633d8ba23d538b301ad4bbac984
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2019
ms.locfileid: "69632901"
---
# <a name="compiler-warning-c4984"></a>编译器警告 C4984

> "if constexpr" 是 c + + 17 语言扩展

## <a name="remarks"></a>备注

编译器在使用默认`if constexpr` c + + 14 标准编译的代码中找到了一个表达式。 此表达式是从 c + + 17 标准开始指定的。 如果需要 c + + 11 或 c + + 14 兼容性, 此表达式是不可移植的。

默认情况下, C4984 作为错误发出, 但它是 suppressible 的。 若要通过将代码编译为 c + + 17 来启用此表达式, 请使用[/std: c + + 17 或/std: c + + 最新版本](../../build/reference/std-specify-language-standard-version.md)。 若要在`if constexpr`作为 Microsoft 扩展的 c + + 14 中编译的代码中使用表达式, 可以取消、禁用或更改错误消息的警告等级。 您可以使用[/wd4984](../../build/reference/compiler-option-warning-level.md)禁用 C4984, 或 __/w__*N*__4984__将其启用为级别*N*警告而不是错误。 或者, 在引发警告的行之前, 使用[#pragma warning (抑制: 4984)](../../preprocessor/warning.md) 。

在 Visual Studio 2017 版本15.3 中开始提供此警告。 有关如何禁用特定编译器版本或更高版本中引入的警告的信息, 请参阅编译器[警告 (按编译器版本](compiler-warnings-by-compiler-version.md))。

## <a name="example"></a>示例

此示例生成 C4984, 并显示修复方法的方法:

```cpp
// C4984.cpp
// compile with: cl /EHsc C4984.cpp
#include <iostream>

int main()
{
    constexpr bool compile_time = true;
    // Uncomment the following line or use /std:c++17 to fix
    // #pragma warning(suppress:4984)
    if constexpr (compile_time)
    {
        std::cout << "compile_time is true";
    }
    else
    {
        std::cout << "compile_time is false";
    }
}
```
