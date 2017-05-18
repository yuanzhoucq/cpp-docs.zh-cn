---
title: "注册表宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 3a3abf5ad29b50c7f6708f02fd7c5aa193b3591c
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="registry-macros"></a>注册表宏
这些宏定义有用类型库和注册表设施。  
  
|||  
|-|-|  
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|指示您希望您的对象中的对象以避免依赖于 atl。 的注册代码DLL 中。|  
|[DECLARE_LIBID](#declare_libid)|若要获取的 ATL 为提供一种*libid*类型库。|  
|[DECLARE_NO_REGISTRY](#declare_no_registry)|避免了默认的 ATL 注册。|  
|[DECLARE_REGISTRY](#declare_registry)|进入或系统注册表中删除该主要对象的项。|  
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|指定自动注册所需的信息*appid*。|  
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|找到指定的资源并运行其中的注册表脚本。|  
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|找到一个 ID 号标识的资源并运行其中的注册表脚本。|  

## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
    
##  <a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY  
 一个表示您希望您的对象中的对象以避免依赖于 atl。 的注册代码的符号DLL 中。  
  
```
#define _ATL_STATIC_REGISTRY
```  
  
### <a name="remarks"></a>备注  
 当定义**ATL_STATIC_REGISTRY**，应使用下面的代码︰  
  
 [!code-cpp[NVC_ATL_EventHandlingSample #&5;](../../atl/codesnippet/cpp/registry-macros_1.cpp)]  
  
##  <a name="declare_libid"></a>DECLARE_LIBID  
 若要获取的 ATL 为提供一种*libid*类型库。  
  
```
DECLARE_LIBID( libid )
```  
  
### <a name="parameters"></a>参数  
 *libid*  
 类型库 GUID。  
  
### <a name="remarks"></a>备注  
 使用`DECLARE_LIBID`中`CAtlModuleT`的派生类。  
  
### <a name="example"></a>示例  
 非特性化向导生成的 ATL 项目将有一个使用此宏的示例。  
  
##  <a name="declare_no_registry"></a>DECLARE_NO_REGISTRY  
 使用`DECLARE_NO_REGISTRY`如果想要避免任何默认的 ATL 注册为此宏会出现的类。  
  
```
DECLARE_NO_REGISTRY()
```  
  
##  <a name="declare_registry"></a>DECLARE_REGISTRY  
 标准类注册进入系统注册表或将其从系统注册表中删除。  
  
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
 [in]`LPCTSTR` ，它是特定于版本的程序标识符。  
  
 *vpid*  
 [in]`LPCTSTR` ，它是一个独立于版本的程序标识符。  
  
 *nid*  
 [in]一个**UINT** ，它是注册表，以用作该程序的描述中的资源字符串的索引。  
  
 `flags`  
 [in]一个`DWORD`包含程序的线程在注册表中的模型。 必须是下列值之一︰ **THREADFLAGS_APARTMENT**， **THREADFLAGS_BOTH**，或**AUTPRXFLAG**。  
  
### <a name="remarks"></a>备注  
 标准注册组成 CLSID、 程序 ID、 版本无关的程序 ID、 描述字符串和线程模型。  
  
 当您创建的对象或控件并使用 ATL 添加类向导时，该向导自动实现基于脚本的注册表的支持，并添加[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)宏的文件。 如果不希望基于脚本的注册表的支持，则需要替换此宏并使用`DECLARE_REGISTRY`。 `DECLARE_REGISTRY`仅将插入到注册表上面所述的五个基本键。 您必须手动编写代码以插入到注册表中的其他密钥。  
  
##  <a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID  
 指定自动注册所需的信息*appid*。  
  
```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid, 
    appid )
```  
  
### <a name="parameters"></a>参数  
 *resid*  
 包含以下信息的.rgs 文件的资源 id *appid*。  
  
 *应用程序 id*  
 一个 GUID。  
  
### <a name="remarks"></a>备注  
 使用`DECLARE_REGISTRY_APPID_RESOURCEID`中`CAtlModuleT`的派生类。  
  
### <a name="example"></a>示例  
 ATL 项目，与添加类代码向导添加的类将具有一个使用此宏的示例。  
  
##  <a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE  
 获取包含此注册表文件的已命名的资源，并运行脚本以输入到系统注册表对象或从系统注册表中删除它们。  
  
```
DECLARE_REGISTRY_RESOURCE( x )
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]字符串标识符所需的资源。  
  
### <a name="remarks"></a>备注  
 当您创建的对象或控件并使用 ATL 项目向导时，向导将自动实现基于脚本的注册表的支持并添加[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)宏，这类似于`DECLARE_REGISTRY_RESOURCE`，对您的文件。  
  
 您可以以静态方式链接与 ATL 注册表组件 （注册器） 进行优化的注册表访问。 以静态方式链接到的注册器代码，请将以下行添加到 stdafx.h 文件中︰  
  
 [!code-cpp[NVC_ATL_COM&#56;](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 如果您想要在运行时替换的替换值的 ATL，则不要指定`DECLARE_REGISTRY_RESOURCE`或`DECLARE_REGISTRY_RESOURCEID`宏。 相反，创建一个数组**_ATL_REGMAP_ENTRIES**结构，其中每个条目都包含一个变量占位符与一个要在运行时替换占位符值成对出现。 然后，调用[CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)，将数组传递。 这会将所有的替换值中添加**_ATL_REGMAP_ENTRIES**到注册机构的替换映射的结构。  

  
 有关可替换参数和脚本的详细信息，请参阅文章[ATL 注册表组件 （注册器）](../../atl/atl-registry-component-registrar.md)。  
  
##  <a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID  
 与相同[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)类似，只不过它使用向导生成**UINT**来标识该资源，而不是字符串名称。  
  
```
DECLARE_REGISTRY_RESOURCEID( x )
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]向导生成所需的资源标识符。  
  
### <a name="remarks"></a>备注  
 当您创建的对象或控件并使用 ATL 项目向导时，向导将自动实现基于脚本的注册表的支持并添加`DECLARE_REGISTRY_RESOURCEID`宏的文件。  
  
 您可以以静态方式链接与 ATL 注册表组件 （注册器） 进行优化的注册表访问。 以静态方式链接到的注册器代码，请将以下行添加到 stdafx.h 文件中︰  
  
 [!code-cpp[NVC_ATL_COM&#56;](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 如果您想要在运行时替换的替换值的 ATL，则不要指定`DECLARE_REGISTRY_RESOURCE`或`DECLARE_REGISTRY_RESOURCEID`宏。 相反，创建一个数组**_ATL_REGMAP_ENTRIES**结构，其中每个条目都包含一个变量占位符与一个要在运行时替换占位符值成对出现。 然后，调用[CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)，将数组传递。 这会将所有的替换值中添加**_ATL_REGMAP_ENTRIES**到注册机构的替换映射的结构。  

  
 有关可替换参数和脚本的详细信息，请参阅文章[ATL 注册表组件 （注册器）](../../atl/atl-registry-component-registrar.md)。  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)

