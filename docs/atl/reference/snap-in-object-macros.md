---
title: "管理单元中对象宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 111fb83ed0eaae936dfa38d7047b2a0c2fb2443b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="snap-in-object-macros"></a>管理单元中对象宏
这些宏提供对管理单元中扩展的支持。  
  
|||  
|-|-|  
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|标记管理单元中对象的管理单元扩展数据类映射的开始。|  
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|标记管理单元中对象的工具栏映射的开始。|  
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|将标记的管理单元中对象的管理单元扩展数据类映射的末尾。|  
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|将标记的管理单元中对象的工具栏映射的末尾。|  
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|创建管理单元扩展的数据类的数据成员。|  
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|输入管理单元中对象的管理单元扩展数据类映射一个管理单元扩展的数据类。|  
|[SNAPINMENUID](#snapinmenuid)|声明上下文菜单中使用的管理单元中对象的 ID。|  
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|输入管理单元中对象的工具栏映射工具栏。|  

## <a name="requirements"></a>惠?  
 **标头：** atlsnap.h 
   
##  <a name="begin_extension_snapin_nodeinfo_map"></a>BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP  
 标记管理单元扩展数据类映射的开始。  
  
```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```  
  
### <a name="parameters"></a>参数  
 classname  
 [in]管理单元扩展数据类的名称。  
  
### <a name="remarks"></a>备注  
 启动与你管理单元扩展映射`BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP`宏，为每个您管理单元扩展的数据类型进行添加条目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)宏，并完成对地图[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)宏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="begin_snapintoolbarid_map"></a>BEGIN_SNAPINTOOLBARID_MAP  
 声明的管理单元中对象的工具栏 ID 映射的开头。  
  
```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```  
  
### <a name="parameters"></a>参数  
 `_class`  
 [in]指定的管理单元对象类。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]  
  
##  <a name="end_extension_snapin_nodeinfo_map"></a>END_EXTENSION_SNAPIN_NODEINFO_MAP  
 将标记管理单元扩展数据类映射的末尾。  
  
```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```  
  
### <a name="remarks"></a>备注  
 启动与你管理单元扩展映射[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)宏，为每个您扩展的管理单元中数据类型进行添加条目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)宏，并完成对地图`END_EXTENSION_SNAPIN_NODEINFO_MAP`宏。  
  
### <a name="example"></a>示例  
 请参阅示例[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)。  
  
##  <a name="end_snapintoolbarid_map"></a>END_SNAPINTOOLBARID_MAP  
 声明的管理单元中对象的工具栏 ID 映射的末尾。  
  
```
END_SNAPINTOOLBARID_MAP( _class )
```  
  
### <a name="parameters"></a>参数  
 `_class`  
 [in]指定的管理单元对象类。  
  
### <a name="example"></a>示例  
 请参阅示例[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)。  
  
##  <a name="extension_snapin_dataclass"></a>EXTENSION_SNAPIN_DATACLASS  
 将数据成员添加到的管理单元扩展数据类**ISnapInItemImpl**-派生类。  
  
```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```  
  
### <a name="parameters"></a>参数  
 `dataClass`  
 [in]管理单元扩展的数据类。  
  
### <a name="remarks"></a>备注  
 此类还应进入管理单元扩展数据类映射。 启动与你管理单元扩展数据类映射[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)宏，为每个您管理单元扩展的数据类型进行添加条目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)宏，并完成对地图[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)宏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="extension_snapin_nodeinfo_entry"></a>EXTENSION_SNAPIN_NODEINFO_ENTRY  
 将管理单元扩展数据类添加到管理单元扩展数据类映射。  
  
```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```  
  
### <a name="parameters"></a>参数  
 `dataClass`  
 [in]管理单元扩展的数据类。  
  
### <a name="remarks"></a>备注  
 启动与你管理单元扩展数据类映射[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)宏，为每个您管理单元扩展的数据类型进行添加条目`EXTENSION_SNAPIN_NODEINFO_ENTRY`宏，并完成用映射[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)宏。  
  
### <a name="example"></a>示例  
 请参阅示例[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)。  
  
##  <a name="snapinmenuid"></a>SNAPINMENUID  
 使用此宏来声明的管理单元中对象的上下文菜单资源。  
  
```
SNAPINMENUID( id )
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]标识管理单元中对象的上下文菜单。  
  
##  <a name="snapintoolbarid_entry"></a>SNAPINTOOLBARID_ENTRY  
 使用此宏管理单元中对象的工具栏 ID 映射到输入工具栏 ID。  
  
```
SNAPINTOOLBARID_ENTRY( id )
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]标识工具栏控件。  
  
### <a name="remarks"></a>备注  
 [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)宏标记的工具栏 ID 映射开始; [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)宏标记的结束。  
  
### <a name="example"></a>示例  
 请参阅示例[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)。  
  
## <a name="see-also"></a>请参阅  
 [宏](../../atl/reference/atl-macros.md)
