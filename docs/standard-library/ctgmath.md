---
title: '&lt;ctgmath&gt; | Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
ms.assetid: ff521893-f445-4dc8-a2f6-699185bb7024
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 76594e226f865e25ff93297fa45bd59310525885
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845045"
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
