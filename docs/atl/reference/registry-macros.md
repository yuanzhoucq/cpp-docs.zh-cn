---
title: 注册表宏 |Microsoft 文档
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
ms.openlocfilehash: ed9b172217f1ca7ada7d8752151126b53055df37
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365212"
---
# <a name="registry-macros"></a>注册表宏
这些宏定义有用类型库和注册表设施。  
  
|||  
|-|-|  
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|表示您希望你处于要避免依赖于 atl。 的对象的对象的注册代码DLL。|  
|[DECLARE_LIBID](#declare_libid)|若要获取的 ATL 为提供一种*libid*类型库。|  
|[DECLARE_NO_REGISTRY](#declare_no_registry)|可避免默认 ATL 注册。|  
|[DECLARE_REGISTRY](#declare_registry)|进入或在系统注册表中删除主要对象的条目。|  
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|指定自动注册所需的信息*appid*。|  
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|查找命名的资源，并运行内它的注册表脚本。|  
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|找到一个 ID 号所标识的资源并运行内它的注册表脚本。|  

## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
    
##  <a name="_atl_static_registry"></a>  _ATL_STATIC_REGISTRY  
 符号，该值指示所需的注册代码对象中的对象以避免依赖于 atl。DLL。  
  
```
#define _ATL_STATIC_REGISTRY
```  
  
### <a name="remarks"></a>备注  
 在定义**ATL_STATIC_REGISTRY**，应使用以下代码：  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]  
  
##  <a name="declare_libid"></a>  DECLARE_LIBID  
 若要获取的 ATL 为提供一种*libid*类型库。  
  
```
DECLARE_LIBID( libid )
```  
  
### <a name="parameters"></a>参数  
 *libid*  
 类型库的 GUID。  
  
### <a name="remarks"></a>备注  
 使用`DECLARE_LIBID`中`CAtlModuleT`-派生类。  
  
### <a name="example"></a>示例  
 非特性化向导生成 ATL 项目将具有使用此宏的示例。  
  
##  <a name="declare_no_registry"></a>  DECLARE_NO_REGISTRY  
 使用`DECLARE_NO_REGISTRY`如果你想要避免出现此宏的类的任何默认 ATL 注册。  
  
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
 `class`  
 [in]包括的向后兼容性。  
  
 `pid`  
 [in]`LPCTSTR` ，它是一个特定于版本的程序标识符。  
  
 *vpid*  
 [in]`LPCTSTR` ，它是一个独立于版本的程序标识符。  
  
 *nid*  
 [in]A **UINT**即注册表以用作该程序的描述中的资源字符串的索引。  
  
 `flags`  
 [in]A`DWORD`包含程序的线程在注册表中的模型。 必须是以下值之一： **THREADFLAGS_APARTMENT**， **THREADFLAGS_BOTH**，或**AUTPRXFLAG**。  
  
### <a name="remarks"></a>备注  
 标准注册组成 CLSID、 程序 ID、 独立于版本的程序 ID、 描述字符串和线程模型。  
  
 当你创建一个对象，或控制使用 ATL 添加类向导时，该向导自动实现基于脚本的注册表的支持和添加[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)宏为你的文件。 如果您不希望基于脚本的注册表支持，则需要将使用此宏`DECLARE_REGISTRY`。 `DECLARE_REGISTRY` 仅将插入到注册表上面所述的五个基本键。 你必须手动编写代码以将其他键插入到注册表。  
  
##  <a name="declare_registry_appid_resourceid"></a>  DECLARE_REGISTRY_APPID_RESOURCEID  
 指定自动注册所需的信息*appid*。  
  
```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid, 
    appid )
```  
  
### <a name="parameters"></a>参数  
 *resid*  
 .Rgs 文件包含以下信息的资源 id *appid*。  
  
 *appid*  
 一个 GUID。  
  
### <a name="remarks"></a>备注  
 使用`DECLARE_REGISTRY_APPID_RESOURCEID`中`CAtlModuleT`-派生类。  
  
### <a name="example"></a>示例  
 ATL 项目，与添加类代码向导添加的类将具有使用此宏的示例。  
  
##  <a name="declare_registry_resource"></a>  DECLARE_REGISTRY_RESOURCE  
 获取包含注册表文件的已命名的资源和运行脚本以输入系统注册表对象或从系统注册表中删除它们。  
  
```
DECLARE_REGISTRY_RESOURCE( x )
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]字符串的资源的资源的标识符。  
  
### <a name="remarks"></a>备注  
 当你创建一个对象，或控制使用 ATL 项目向导时，该向导将自动实现基于脚本的注册表的支持和添加[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)宏，类似于`DECLARE_REGISTRY_RESOURCE`到你文件。  
  
 你可以静态链接与优化的注册表访问 ATL 注册表组件 （注册器）。 若要以静态方式链接到的注册机构代码，请将以下行添加到 stdafx.h 文件：  
  
 [!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 如果你想要在运行时替换的替换值的 ATL，未指定`DECLARE_REGISTRY_RESOURCE`或`DECLARE_REGISTRY_RESOURCEID`宏。 相反，创建的数组 **_ATL_REGMAP_ENTRIES**与一个要在运行时替换占位符值成对出现的结构，其中的每个条目都包含变量的占位符。 然后调用[CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)，将数组传递。 这会将所有中的替换值添加 **_ATL_REGMAP_ENTRIES**结构到注册机构的替换映射。  

  
 有关可替换参数和脚本的详细信息，请参阅文章[ATL 注册表组件 （注册器）](../../atl/atl-registry-component-registrar.md)。  
  
##  <a name="declare_registry_resourceid"></a>  DECLARE_REGISTRY_RESOURCEID  
 与相同[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) ，只不过前者使用向导生成**UINT**来标识资源，而不是字符串名称。  
  
```
DECLARE_REGISTRY_RESOURCEID( x )
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]向导生成所需的资源标识符。  
  
### <a name="remarks"></a>备注  
 当你创建一个对象，或控制使用 ATL 项目向导时，该向导将自动实现基于脚本的注册表的支持和添加`DECLARE_REGISTRY_RESOURCEID`宏为你的文件。  
  
 你可以静态链接与优化的注册表访问 ATL 注册表组件 （注册器）。 若要以静态方式链接到的注册机构代码，请将以下行添加到 stdafx.h 文件：  
  
 [!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 如果你想要在运行时替换的替换值的 ATL，未指定`DECLARE_REGISTRY_RESOURCE`或`DECLARE_REGISTRY_RESOURCEID`宏。 相反，创建的数组 **_ATL_REGMAP_ENTRIES**与一个要在运行时替换占位符值成对出现的结构，其中的每个条目都包含变量的占位符。 然后调用[CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)，将数组传递。 这会将所有中的替换值添加 **_ATL_REGMAP_ENTRIES**结构到注册机构的替换映射。  

  
 有关可替换参数和脚本的详细信息，请参阅文章[ATL 注册表组件 （注册器）](../../atl/atl-registry-component-registrar.md)。  
  
## <a name="see-also"></a>请参阅  
 [宏](../../atl/reference/atl-macros.md)
