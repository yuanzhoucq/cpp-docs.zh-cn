---
title: 分类宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 1d8bbae4608aa661bbc612604f7d85855f325f5f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321600"
---
# <a name="category-macros"></a>分类宏

这些宏定义类别映射。

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|标记类别映射的开头。|
|[END_CATEGORY_MAP](#end_category_map)|标记类别映射的末尾。|
|[IMPLEMENTED_CATEGORY](#implemented_category)|指示由 COM 对象实现的类别。|
|[REQUIRED_CATEGORY](#required_category)|指示 COM 对象需要容器的类别。|

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="begin_category_map"></a><a name="begin_category_map"></a>BEGIN_CATEGORY_MAP

标记类别映射的开头。

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>参数

*类*<br/>
[在]包含类别映射的类的名称。

### <a name="remarks"></a>备注

类别映射用于指定 COM 类将实现哪些组件类别，以及它需要从容器中实现哪些类别。

为 COM 类实现的每个类别向地图添加[IMPLEMENTED_CATEGORY](#implemented_category)条目。 为类要求其客户端实现的每个类别向地图添加[REQUIRED_CATEGORY](#required_category)项。 使用[END_CATEGORY_MAP](#end_category_map)宏标记地图的末尾。

如果类具有关联的[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO，](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)则映射中列出的组件类别将在注册模块时自动注册。

> [!NOTE]
> ATL 使用标准组件类别管理器来注册组件类别。 如果在注册模块时管理器不存在，则注册成功，但不会为该类注册组件类别。

有关组件类别的详细信息，请参阅[什么是组件类别及其](/windows/win32/com/component-categories-and-how-they-work)在 Windows SDK 中的工作方式。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="end_category_map"></a><a name="end_category_map"></a>END_CATEGORY_MAP

标记类别映射的末尾。

```
END_CATEGORY_MAP()
```

### <a name="example"></a>示例

请参阅[BEGIN_CATEGORY_MAP](#begin_category_map)的示例。

## <a name="implemented_category"></a><a name="implemented_category"></a>IMPLEMENTED_CATEGORY

向组件的[类别映射](#begin_category_map)添加IMPLEMENTED_CATEGORY宏，以指定应将其注册为实现*catID*参数标识的类别。

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>参数

*卡特ID*<br/>
[在]持有已实现类别全局唯一标识符 （GUID） 的 CATID 常量或变量。 *catID*的地址将被获取并添加到地图中。 有关股票类别的选择，请参阅下表。

### <a name="remarks"></a>备注

如果类具有关联的[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)宏，则在注册模块时，将自动注册地图中列出的组件类别。

客户端可以使用为类注册的类别信息来确定其功能和要求，而无需创建该类的实例。

有关组件类别的详细信息，请参阅[什么是组件类别及其](/windows/win32/com/component-categories-and-how-they-work)在 Windows SDK 中的工作方式。

### <a name="a-selection-of-stock-categories"></a>股票类别的选择

|说明|符号|注册处|
|-----------------|------------|-------------------|
|脚本安全|CATID_SafeForScripting|[7DD95801-9882-11CF-9FA9-00A06C42C4]|
|安全初始化|CATID_SafeForInitializing|[7DD95802-9882-11CF-9FA9-00A06C42C4]|
|简单的框架站点包含|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00A06C8166}|
|简单数据绑定|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00A06C8166}|
|高级数据绑定|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00A06C8166}|
|无窗口控件|CATID_WindowlessObject|[1D06B600-3AE3-11cf-87B9-00A06C8166]|
|互联网感知对象|有关示例列表，请参阅 Windows SDK 中的[Internet 感知对象](/windows/win32/com/internet-aware-objects)。||

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="required_category"></a><a name="required_category"></a>REQUIRED_CATEGORY

将REQUIRED_CATEGORY宏添加到组件的[类别映射](#begin_category_map)中，以指定应将其注册为需要*catID*参数标识的类别。

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>参数

*卡特ID*<br/>
[在]CATID 常量或变量，用于保存所需类别的全局唯一标识符 （GUID）。 *catID*的地址将被获取并添加到地图中。 有关股票类别的选择，请参阅下表。

### <a name="remarks"></a>备注

如果类具有关联的[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)宏，则在注册模块时，将自动注册地图中列出的组件类别。

客户端可以使用为类注册的类别信息来确定其功能和要求，而无需创建该类的实例。 例如，控件可能要求容器支持数据绑定。 容器可以通过查询该控件所需的类别管理器来了解其是否具有承载控件所需的功能。 如果容器不支持所需的功能，它可以拒绝承载 COM 对象。

有关组件类别（包括示例列表）的详细信息，请参阅[什么是组件类别及其](/windows/win32/com/component-categories-and-how-they-work)在 Windows SDK 中的工作方式。

### <a name="a-selection-of-stock-categories"></a>股票类别的选择

|说明|符号|注册处|
|-----------------|------------|-------------------|
|脚本安全|CATID_SafeForScripting|[7DD95801-9882-11CF-9FA9-00A06C42C4]|
|安全初始化|CATID_SafeForInitializing|[7DD95802-9882-11CF-9FA9-00A06C42C4]|
|简单的框架站点包含|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00A06C8166}|
|简单数据绑定|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00A06C8166}|
|高级数据绑定|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00A06C8166}|
|无窗口控件|CATID_WindowlessObject|[1D06B600-3AE3-11cf-87B9-00A06C8166]|
|互联网感知对象|有关示例列表，请参阅 Windows SDK 中的[Internet 感知对象](/windows/win32/com/internet-aware-objects)。||

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)
