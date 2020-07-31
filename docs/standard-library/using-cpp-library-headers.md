---
title: 使用 C++ 库标头
ms.date: 11/04/2016
helpviewer_keywords:
- headers, naming in C++ include directive
- standard header in C++
- headers
- INCLUDE directive
- headers, C++ Standard Library
- library headers
- C++ Standard Library, headers
ms.assetid: a36e889e-1af2-4cd9-a211-bfc7a3fd8e85
ms.openlocfilehash: a73ebebb4fdde5dd72f148390d004c32b9f4dff7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215473"
---
# <a name="using-c-library-headers"></a>使用 C++ 库标头

通过在 Include 指令中为其命名，可包括标准标头的内容。

```cpp
#include <iostream>// include I/O facilities
```

可按任何顺序包括标准标头，可多次包括一个标准标头，或包括用于定义相同宏或相同类型的两个或多个标准标头。 声明内不能包括标准标头。 包括标准标头之前，不能定义具有与关键字相同名称的宏。

如果 C++ 库标头包括任何其他 C++ 库标头，则需要定义所需的类型。 （请始终在翻译单元中显式包含所需的任何 c + + 库标头，但避免您猜到了错误的实际依赖项。）标准 C 标头决不包含其他标准标头。 标准标头仅声明或定义此文档中描述的相关实体。

库中的每个函数都在标准标头中声明。 与在标准 C 中不同，如果一个屏蔽宏包含与屏蔽函数声明及实现相同效果的函数相同的名称，则标准标头不提供此屏蔽宏。 若要深入了解屏蔽宏，请参阅 [C++ 库约定](../standard-library/cpp-library-conventions.md)。

C + + 库标头中除**运算符 delete**和**运算符 new**以外的所有名称均在 `std` 命名空间或命名空间中嵌套的命名空间中定义 `std` 。 例如，将名称 `cin` 引用为 `std::cin`。 但是请注意，该宏名称不受命名空间限定，因此你始终需要写入不带命名空间限定符的 `__STD_COMPLEX`。

在某些转换环境中（包括 c + + 库标头），可以将命名空间中声明的外部名称提升 `std` 到全局命名空间，其中 **`using`** 每个名称都有单独的声明。 否则，标头不** 能将任何库名称引入当前命名空间中。

C + + 标准要求 C 标准标头声明命名空间中的所有外部名称 `std` ，然后将它们提升到全局命名空间，其中每个名称各有单独的 **`using`** 声明。 但在某些转换环境中，C 标准标头不包含命名空间声明，所有名称都直接在全局命名空间中进行声明。 因此，用于处理命名空间的可移植性最高的方法将遵循以下两种规则：

- 若要肯定在命名空间中声明 `std` 传统上在中声明的外部名称 \<stdlib.h> ，例如，包含标头 \<cstdlib> 。 此名称也可能在全局命名空间中声明。

- 若要肯定在全局命名空间中声明一个在中声明的外部名称 \<stdlib.h> ，请直接包含该标头 \<stdlib.h> 。 此名称也可能在命名空间 `std` 中声明。

因此，如果您要调用 `std::abort` 来导致异常终止，则应该包含 \<cstdlib> 。 如果要调用 `abort` ，则应包含 \<stdlib.h> 。

此外，还可以编写以下声明：

```cpp
using namespace std;
```

这会将所有库名称引入当前命名空间。 如果在所有 Include 指令之后立即编写此声明，则会将这些名称提升至全局命名空间中。 随后可忽略转换单元的余数中的命名空间注意事项。 同时可避免不同转换环境之间产生的最大不同。

除非明确指定，否则在你的程序中，可能不能在 `std` 命名空间中定义名称，或不能在 `std` 命名空间内的嵌套命名空间中定义名称。

## <a name="see-also"></a>另请参阅

[C + + 标准库概述](../standard-library/cpp-standard-library-overview.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
