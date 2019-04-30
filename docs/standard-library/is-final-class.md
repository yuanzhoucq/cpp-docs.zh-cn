---
title: is_final 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_final
helpviewer_keywords:
- is_final
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
ms.openlocfilehash: f605b160f6ed71aaafcc7c391e17180e4b243444
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346445"
---
# <a name="isfinal-class"></a>is_final 类

测试类型是否是标记为 `final` 的类类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_final;
```

### <a name="parameters"></a>参数

*T*<br/>
要查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*T*标记的类类型`final`，否则为 false。 如果*T*是类类型，它必须是完整的类型。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[final 说明符](../cpp/final-specifier.md)<br/>
