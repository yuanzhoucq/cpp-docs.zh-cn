---
title: '&lt;ccomplex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ccomplex>
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
ms.openlocfilehash: ab9e95eb7b432a85a75d73d388ec069b0d04ac62
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351100"
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;

包含 C++ 标准库标头 [\<complex>](../standard-library/complex.md)，它可有效地包含标准 C 库标头 \<complex.h>，并将关联名称添加到 `std` 命名空间。

## <a name="syntax"></a>语法

```cpp
#include <ccomplex>
```

## <a name="remarks"></a>备注

包含该标头还将确保使用标准 C 库标头中的外部链接声明的名称在 `std` 命名空间中声明。

未在 `std` 命名空间中定义 \<complex.h> 中声明的名称 `clog`，因为这可能会与 [\<iostream>](../standard-library/iostream.md) 中声明的 `clog` 发生冲突。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)<br/>
