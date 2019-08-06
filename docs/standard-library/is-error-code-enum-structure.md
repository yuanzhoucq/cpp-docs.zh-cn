---
title: is_error_code_enum 结构
ms.date: 11/04/2016
f1_keywords:
- future/std::is_error_code_enum
ms.assetid: 84ae4b99-66d2-41ba-9b50-645fcbe14630
ms.openlocfilehash: f2a9f0d6b812b430ba3fca2d39343f912791da6f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452615"
---
# <a name="iserrorcodeenum-structure"></a>is_error_code_enum 结构

指示 [future_errc](../standard-library/future-enums.md#future_errc) 适合存储 [error_code](../standard-library/error-code-class.md) 的专用化。

## <a name="syntax"></a>语法

```cpp
template <>
struct is_error_code_enum<Future_errc> : public true_type;
```

## <a name="requirements"></a>要求

**标头:** \<未来 >

**命名空间：** std

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
