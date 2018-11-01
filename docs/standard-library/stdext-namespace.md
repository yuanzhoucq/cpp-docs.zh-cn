---
title: stdext 命名空间
ms.date: 09/06/2017
f1_keywords:
- stdext
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
ms.openlocfilehash: aeba486393e6b45481108f967f3de8eb73a0adea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468479"
---
# <a name="stdext-namespace"></a>stdext 命名空间

成员[ \<hash_map >](../standard-library/hash-map.md)并[ \<hash_set >](../standard-library/hash-set.md)标头文件当前不是 ISO c + + 标准的一部分。 因此，这些类型和成员已从 `std` 命名空间移动到命名空间 `stdext`以保持符合 C++ 标准。

使用编译时[/Ze](../build/reference/za-ze-disable-language-extensions.md)，这是默认情况下，编译器会发出警告的使用`std`的成员\<hash_map > 和\<hash_set > 标头文件。 若要禁用该警告，请使用 [警告](../preprocessor/warning.md) 杂注。

若要让编译器生成的错误`std`的成员\<hash_map > 和\<hash_set > 标头文件的工具 **/Ze**，添加以下指令之前`#include`任何 c + + 标准库标头文件。

```cpp
#define _DEFINE_DEPRECATED_HASH_CLASSES 0
```

使用编译时 **/Za**，编译器将生成错误。

## <a name="see-also"></a>请参阅

[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)

