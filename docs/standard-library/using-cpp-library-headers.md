---
title: 使用 C++ 库标头 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- headers, naming in C++ include directive
- standard header in C++
- headers
- INCLUDE directive
- headers, C++ Standard Library
- library headers
- C++ Standard Library, headers
ms.assetid: a36e889e-1af2-4cd9-a211-bfc7a3fd8e85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30d31f30971184356374b3991fedda474ca27465
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="using-c-library-headers"></a>使用 C++ 库标头

通过在 Include 指令中为其命名，可包括标准标头的内容。

```cpp
#include <iostream>// include I/O facilities
```

可按任何顺序包括标准标头，可多次包括一个标准标头，或包括用于定义相同宏或相同类型的两个或多个标准标头。 声明内不能包括标准标头。 包括标准标头之前，不能定义具有与关键字相同名称的宏。

如果 C++ 库标头包括任何其他 C++ 库标头，则需要定义所需的类型。 （但是，始终显式包括转换单元中所需的任何 C++ 库标头，以免弄错其实际依赖项。）标准 C 标头不能包括另一标准标头。 标准标头仅声明或定义此文档中描述的相关实体。

库中的每个函数都在标准标头中声明。 与在标准 C 中不同，如果一个屏蔽宏包含与屏蔽函数声明及实现相同效果的函数相同的名称，则标准标头不提供此屏蔽宏。 若要深入了解屏蔽宏，请参阅 [C++ 库约定](../standard-library/cpp-library-conventions.md)。

除 C++ 库标头中的 `operator delete` 和 `operator new` 以外的所有名称都在 `std` 命名空间中定义，或者在 `std` 命名空间内的嵌套命名空间中定义。 例如，将名称 `cin` 引用为 `std::cin`。 但是请注意，该宏名称不受命名空间限定，因此你始终需要写入不带命名空间限定符的 `__STD_COMPLEX`。

在某些转换环境中（包括 C++ 库标头），可将在 `std` 的命名空间中声明的外部名称提升至全局命名空间中，其中每个名称都包含单个 `using` 声明。 否则，标头不能将任何库名称引入当前命名空间中。

C++ 标准要求 C 标准标头对命名空间 `std` 中的所有外部名称进行声明，然后将它们提升至全局命名空间中，其中每个名称都包含单个 `using` 声明。 但在某些转换环境中，C 标准标头不包含命名空间声明，所有名称都直接在全局命名空间中进行声明。 因此，用于处理命名空间的可移植性最高的方法将遵循以下两种规则：

- 例如，若要在命名空间 `std` 中肯定声明过去在 \<stdlib.h> 中声明的外部名称，则需包括标头 \<cstdlib>。 此名称也可能在全局命名空间中声明。

- 若要在全局命名空间中肯定声明已在 \<stdlib.h> 中声明的外部名称，请直接包括标头 \<stdlib.h>。 此名称也可能在命名空间 `std` 中声明。

因此，如果想要调用 `std::abort` 以产生异常终止，则应包括 \<cstdlib>。 如果想要调用 `abort`，则应包括 \<stdlib.h>。

此外，还可以编写以下声明：

```cpp
using namespace std;
```

这会将所有库名称引入当前命名空间。 如果在所有 Include 指令之后立即编写此声明，则会将这些名称提升至全局命名空间中。 随后可忽略转换单元的余数中的命名空间注意事项。 同时可避免不同转换环境之间产生的最大不同。

除非明确指定，否则在你的程序中，可能不能在 `std` 命名空间中定义名称，或不能在 `std` 命名空间内的嵌套命名空间中定义名称。

## <a name="see-also"></a>请参阅

[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
