---
title: 类别宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 411e06cc795827eef356018ba427510fd9eb7c06
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497856"
---
# <a name="category-macros"></a>类别宏

这些宏定义类别映射。

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|标记类别映射的开头。|
|[END_CATEGORY_MAP](#end_category_map)|标记类别映射的结尾。|
|[IMPLEMENTED_CATEGORY](#implemented_category)|指示 COM 对象实现的类别。|
|[REQUIRED_CATEGORY](#required_category)|指示 COM 对象所需的类别。|

## <a name="requirements"></a>要求

**标头：** atlcom。h

##  <a name="begin_category_map"></a>  BEGIN_CATEGORY_MAP

标记类别映射的开头。

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>参数

*theClass*<br/>
中包含类别映射的类的名称。

### <a name="remarks"></a>备注

类别映射用于指定 COM 类将实现的组件类别以及它需要从其容器中执行的类别。

将[IMPLEMENTED_CATEGORY](#implemented_category)条目添加到 COM 类实现的每个类别的映射。 将[REQUIRED_CATEGORY](#required_category)条目添加到类需要其客户端实现的每个类别的映射。 用[END_CATEGORY_MAP](#end_category_map)宏标记地图的结尾。

如果类具有关联的[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)，则在注册模块时将自动注册映射中列出的组件类别。

> [!NOTE]
>  ATL 使用标准组件类别管理器注册组件类别。 如果注册模块时系统中不存在管理器，则注册会成功，但不会为该类注册组件类别。

有关组件类别的详细信息，请参阅[什么是组件类别以及它们](/windows/win32/com/component-categories-and-how-they-work)在 Windows SDK 中的工作方式。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="end_category_map"></a>END_CATEGORY_MAP

标记类别映射的结尾。

```
END_CATEGORY_MAP()
```

### <a name="example"></a>示例

请参阅[BEGIN_CATEGORY_MAP](#begin_category_map)的示例。

##  <a name="implemented_category"></a>IMPLEMENTED_CATEGORY

将 IMPLEMENTED_CATEGORY 宏添加到组件的[类别映射](#begin_category_map)，以指定它应注册为实现由*catID*参数标识的类别。

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>参数

*catID*<br/>
中一个 CATID 常量或变量，保存已实现类别的全局唯一标识符（GUID）。 将采用*catID*的地址并将其添加到映射。 请参阅下表，了解所选的股票类别。

### <a name="remarks"></a>备注

如果类具有关联的[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)宏，则在注册模块时将自动注册映射中列出的组件类别。

客户端可以使用为类注册的类别信息来确定其功能和要求，而无需创建它的实例。

有关组件类别的详细信息，请参阅[什么是组件类别以及它们](/windows/win32/com/component-categories-and-how-they-work)在 Windows SDK 中的工作方式。

### <a name="a-selection-of-stock-categories"></a>股票类别的选择

|描述|符号|注册表 GUID|
|-----------------|------------|-------------------|
|脚本安全|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|初始化安全|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|简单框架网站包含|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|简单数据绑定|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|高级数据绑定|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|无窗口控件|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|识别 Internet 的对象|有关示例列表，请参阅 Windows SDK 中的 " [Internet 感知对象](/windows/win32/com/internet-aware-objects)"。||

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="required_category"></a>REQUIRED_CATEGORY

将 REQUIRED_CATEGORY 宏添加到组件的[类别映射](#begin_category_map)，以指定它应注册为需要由*catID*参数标识的类别。

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>参数

*catID*<br/>
中包含所需类别的全局唯一标识符（GUID）的 CATID 常量或变量。 将采用*catID*的地址并将其添加到映射。 请参阅下表，了解所选的股票类别。

### <a name="remarks"></a>备注

如果类具有关联的[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)宏，则在注册模块时将自动注册映射中列出的组件类别。

客户端可以使用为类注册的类别信息来确定其功能和要求，而无需创建它的实例。 例如，控件可能要求容器支持数据绑定。 容器可以通过在类别管理器中查询该控件所需的类别，来找出它是否具有宿主控件所需的功能。 如果容器不支持所需的功能，则可以拒绝承载 COM 对象。

有关组件类别的详细信息（包括示例列表），请参阅[什么是组件类别以及它们](/windows/win32/com/component-categories-and-how-they-work)在 Windows SDK 中的工作方式。

### <a name="a-selection-of-stock-categories"></a>股票类别的选择

|描述|符号|注册表 GUID|
|-----------------|------------|-------------------|
|脚本安全|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|初始化安全|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|简单框架网站包含|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|简单数据绑定|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|高级数据绑定|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|无窗口控件|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|识别 Internet 的对象|有关示例列表，请参阅 Windows SDK 中的 " [Internet 感知对象](/windows/win32/com/internet-aware-objects)"。||

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)
