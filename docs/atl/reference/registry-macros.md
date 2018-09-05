---
title: 注册表宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::_ATL_STATIC_REGISTRY
- atlcom/ATL::DECLARE_LIBID
- atlcom/ATL::DECLARE_NO_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY_APPID_RESOURCEID
- atlcom/ATL::DECLARE_REGISTRY_RESOURCE
- atlcom/ATL::DECLARE_REGISTRY_RESOURCEID
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0cf941171ef992c677c619a1c6a45ab9868526a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767951"
---
# <a name="registry-macros"></a>注册表宏

这些宏定义有用类型库和注册表功能。

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|指示您希望您的对象中要避免 atl 的依赖项的对象的注册代码DLL。|
|[DECLARE_LIBID](#declare_libid)|为 ATL 以获取提供一种*libid*的类型库。|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|避免了默认的 ATL 注册。|
|[DECLARE_REGISTRY](#declare_registry)|进入，或者在系统注册表中删除该主要对象的项。|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|指定自动注册所需的信息*appid*。|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|找到的已命名的资源并运行在其注册表脚本。|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|查找由一个 ID 号标识的资源并运行其中的注册表脚本。|  

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="_atl_static_registry"></a>  _ATL_STATIC_REGISTRY

一个表示您希望您的对象中要避免 atl 的依赖项的对象的注册代码的符号DLL。

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>备注

在定义 ATL_STATIC_REGISTRY 时，应使用以下代码：

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

##  <a name="declare_libid"></a>  DECLARE_LIBID

为 ATL 以获取提供一种*libid*的类型库。

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>参数

*libid*  
类型库的 GUID。

### <a name="remarks"></a>备注

使用中的 DECLARE_LIBID `CAtlModuleT`-派生的类。

### <a name="example"></a>示例

非特性化向导生成 ATL 项目将有一个使用此宏的示例。

##  <a name="declare_no_registry"></a>  DECLARE_NO_REGISTRY

如果您想要避免此宏会显示的类的任何默认的 ATL 注册，请使用 DECLARE_NO_REGISTRY。

```
DECLARE_NO_REGISTRY()
```

##  <a name="declare_registry"></a>  DECLARE_REGISTRY

将标准类注册输入到系统注册表或将其从系统注册表中删除。

```
DECLARE_REGISTRY(
    class, 
    pid, 
    vpid, 
    nid, 
    flags )
```

### <a name="parameters"></a>参数

*class*  
[in]包含用于向后兼容。

pid  
[in]是特定于版本的程序标识符 LPCTSTR。

*vpid*  
[in]是独立于版本的程序标识符 LPCTSTR。

*nid*  
[in]UINT，是要用作程序的说明在注册表中的资源字符串的索引。

*flags*  
[in]一个 dword 值，包含程序的注册表中的线程模型。 必须是以下值之一： THREADFLAGS_APARTMENT、 THREADFLAGS_BOTH 或 AUTPRXFLAG。

### <a name="remarks"></a>备注

标准注册包含 CLSID、 程序 ID、 独立于版本的程序 ID、 说明字符串和线程模型。

当您创建的对象或控制使用 ATL 添加类向导时，向导会自动实现基于脚本的注册表的支持并添加[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)宏为你的文件。 如果不想使用脚本基于注册表的支持，您需要替换 DECLARE_REGISTRY 为此宏。 DECLARE_REGISTRY 仅插入到注册表，上面所述的五个基本密钥。 您必须手动编写代码以插入到注册表的其他密钥。

##  <a name="declare_registry_appid_resourceid"></a>  DECLARE_REGISTRY_APPID_RESOURCEID

指定自动注册所需的信息*appid*。

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid, 
    appid )
```

### <a name="parameters"></a>参数

*resid*  
Rgs 文件包含有关的信息的资源 id *appid*。

*appid*  
一个 GUID。

### <a name="remarks"></a>备注

使用中的 DECLARE_REGISTRY_APPID_RESOURCEID `CAtlModuleT`-派生的类。

### <a name="example"></a>示例

使用添加类代码向导添加到 ATL 项目中的类将具有一个使用此宏的示例。

##  <a name="declare_registry_resource"></a>  DECLARE_REGISTRY_RESOURCE

获取包含注册表文件的命名的资源，并运行脚本以输入到系统注册表对象或从系统注册表中删除它们。

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>参数

*x*  
[in]字符串的所需的资源的标识符。

### <a name="remarks"></a>备注

当您创建的对象或控制使用 ATL 项目向导时，该向导将自动实现基于脚本的注册表的支持和添加[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)宏，类似于 DECLARE_REGISTRY_对文件的资源。

你可以以静态方式链接与 ATL 注册表组件 （注册器） 进行优化的注册表访问。 以静态方式链接到的注册机构代码，请将以下行添加到 stdafx.h 文件中：

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

如果你想要在运行时替换的替换值的 ATL，不要指定 DECLARE_REGISTRY_RESOURCE 或 DECLARE_REGISTRY_RESOURCEID 宏。 相反，创建一个数组`_ATL_REGMAP_ENTRIES`结构，其中的每个条目都包含变量的占位符的值的占位符替换为在运行时与成对出现。 然后调用[CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)，将数组传递。 这会添加所有中的替换值`_ATL_REGMAP_ENTRIES`到注册机构的替换映射的结构。  

有关可替换参数和脚本的详细信息，请参阅文章[ATL 注册表组件 （注册器）](../../atl/atl-registry-component-registrar.md)。

##  <a name="declare_registry_resourceid"></a>  DECLARE_REGISTRY_RESOURCEID

与相同[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) ，只不过它使用向导生成 UINT 来标识资源，而不是字符串名称。

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>参数

*x*  
[in]向导生成所需的资源标识符。

### <a name="remarks"></a>备注

当你创建的对象或使用 ATL 项目向导的控件时，该向导将自动实现基于脚本的注册表的支持和 DECLARE_REGISTRY_RESOURCEID 宏添加到你的文件。

你可以以静态方式链接与 ATL 注册表组件 （注册器） 进行优化的注册表访问。 以静态方式链接到的注册机构代码，请将以下行添加到 stdafx.h 文件中：

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

如果你想要在运行时替换的替换值的 ATL，不要指定 DECLARE_REGISTRY_RESOURCE 或 DECLARE_REGISTRY_RESOURCEID 宏。 相反，创建一个数组`_ATL_REGMAP_ENTRIES`结构，其中的每个条目都包含变量的占位符的值的占位符替换为在运行时与成对出现。 然后调用[CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)，将数组传递。 这会添加所有中的替换值`_ATL_REGMAP_ENTRIES`到注册机构的替换映射的结构。  

有关可替换参数和脚本的详细信息，请参阅文章[ATL 注册表组件 （注册器）](../../atl/atl-registry-component-registrar.md)。

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)
