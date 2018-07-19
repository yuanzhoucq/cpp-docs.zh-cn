---
title: 单元对象宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlsnap/ATL::BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::BEGIN_SNAPINTOOLBARID_MAP
- atlsnap/ATL::END_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::END_SNAPINTOOLBARID_MAP
- atlsnap/ATL::EXTENSION_SNAPIN_DATACLASS
- atlsnap/ATL::EXTENSION_SNAPIN_NODEINFO_ENTRY
- atlsnap/ATL::SNAPINMENUID
- atlsnap/ATL::SNAPINTOOLBARID_ENTRY
dev_langs:
- C++
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6dee93d395a86cc2c06945f9f6f1e84ced6558af
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879398"
---
# <a name="snap-in-object-macros"></a>单元对象宏
这些宏提供对管理单元中扩展的支持。  
  
|||  
|-|-|  
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|表示管理单元中对象的管理单元中扩展数据类映射的开头。|  
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|表示管理单元中对象的工具栏映射的开头。|  
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|表示管理单元中对象的管理单元中扩展数据类映射的结尾。|  
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|标记的工具栏映射的管理单元中对象的末尾。|  
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|创建管理单元中扩展的数据类的数据成员。|  
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|输入管理单元中对象的管理单元中扩展数据类映射一个管理单元中扩展的数据类。|  
|[SNAPINMENUID](#snapinmenuid)|声明上下文菜单中使用的管理单元中对象的 ID。|  
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|输入管理单元中对象的工具栏映射一个工具栏。|  

## <a name="requirements"></a>要求  
 **标头：** atlsnap.h 
   
##  <a name="begin_extension_snapin_nodeinfo_map"></a>  BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP  
 表示管理单元中扩展数据类映射的开头。  
  
```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```  
  
### <a name="parameters"></a>参数  
 classname  
 [in]管理单元中扩展数据类的名称。  
  
### <a name="remarks"></a>备注  
 管理单元中扩展映射开始 BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP 宏，您管理单元中扩展的数据类型进行的每个添加的条目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)宏，并完成对地图[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)宏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="begin_snapintoolbarid_map"></a>  BEGIN_SNAPINTOOLBARID_MAP  
 声明的工具栏 ID 映射的管理单元中对象的开头。  
  
```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```  
  
### <a name="parameters"></a>参数  
 *（_c)*  
 [in]指定管理单元中的对象类。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]  
  
##  <a name="end_extension_snapin_nodeinfo_map"></a>  END_EXTENSION_SNAPIN_NODEINFO_MAP  
 将标记扩展管理单元中的数据类映射的结尾。  
  
```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```  
  
### <a name="remarks"></a>备注  
 启动与您的管理单元扩展映射[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)宏，您的扩展管理单元中的数据类型进行的每个添加的条目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)宏，并完成与 END_EXTENSION_SNAPIN_NODEINFO_MAP 宏保持一致的映射。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)。  
  
##  <a name="end_snapintoolbarid_map"></a>  END_SNAPINTOOLBARID_MAP  
 声明的工具栏 ID 映射的管理单元中对象的末尾。  
  
```
END_SNAPINTOOLBARID_MAP( _class )
```  
  
### <a name="parameters"></a>参数  
 *（_c)*  
 [in]指定管理单元中的对象类。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)。  
  
##  <a name="extension_snapin_dataclass"></a>  EXTENSION_SNAPIN_DATACLASS  
 将数据成员添加到的管理单元中扩展数据类**ISnapInItemImpl**-派生的类。  
  
```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```  
  
### <a name="parameters"></a>参数  
 *dataClass*  
 [in]管理单元中扩展的数据类。  
  
### <a name="remarks"></a>备注  
 此类还应进入管理单元中扩展数据类映射。 启动与您的管理单元扩展数据类映射[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)宏，您管理单元中扩展的数据类型进行的每个添加的条目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)宏，并完成对地图[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)宏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="extension_snapin_nodeinfo_entry"></a>  EXTENSION_SNAPIN_NODEINFO_ENTRY  
 将一个管理单元中扩展的数据类添加到管理单元中扩展数据类映射。  
  
```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```  
  
### <a name="parameters"></a>参数  
 *dataClass*  
 [in]管理单元中扩展的数据类。  
  
### <a name="remarks"></a>备注  
 启动与您的管理单元扩展数据类映射[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)宏，将项目添加为每个管理单元中扩展数据类型与 EXTENSION_SNAPIN_NODEINFO_ENTRY 宏保持一致，并完成映射与[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)宏。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)。  
  
##  <a name="snapinmenuid"></a>  SNAPINMENUID  
 此宏用于声明管理单元中对象的上下文菜单资源。  
  
```
SNAPINMENUID( id )
```  
  
### <a name="parameters"></a>参数  
 *id*  
 [in]标识管理单元中对象的上下文菜单。  
  
##  <a name="snapintoolbarid_entry"></a>  SNAPINTOOLBARID_ENTRY  
 使用此宏管理单元中对象的工具栏 ID 映射到输入工具栏 ID。  
  
```
SNAPINTOOLBARID_ENTRY( id )
```  
  
### <a name="parameters"></a>参数  
 *id*  
 [in]标识工具栏控件。  
  
### <a name="remarks"></a>备注  
 [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)宏表示工具栏 ID 映射的开头; [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)宏标记末尾。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)。  
  
## <a name="see-also"></a>请参阅  
 [宏](../../atl/reference/atl-macros.md)
