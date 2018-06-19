---
title: is_error_code_enum 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- system_error/std::is_error_code_enum
dev_langs:
- C++
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7024817c5a02d7c4a529167ca65a292b34be119
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844596"
---
# <a name="iserrorcodeenum-class"></a>is_error_code_enum 类

表示测试 [error_code](../standard-library/error-code-class.md) 枚举的类型谓词。

## <a name="syntax"></a>语法

```cpp
template <_Enum>
class is_error_code_enum;
```

## <a name="remarks"></a>备注

如果类型 `_Enum` 是一个适合存储在类型 `error_code` 的对象中的枚举值，则此[类型谓词](../standard-library/type-traits.md)的实例为 true。

允许将专用化添加到此类型，以获得用户定义类型。

## <a name="requirements"></a>要求

**标头：** \<system_error>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
