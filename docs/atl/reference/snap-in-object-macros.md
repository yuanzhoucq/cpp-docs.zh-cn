---
title: 单元对象宏
ms.date: 11/04/2016
f1_keywords:
- atlsnap/ATL::BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::BEGIN_SNAPINTOOLBARID_MAP
- atlsnap/ATL::END_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::END_SNAPINTOOLBARID_MAP
- atlsnap/ATL::EXTENSION_SNAPIN_DATACLASS
- atlsnap/ATL::EXTENSION_SNAPIN_NODEINFO_ENTRY
- atlsnap/ATL::SNAPINMENUID
- atlsnap/ATL::SNAPINTOOLBARID_ENTRY
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
ms.openlocfilehash: 6a57cdb3c9b6a4448bc954ff754ac9b18fa0b393
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325862"
---
# <a name="snap-in-object-macros"></a>单元对象宏

这些宏支持卡入扩展。

|||
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|标记捕捉到对象的入网扩展数据类映射的开始。|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|标记捕捉对象工具栏映射的开头。|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|标记捕捉到对象的入网扩展数据类映射的末尾。|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|标记捕捉对象工具栏映射的末尾。|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|为管理单元扩展的数据类创建数据成员。|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|将入卡扩展数据类输入到 Snap-in 对象的入网扩展数据类映射中。|
|[斯内普努伊德](#snapinmenuid)|声明捕捉对象使用的上下文菜单的 ID。|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|将工具栏输入入卡入对象的工具栏映射中。|

## <a name="requirements"></a>要求

**标题：** atlsnap.h

## <a name="begin_extension_snapin_nodeinfo_map"></a><a name="begin_extension_snapin_nodeinfo_map"></a>BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

标记入卡扩展数据类映射的开头。

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>参数

*类名*<br/>
[在]管理单元扩展数据类的名称。

### <a name="remarks"></a>备注

使用BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP宏启动卡入扩展映射，使用[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)宏为每个卡入扩展数据类型添加条目，然后使用[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)宏完成贴图。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="begin_snapintoolbarid_map"></a><a name="begin_snapintoolbarid_map"></a>BEGIN_SNAPINTOOLBARID_MAP

声明捕捉对象工具栏 ID 映射的开头。

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>参数

*_class*<br/>
[在]指定入网对象类。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

## <a name="end_extension_snapin_nodeinfo_map"></a><a name="end_extension_snapin_nodeinfo_map"></a>END_EXTENSION_SNAPIN_NODEINFO_MAP

标记卡入扩展数据类映射的末尾。

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>备注

使用[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)宏启动卡入扩展映射，使用[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)宏为每个扩展管理单元数据类型添加条目，然后使用END_EXTENSION_SNAPIN_NODEINFO_MAP宏完成贴图。

### <a name="example"></a>示例

请参阅[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)的示例。

## <a name="end_snapintoolbarid_map"></a><a name="end_snapintoolbarid_map"></a>END_SNAPINTOOLBARID_MAP

声明捕捉对象工具栏 ID 映射的末尾。

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>参数

*_class*<br/>
[在]指定入网对象类。

### <a name="example"></a>示例

请参阅[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)的示例。

## <a name="extension_snapin_dataclass"></a><a name="extension_snapin_dataclass"></a>EXTENSION_SNAPIN_DATACLASS

将数据成员添加到**ISnapInItemImpl**派生类的入网扩展数据类。

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>参数

*数据类*<br/>
[在]管理单元扩展的数据类。

### <a name="remarks"></a>备注

此类也应输入到管理单元扩展数据类映射中。 使用[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)宏启动卡入扩展数据类映射，使用[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)宏为每个卡入扩展数据类型添加条目，以及使用[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)宏完成映射。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="extension_snapin_nodeinfo_entry"></a><a name="extension_snapin_nodeinfo_entry"></a>EXTENSION_SNAPIN_NODEINFO_ENTRY

将卡入式扩展数据类添加到卡入扩展数据类映射。

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>参数

*数据类*<br/>
[在]管理单元扩展的数据类。

### <a name="remarks"></a>备注

使用[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)宏启动卡入扩展数据类映射，使用EXTENSION_SNAPIN_NODEINFO_ENTRY宏为每个卡入扩展数据类型添加条目，然后使用[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)宏完成映射。

### <a name="example"></a>示例

请参阅[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)的示例。

## <a name="snapinmenuid"></a><a name="snapinmenuid"></a>斯内普努伊德

使用此宏可以声明 Snap-In 对象的上下文菜单资源。

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>参数

*id*<br/>
[在]标识入网对象的上下文菜单。

## <a name="snapintoolbarid_entry"></a><a name="snapintoolbarid_entry"></a>SNAPINTOOLBARID_ENTRY

使用此宏在捕捉对象的工具栏 ID 映射中输入工具栏 ID。

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>参数

*id*<br/>
[在]标识工具栏控件。

### <a name="remarks"></a>备注

BEGIN_SNAPINTOOLBARID_MAP宏标记工具栏 ID 映射的开头;如果宏[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)宏将标记工具栏 ID 映射的开头。[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)宏标记结束。

### <a name="example"></a>示例

请参阅[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)的示例。

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)
