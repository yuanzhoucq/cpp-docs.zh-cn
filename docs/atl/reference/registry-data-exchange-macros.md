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
ms.openlocfilehash: 69b823cbcd85ebaaeb05979283ea4f8fea80f4b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197479"
---
# <a name="registry-data-exchange-macros"></a>注册表数据交换宏

这些宏执行注册表数据交换操作。

|||
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|标记注册表数据交换映射的开始。|
|[END_RDX_MAP](#end_rdx_map)|将标记注册表数据交换映射的结尾。|
|[RDX_BINARY](#rdx_binary)|BYTE 类型的指定的成员变量相关联的指定的注册表项。|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|将指定的注册表项与指定的成员类型的变量的 CString 相关联。|
|[RDX_DWORD](#rdx_dword)|指定的注册表条目相关联的指定的成员变量的类型为 DWORD。|
|[RDX_TEXT](#rdx_text)|将指定的注册表项与指定的成员类型的变量的 TCHAR 相关联。|

## <a name="requirements"></a>要求

**标头：** atlplus.h

##  <a name="begin_rdx_map"></a>  BEGIN_RDX_MAP

标记注册表数据交换映射的开始。

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>备注

在注册表数据交换映射使用以下宏来读取和写入系统注册表中的条目：

|宏|描述|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|BYTE 类型的指定的成员变量相关联的指定的注册表项。|
|[RDX_DWORD](#rdx_dword)|指定的注册表条目相关联的指定的成员变量的类型为 DWORD。|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|将指定的注册表项与指定的成员类型的变量的 CString 相关联。|
|[RDX_TEXT](#rdx_text)|将指定的注册表项与指定的成员类型的变量的 TCHAR 相关联。|

全局函数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或应使用由 BEGIN_RDX_MAP 和 END_RDX_MAP 宏，创建具有相同名称的成员函数，每当你的代码需要在系统注册表之间交换数据和在 RDX 映射中指定的变量。

##  <a name="end_rdx_map"></a>  END_RDX_MAP

将标记注册表数据交换映射的结尾。

```
END_RDX_MAP
```

##  <a name="rdx_binary"></a>  RDX_BINARY

BYTE 类型的指定的成员变量相关联的指定的注册表项。

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>参数

*rootkey*<br/>
注册表项根。

*subkey*<br/>
注册表子项中。

*valuename*<br/>
注册表项中。

*member*<br/>
要与指定的注册表项相关联的成员变量。

*member_size*<br/>
以字节为单位的成员变量的大小。

### <a name="remarks"></a>备注

此宏与 BEGIN_RDX_MAP 和 END_RDX_MAP 宏结合使用，若要将成员变量与给定的注册表项相关联。 全局函数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或用于执行系统注册表和成员变量之间的数据交换由 BEGIN_RDX_MAP 和 END_RDX_MAP 宏，创建具有相同名称的成员函数在 RDX 图中。

##  <a name="rdx_cstring_text"></a>  RDX_CSTRING_TEXT

将指定的注册表项与指定的成员类型的变量的 CString 相关联。

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>参数

*rootkey*<br/>
注册表项根。

*subkey*<br/>
注册表子项中。

*valuename*<br/>
注册表项中。

*member*<br/>
要与指定的注册表项相关联的成员变量。

*member_size*<br/>
以字节为单位的成员变量的大小。

### <a name="remarks"></a>备注

此宏与 BEGIN_RDX_MAP 和 END_RDX_MAP 宏结合使用，若要将成员变量与给定的注册表项相关联。 全局函数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或用于执行系统注册表和成员变量之间的数据交换由 BEGIN_RDX_MAP 和 END_RDX_MAP 宏，创建具有相同名称的成员函数在 RDX 图中。

##  <a name="rdx_dword"></a>  RDX_DWORD

指定的注册表条目相关联的指定的成员变量的类型为 DWORD。

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>参数

*rootkey*<br/>
注册表项根。

*subkey*<br/>
注册表子项中。

*valuename*<br/>
注册表项中。

*member*<br/>
要与指定的注册表项相关联的成员变量。

*member_size*<br/>
以字节为单位的成员变量的大小。

### <a name="remarks"></a>备注

此宏与 BEGIN_RDX_MAP 和 END_RDX_MAP 宏结合使用，若要将成员变量与给定的注册表项相关联。 全局函数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或用于执行系统注册表和成员变量之间的数据交换由 BEGIN_RDX_MAP 和 END_RDX_MAP 宏，创建具有相同名称的成员函数在 RDX 图中。

##  <a name="rdx_text"></a>  RDX_TEXT

将指定的注册表项与指定的成员类型的变量的 TCHAR 相关联。

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>参数

*rootkey*<br/>
注册表项根。

*subkey*<br/>
注册表子项中。

*valuename*<br/>
注册表项中。

*member*<br/>
要与指定的注册表项相关联的成员变量。

*member_size*<br/>
以字节为单位的成员变量的大小。

### <a name="remarks"></a>备注

此宏与 BEGIN_RDX_MAP 和 END_RDX_MAP 宏结合使用，若要将成员变量与给定的注册表项相关联。 全局函数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或用于执行系统注册表和成员变量之间的数据交换由 BEGIN_RDX_MAP 和 END_RDX_MAP 宏，创建具有相同名称的成员函数在 RDX 图中。

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
