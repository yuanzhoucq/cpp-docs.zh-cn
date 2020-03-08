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
ms.openlocfilehash: c2a70c15473798ba6eb2ef35e0b7ded395708586
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857130"
---
# <a name="registry-macros"></a>注册表宏

这些宏定义有用的类型库和注册表功能。

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|指示您希望对象的注册代码位于对象中，以避免依赖于 ATL.DLL.|
|[DECLARE_LIBID](#declare_libid)|为 ATL 提供了一种方法来获取类型库的*libid* 。|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|避免默认的 ATL 注册。|
|[DECLARE_REGISTRY](#declare_registry)|在系统注册表中输入或删除主对象的条目。|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|指定自动注册*appid*所需的信息。|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|查找指定的资源，并在其中运行注册表脚本。|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|查找由 ID 号标识的资源，并在其中运行注册表脚本。|

## <a name="requirements"></a>要求

**标头：** atlcom。h

##  <a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY

一个符号，指示你希望对象的注册代码位于对象中，以避免依赖于 ATL.DLL.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>备注

在定义 ATL_STATIC_REGISTRY 时，应使用以下代码：

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

##  <a name="declare_libid"></a>  DECLARE_LIBID

为 ATL 提供了一种方法来获取类型库的*libid* 。

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>参数

*libid*<br/>
类型库的 GUID。

### <a name="remarks"></a>备注

使用 `CAtlModuleT`派生类中的 DECLARE_LIBID。

### <a name="example"></a>示例

非特性向导生成的 ATL 项目将有一个使用此宏的示例。

##  <a name="declare_no_registry"></a>DECLARE_NO_REGISTRY

如果要避免显示此宏的类的任何默认 ATL 注册，请使用 DECLARE_NO_REGISTRY。

```
DECLARE_NO_REGISTRY()
```

##  <a name="declare_registry"></a>DECLARE_REGISTRY

将标准类注册输入到系统注册表中，或将其从系统注册表中移除。

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
中为了向后兼容而提供。

pid<br/>
中LPCTSTR，它是特定于版本的程序标识符。

*vpid*<br/>
中是独立于版本的程序标识符的 LPCTSTR。

*nid*<br/>
中UINT，是注册表中要用作程序说明的资源字符串的索引。

*flags*<br/>
中包含注册表中程序的线程模型的 DWORD。 必须是以下值之一：THREADFLAGS_APARTMENT、THREADFLAGS_BOTH 或 AUTPRXFLAG。

### <a name="remarks"></a>备注

标准注册包含 CLSID、程序 ID、独立于版本的程序 ID、说明字符串和线程模型。

当使用 ATL 添加类向导创建对象或控件时，向导将自动实现基于脚本的注册表支持并将[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)宏添加到文件中。 如果不想要支持基于脚本的注册表，则需要将此宏替换 DECLARE_REGISTRY。 DECLARE_REGISTRY 仅将上述五个基本键插入注册表中。 您必须手动编写代码以将其他键插入注册表中。

##  <a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID

指定自动注册*appid*所需的信息。

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>参数

*resid 标识*<br/>
包含*appid*相关信息的 .rgs 文件的资源 id。

*appid*<br/>
一个 GUID。

### <a name="remarks"></a>备注

使用 `CAtlModuleT`派生类中的 DECLARE_REGISTRY_APPID_RESOURCEID。

### <a name="example"></a>示例

使用 "添加类代码" 向导添加到 ATL 项目中的类将有一个使用此宏的示例。

##  <a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE

获取包含注册表文件的已命名资源，并运行该脚本，以将对象输入到系统注册表中或从系统注册表中删除对象。

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>参数

*x*<br/>
中资源的字符串标识符。

### <a name="remarks"></a>备注

当使用 ATL 项目向导创建对象或控件时，向导将自动实现基于脚本的注册表支持，并将与 DECLARE_REGISTRY_RESOURCE 类似的[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)宏添加到文件。

可以使用 ATL 注册表组件（注册器）进行静态链接，以实现优化的注册表访问。 若要以静态方式链接到注册器代码，请将以下行添加到*pch .h*文件（Visual Studio 2017 及更早版本中的*stdafx.h* ）：

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

如果希望 ATL 在运行时替换替换值，请不要指定 DECLARE_REGISTRY_RESOURCE 或 DECLARE_REGISTRY_RESOURCEID 宏。 而是创建 `_ATL_REGMAP_ENTRIES` 结构的数组，其中每个条目都包含一个与值配对的变量占位符，以便在运行时替换占位符。 然后调用[CAtlModule：： UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule：： UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)，传递数组。 这会将 `_ATL_REGMAP_ENTRIES` 结构中的所有替换值添加到注册机构的替换地图。

有关可替换参数和脚本的详细信息，请参阅[ATL 注册表组件（注册器）](../../atl/atl-registry-component-registrar.md)一文。

##  <a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID

与[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)相同，只不过它使用向导生成的 UINT 来标识资源，而不是字符串名称。

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>参数

*x*<br/>
中向导生成的资源标识符。

### <a name="remarks"></a>备注

使用 ATL 项目向导创建对象或控件时，向导将自动实现基于脚本的注册表支持并将 DECLARE_REGISTRY_RESOURCEID 宏添加到文件中。

可以使用 ATL 注册表组件（注册器）进行静态链接，以实现优化的注册表访问。 若要以静态方式链接到注册器代码，请将以下行添加到*stdafx.h*文件（Visual Studio 2019 及更高版本中的*pch* ）：

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

如果希望 ATL 在运行时替换替换值，请不要指定 DECLARE_REGISTRY_RESOURCE 或 DECLARE_REGISTRY_RESOURCEID 宏。 而是创建 `_ATL_REGMAP_ENTRIES` 结构的数组，其中每个条目都包含一个与值配对的变量占位符，以便在运行时替换占位符。 然后调用[CAtlModule：： UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule：： UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)，传递数组。 这会将 `_ATL_REGMAP_ENTRIES` 结构中的所有替换值添加到注册机构的替换地图。

有关可替换参数和脚本的详细信息，请参阅[ATL 注册表组件（注册器）](../../atl/atl-registry-component-registrar.md)一文。

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)
