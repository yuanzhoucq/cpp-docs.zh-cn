---
title: "管理单元中对象宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
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
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 13823feb06e7fecb2e81a01f3c88e3664de01d30
ms.lasthandoff: 02/24/2017

---
# <a name="snap-in-object-macros"></a>管理单元对象宏
这些宏提供对管理单元扩展支持。  
  
|||  
|-|-|  
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|标记管理单元中对象的管理单元扩展数据类映射的开头。|  
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|标记的工具栏上映射的管理单元中对象的开始。|  
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|标记管理单元中对象的管理单元扩展数据类映射的结尾。|  
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|标记的工具栏上映射的管理单元中对象的末尾。|  
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|创建管理单元扩展的数据类的数据成员。|  
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|将在管理单元中对象的管理单元扩展数据类映射输入管理单元扩展数据类。|  
|[SNAPINMENUID](#snapinmenuid)|声明上下文菜单中使用的管理单元中对象的 ID。|  
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|到工具栏映射中的管理单元对象将进入一个工具栏。|  

## <a name="requirements"></a>要求  
 **标头︰** atlsnap.h 
   
##  <a name="a-namebeginextensionsnapinnodeinfomapa--beginextensionsnapinnodeinfomap"></a><a name="begin_extension_snapin_nodeinfo_map"></a>BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP  
 标记管理单元扩展数据类映射的开头。  
  
```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```  
  
### <a name="parameters"></a>参数  
 *类名*  
 [in]管理单元扩展数据类的名称。  
  
### <a name="remarks"></a>备注  
 启动与您的管理单元扩展映射`BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP`宏，您的管理单元扩展数据类型进行的每个添加条目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)宏，并完成用映射[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)宏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&105;](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="a-namebeginsnapintoolbaridmapa--beginsnapintoolbaridmap"></a><a name="begin_snapintoolbarid_map"></a>BEGIN_SNAPINTOOLBARID_MAP  
 声明的工具栏 ID 映射的管理单元中对象的开头。  
  
```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```  
  
### <a name="parameters"></a>参数  
 `_class`  
 [in]指定管理单元中的对象类。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&106;](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]  
  
##  <a name="a-nameendextensionsnapinnodeinfomapa--endextensionsnapinnodeinfomap"></a><a name="end_extension_snapin_nodeinfo_map"></a>END_EXTENSION_SNAPIN_NODEINFO_MAP  
 标记管理单元扩展数据类映射的结尾。  
  
```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```  
  
### <a name="remarks"></a>备注  
 启动与您的管理单元扩展映射[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)宏，您的扩展管理单元中的数据类型进行的每个添加的条目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)宏，并完成用映射`END_EXTENSION_SNAPIN_NODEINFO_MAP`宏。  
  
### <a name="example"></a>示例  
 请参阅示例[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)。  
  
##  <a name="a-nameendsnapintoolbaridmapa--endsnapintoolbaridmap"></a><a name="end_snapintoolbarid_map"></a>END_SNAPINTOOLBARID_MAP  
 声明的工具栏 ID 映射的管理单元中对象的末尾。  
  
```
END_SNAPINTOOLBARID_MAP( _class )
```  
  
### <a name="parameters"></a>参数  
 `_class`  
 [in]指定管理单元中的对象类。  
  
### <a name="example"></a>示例  
 请参阅示例[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)。  
  
##  <a name="a-nameextensionsnapindataclassa--extensionsnapindataclass"></a><a name="extension_snapin_dataclass"></a>EXTENSION_SNAPIN_DATACLASS  
 将数据成员添加到的管理单元扩展数据类**ISnapInItemImpl**的派生类。  
  
```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```  
  
### <a name="parameters"></a>参数  
 `dataClass`  
 [in]管理单元扩展的数据类。  
  
### <a name="remarks"></a>备注  
 此类还应进入管理单元扩展数据类映射。 启动与您的管理单元扩展数据类映射[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)宏，您的管理单元扩展数据类型进行的每个添加条目[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)宏，并完成用映射[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)宏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&105;](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]  
  
##  <a name="a-nameextensionsnapinnodeinfoentrya--extensionsnapinnodeinfoentry"></a><a name="extension_snapin_nodeinfo_entry"></a>EXTENSION_SNAPIN_NODEINFO_ENTRY  
 向管理单元扩展数据类图中添加管理单元扩展数据类。  
  
```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```  
  
### <a name="parameters"></a>参数  
 `dataClass`  
 [in]管理单元扩展的数据类。  
  
### <a name="remarks"></a>备注  
 启动与您的管理单元扩展数据类映射[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)宏，您的管理单元扩展数据类型进行的每个添加条目`EXTENSION_SNAPIN_NODEINFO_ENTRY`宏，并完成用映射[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)宏。  
  
### <a name="example"></a>示例  
 请参阅示例[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)。  
  
##  <a name="a-namesnapinmenuida--snapinmenuid"></a><a name="snapinmenuid"></a>SNAPINMENUID  
 此宏用于声明管理单元中对象的上下文菜单资源。  
  
```
SNAPINMENUID( id )
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]标识管理单元中对象的上下文菜单。  
  
##  <a name="a-namesnapintoolbaridentrya--snapintoolbaridentry"></a><a name="snapintoolbarid_entry"></a>SNAPINTOOLBARID_ENTRY  
 使用此宏来管理单元中对象的工具栏 ID 映射到输入工具栏 ID。  
  
```
SNAPINTOOLBARID_ENTRY( id )
```  
  
### <a name="parameters"></a>参数  
 `id`  
 [in]确定工具栏控件。  
  
### <a name="remarks"></a>备注  
 [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)宏标记开头的工具栏 ID 映射; [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)宏标记的末尾。  
  
### <a name="example"></a>示例  
 请参阅示例[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)。  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)

