---
title: 注册表宏
ms.date: 08/19/2019
f1_keywords:
- atlcom/ATL::_ATL_STATIC_REGISTRY
- atlcom/ATL::DECLARE_LIBID
- atlcom/ATL::DECLARE_NO_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY_APPID_RESOURCEID
- atlcom/ATL::DECLARE_REGISTRY_RESOURCE
- atlcom/ATL::DECLARE_REGISTRY_RESOURCEID
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
ms.openlocfilehash: fd012b4300f4cd72cdc9ab363b770ac1dbefa06e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326044"
---
# <a name="registry-macros"></a>注册表宏

这些宏定义有用的类型库和注册表工具。

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|指示您希望对象的注册代码位于对象中，以避免依赖 ATL。Dll。|
|[DECLARE_LIBID](#declare_libid)|为 ATL 提供了获取类型库的*升标*的方法。|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|避免默认 ATL 注册。|
|[DECLARE_REGISTRY](#declare_registry)|在系统注册表中输入或删除主对象的条目。|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|指定自动注册*应用程序所需的*信息。|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|查找命名资源并在其中运行注册表脚本。|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|查找由 ID 号标识的资源，并在其中运行注册表脚本。|

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="_atl_static_registry"></a><a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY

指示您希望对象的注册代码位于对象中以避免依赖 ATL 的符号。Dll。

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>备注

定义ATL_STATIC_REGISTRY时，应使用以下代码：

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

## <a name="declare_libid"></a><a name="declare_libid"></a>DECLARE_LIBID

为 ATL 提供了获取类型库的*升标*的方法。

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>参数

*利比德*<br/>
类型库的 GUID。

### <a name="remarks"></a>备注

在`CAtlModuleT`派生类中使用DECLARE_LIBID。

### <a name="example"></a>示例

非属性化向导生成的 ATL 项目将具有使用此宏的示例。

## <a name="declare_no_registry"></a><a name="declare_no_registry"></a>DECLARE_NO_REGISTRY

如果要避免显示此宏的类的任何默认 ATL 注册，请使用DECLARE_NO_REGISTRY。

```
DECLARE_NO_REGISTRY()
```

## <a name="declare_registry"></a><a name="declare_registry"></a>DECLARE_REGISTRY

将标准类注册输入系统注册表，或将其从系统注册表中删除。

```
DECLARE_REGISTRY(
    class,
    pid,
    vpid,
    nid,
    flags )
```

### <a name="parameters"></a>参数

*class*<br/>
[在]包括用于向后兼容性。

*Pid*<br/>
[在]LPCTSTR，它是特定于版本的程序标识符。

*vpid*<br/>
[在]LPCTSTR，它是一个独立于版本的程序标识符。

*尼德*<br/>
[在]UINT，它是注册表中资源字符串的索引，用于用作程序的说明。

*标志*<br/>
[在]包含注册表中程序线程模型的 DWORD。 必须为以下值之一：THREADFLAGS_APARTMENT、THREADFLAGS_BOTH 或 AUTPRXFLAG。

### <a name="remarks"></a>备注

标准注册由 CLSID、程序 ID、独立于版本的程序 ID、描述字符串和线程模型组成。

使用 ATL 添加类向导创建对象或控件时，向导将自动实现基于脚本的注册表支持，并将[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)宏添加到文件中。 如果不需要基于脚本的注册表支持，则需要将此宏替换为DECLARE_REGISTRY。 DECLARE_REGISTRY仅将上述五个基本键插入注册表。 您必须手动编写代码才能将其他键插入注册表。

## <a name="declare_registry_appid_resourceid"></a><a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID

指定自动注册*应用程序所需的*信息。

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>参数

*渣 油*<br/>
包含有关*应用程序*的信息的 .rgs 文件的资源 ID。

*应用程序*<br/>
一个 GUID。

### <a name="remarks"></a>备注

在`CAtlModuleT`派生类中使用DECLARE_REGISTRY_APPID_RESOURCEID。

### <a name="example"></a>示例

使用"添加类"代码向导添加到 ATL 项目的类将具有使用此宏的示例。

## <a name="declare_registry_resource"></a><a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE

获取包含注册表文件的命名资源，并运行脚本以将对象输入到系统注册表中或从系统注册表中删除它们。

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>参数

** x <br/>
[在]资源的字符串标识符。

### <a name="remarks"></a>备注

使用 ATL 项目向导创建对象或控件时，向导将自动实现基于脚本的注册表支持，并将[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)宏（类似于DECLARE_REGISTRY_RESOURCE）添加到文件中。

您可以静态地与 ATL 注册表组件 （注册器） 链接，以优化注册表访问。 要静态链接到注册器代码，请向*pch.h*文件添加以下行（Visual Studio 2017 和更早版本中的*stdafx.h）：*

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

如果希望 ATL 在运行时替换替换值，请不要指定DECLARE_REGISTRY_RESOURCE或DECLARE_REGISTRY_RESOURCEID宏。 相反，请创建一个`_ATL_REGMAP_ENTRIES`结构数组，其中每个条目包含一个变量占位符，该占位符与值配对，以在运行时替换占位符。 然后调用[CAtlModule：：从资源D](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule 更新注册表：更新注册表从资源](catlmodule-class.md#updateregistryfromresources)，传递数组。 这会将`_ATL_REGMAP_ENTRIES`结构中的所有替换值添加到注册器的替换映射中。

有关可替换参数和脚本的详细信息，请参阅[ATL 注册表组件 （注册） 一](../../atl/atl-registry-component-registrar.md)文。

## <a name="declare_registry_resourceid"></a><a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID

与[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)相同，只不过它使用向导生成的 UINT 来标识资源，而不是字符串名称。

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>参数

** x <br/>
[在]向导生成的资源标识符。

### <a name="remarks"></a>备注

使用 ATL 项目向导创建对象或控件时，向导将自动实现基于脚本的注册表支持，并将DECLARE_REGISTRY_RESOURCEID宏添加到文件中。

您可以静态地与 ATL 注册表组件 （注册器） 链接，以优化注册表访问。 要静态链接到注册器代码，请向*stdafx.h*文件添加以下行（Visual Studio 2019 及更高版本中*的 pch.h）：*

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

如果希望 ATL 在运行时替换替换值，请不要指定DECLARE_REGISTRY_RESOURCE或DECLARE_REGISTRY_RESOURCEID宏。 相反，请创建一个`_ATL_REGMAP_ENTRIES`结构数组，其中每个条目包含一个变量占位符，该占位符与值配对，以在运行时替换占位符。 然后调用[CAtlModule：：从资源D](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule 更新注册表：更新注册表从资源](catlmodule-class.md#updateregistryfromresources)，传递数组。 这会将`_ATL_REGMAP_ENTRIES`结构中的所有替换值添加到注册器的替换映射中。

有关可替换参数和脚本的详细信息，请参阅[ATL 注册表组件 （注册） 一](../../atl/atl-registry-component-registrar.md)文。

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)
