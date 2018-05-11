---
title: stdext 命名空间 | Microsoft Docs
ms.custom: ''
ms.date: 09/06/2017
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- stdext
dev_langs:
- C++
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 302d5b696a3413e36dd76cb931556a3fae7e7615
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="stdext-namespace"></a>stdext 命名空间

成员[ \<hash_map >](../standard-library/hash-map.md)和[ \<hash_set >](../standard-library/hash-set.md)标头文件当前不是 ISO c + + 标准的一部分。 因此，这些类型和成员已从 `std` 命名空间移动到命名空间 `stdext`以保持符合 C++ 标准。

使用编译时[/Ze](../build/reference/za-ze-disable-language-extensions.md)，这是默认设置，则编译器会警告上使用`std`成员\<hash_map > 和\<hash_set > 标头文件。 若要禁用该警告，请使用 [警告](../preprocessor/warning.md) 杂注。

若要让编译器生成的用于错误`std`成员\<hash_map > 和\<hash_set > 标头文件都具有 **/Ze**，添加以下指令之前`#include`任何 c + + 标准库头文件。

```cpp
#define _DEFINE_DEPRECATED_HASH_CLASSES 0
```

使用编译时 **/Za**，编译器将生成错误。

## <a name="see-also"></a>请参阅

[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)

