---
title: '&lt;ctgmath&gt; | Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
ms.assetid: ff521893-f445-4dc8-a2f6-699185bb7024
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fbff9bcb3e36ef65e811314d0c426c9992e87fda
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="ltctgmathgt"></a>&lt;ctgmath&gt;

实际上包括 C++ 标准库标头 \<ccomplex> 和 \<cmath>，用于提供等同于 \<tgmath.h> 的泛型类型算术宏。

## <a name="syntax"></a>语法

```cpp
#include <ctgmath>

```

## <a name="remarks"></a>备注

标准 C 库标头 \<tgmath.h> 的功能通过 \<ccomplex> 和 \<cmath> 中的重载来提供。

包含该标头还将确保使用标准 C 库标头中的外部链接声明的名称在 `std` 命名空间中声明。

## <a name="see-also"></a>请参阅

[\<ccomplex >](../standard-library/ccomplex.md)<br/>
[\<t h >](../standard-library/cmath.md)<br/>
[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
