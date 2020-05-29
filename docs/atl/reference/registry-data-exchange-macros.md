---
title: 注册表数据交换宏
ms.date: 11/04/2016
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
ms.openlocfilehash: a7d580e4907cec40f97c0cead616665fff7b8a01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326074"
---
# <a name="registry-data-exchange-macros"></a>注册表数据交换宏

这些宏执行注册表数据交换操作。

|||
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|标记注册表数据交换映射的开头。|
|[END_RDX_MAP](#end_rdx_map)|标记注册表数据交换映射的末尾。|
|[RDX_BINARY](#rdx_binary)|将指定的注册表项与 BYTE 类型的指定成员变量关联。|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|将指定的注册表项与 CString 类型的指定成员变量关联。|
|[RDX_DWORD](#rdx_dword)|将指定的注册表项与 DWORD 类型的指定成员变量关联。|
|[RDX_TEXT](#rdx_text)|将指定的注册表项与 TCHAR 类型的指定成员变量关联。|

## <a name="requirements"></a>要求

**标题：** atlplus.h

## <a name="begin_rdx_map"></a><a name="begin_rdx_map"></a>BEGIN_RDX_MAP

标记注册表数据交换映射的开头。

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>备注

以下宏用于注册表数据交换映射中读取和写入系统注册表中的条目：

|宏|说明|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|将指定的注册表项与 BYTE 类型的指定成员变量关联。|
|[RDX_DWORD](#rdx_dword)|将指定的注册表项与 DWORD 类型的指定成员变量关联。|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|将指定的注册表项与 CString 类型的指定成员变量关联。|
|[RDX_TEXT](#rdx_text)|将指定的注册表项与 TCHAR 类型的指定成员变量关联。|

当代码需要在系统注册表和 RDX 映射中指定的变量之间交换数据时，应使用全局函数[RegistryDataExchange，](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)或由BEGIN_RDX_MAP和END_RDX_MAP宏创建的相同名称的成员函数。

## <a name="end_rdx_map"></a><a name="end_rdx_map"></a>END_RDX_MAP

标记注册表数据交换映射的末尾。

```
END_RDX_MAP
```

## <a name="rdx_binary"></a><a name="rdx_binary"></a>RDX_BINARY

将指定的注册表项与 BYTE 类型的指定成员变量关联。

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>参数

*根键*<br/>
注册表密钥根。

*子键*<br/>
注册表子项。

*值名称*<br/>
注册表项。

*成员*<br/>
要与指定的注册表项关联的成员变量。

*member_size*<br/>
成员变量的大小（以字节为单位）。

### <a name="remarks"></a>备注

此宏与BEGIN_RDX_MAP和END_RDX_MAP宏结合使用，用于将成员变量与给定的注册表项相关联。 全局函数[RegistryDataExchange，](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)或由BEGIN_RDX_MAP和END_RDX_MAP宏创建的同名成员函数，应用于在 RDX 映射中系统注册表和成员变量之间执行数据交换。

## <a name="rdx_cstring_text"></a><a name="rdx_cstring_text"></a>RDX_CSTRING_TEXT

将指定的注册表项与 CString 类型的指定成员变量关联。

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>参数

*根键*<br/>
注册表密钥根。

*子键*<br/>
注册表子项。

*值名称*<br/>
注册表项。

*成员*<br/>
要与指定的注册表项关联的成员变量。

*member_size*<br/>
成员变量的大小（以字节为单位）。

### <a name="remarks"></a>备注

此宏与BEGIN_RDX_MAP和END_RDX_MAP宏结合使用，用于将成员变量与给定的注册表项相关联。 全局函数[RegistryDataExchange，](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)或由BEGIN_RDX_MAP和END_RDX_MAP宏创建的同名成员函数，应用于在 RDX 映射中系统注册表和成员变量之间执行数据交换。

## <a name="rdx_dword"></a><a name="rdx_dword"></a>RDX_DWORD

将指定的注册表项与 DWORD 类型的指定成员变量关联。

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>参数

*根键*<br/>
注册表密钥根。

*子键*<br/>
注册表子项。

*值名称*<br/>
注册表项。

*成员*<br/>
要与指定的注册表项关联的成员变量。

*member_size*<br/>
成员变量的大小（以字节为单位）。

### <a name="remarks"></a>备注

此宏与BEGIN_RDX_MAP和END_RDX_MAP宏结合使用，用于将成员变量与给定的注册表项相关联。 全局函数[RegistryDataExchange，](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)或由BEGIN_RDX_MAP和END_RDX_MAP宏创建的同名成员函数，应用于在 RDX 映射中系统注册表和成员变量之间执行数据交换。

## <a name="rdx_text"></a><a name="rdx_text"></a>RDX_TEXT

将指定的注册表项与 TCHAR 类型的指定成员变量关联。

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>参数

*根键*<br/>
注册表密钥根。

*子键*<br/>
注册表子项。

*值名称*<br/>
注册表项。

*成员*<br/>
要与指定的注册表项关联的成员变量。

*member_size*<br/>
成员变量的大小（以字节为单位）。

### <a name="remarks"></a>备注

此宏与BEGIN_RDX_MAP和END_RDX_MAP宏结合使用，用于将成员变量与给定的注册表项相关联。 全局函数[RegistryDataExchange，](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)或由BEGIN_RDX_MAP和END_RDX_MAP宏创建的同名成员函数，应用于在 RDX 映射中系统注册表和成员变量之间执行数据交换。

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
