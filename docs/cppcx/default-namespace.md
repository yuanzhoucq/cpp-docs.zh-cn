---
title: default 命名空间
ms.date: 12/30/2016
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
ms.openlocfilehash: 60a47c9549ee40b419eb5f4aa84720f8dcd1c366
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389458"
---
# <a name="default-namespace"></a>default 命名空间

`default`命名空间范围的内置类型支持的C++/CX。

## <a name="syntax"></a>语法

```
namespace default;
```

### <a name="members"></a>成员

所有内置类型都继承以下成员。

|||
|-|-|
|[default::(type_name)::Equals](../cppcx/default-type-name-equals-method.md)|确定指定的对象是否等于当前对象。|
|[default::(type_name)::GetHashCode](../cppcx/default-type-name-gethashcode-method.md)|返回此实例的哈希代码。|
|[default::(type_name)::GetType](../cppcx/default-type-name-gettype-method.md)|返回表示当前类型的字符串。|
|[default::(type_name)::ToString](../cppcx/default-type-name-tostring-method.md)|返回表示当前类型的字符串。|

### <a name="built-in-types"></a>内置类型

|名称|描述|
|----------|-----------------|
|`char16`|表示 Unicode (UTF-16) 码位的 16 位非数字值。|
|`float32`|32 位 IEEE 754 浮点数。|
|`float64`|64 位 IEEE 754 浮点数。|
|`int16`|16 位带符号整数。|
|`int32`|32 位带符号整数。|
|`int64`|64 位带符号整数。|
|`int8`|8 位带符号数值。|
|`uint16`|16 位无符号整数。|
|`uint32`|32 位无符号整数。|
|`uint64`|64 位无符号整数。|
|`uint8`|8 位无符号数值。|

### <a name="requirements"></a>要求

**标头：** vccorlib.h

## <a name="see-also"></a>请参阅

[VisualC++语言参考](../cppcx/visual-c-language-reference-c-cx.md)
