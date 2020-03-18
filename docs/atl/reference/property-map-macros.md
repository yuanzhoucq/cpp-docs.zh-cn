---
title: 属性映射宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
ms.openlocfilehash: 1e2e7235dd924467d9d5e0613a704fedf8340ae4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422972"
---
# <a name="property-map-macros"></a>属性映射宏

这些宏定义属性映射和条目。

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|标记 ATL 属性映射的开头。|
|[PROP_DATA_ENTRY](#prop_data_entry)|指示 ActiveX 控件的范围或维度。|
|[PROP_ENTRY_TYPE](#prop_entry_type)|在属性映射中输入属性说明、属性 DISPID 和属性页 CLSID。|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|在属性映射中输入属性说明、属性 DISPID、属性页 CLSID 和 `IDispatch` IID。|
|[PROP_PAGE](#prop_page)|在属性映射中输入属性页 CLSID。|
|[END_PROP_MAP](#end_prop_map)|标记 ATL 属性映射的结尾。|

## <a name="requirements"></a>要求

**标头：** atlcom。h

##  <a name="begin_prop_map"></a>BEGIN_PROP_MAP

标记对象的属性映射的开头。

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>parameters

*类*<br/>
中指定包含属性映射的类。

### <a name="remarks"></a>备注

属性映射存储属性说明、属性 Dispid、属性页 Clsid 和 `IDispatch` Iid。 类[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)、 [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)、 [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)和[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)使用属性映射来检索和设置此信息。

使用 ATL 项目向导创建对象时，向导将通过指定 BEGIN_PROP_MAP 后跟[END_PROP_MAP](#end_prop_map)来创建一个空属性映射。

BEGIN_PROP_MAP 不会保存属性映射的范围（即维度），因为使用属性映射的对象可能没有用户界面，因此不会有任何范围。 如果对象是具有用户界面的 ActiveX 控件，则它具有范围。 在这种情况下，你必须在属性映射中指定[PROP_DATA_ENTRY](#prop_data_entry)以提供范围。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

##  <a name="prop_data_entry"></a>PROP_DATA_ENTRY

指示 ActiveX 控件的范围或维度。

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>parameters

*szDesc*<br/>
中属性说明。

*member*<br/>
中包含该范围的数据成员;例如，`m_sizeExtent`。

*vt*<br/>
中指定属性的变量类型。

### <a name="remarks"></a>备注

此宏会使指定的数据成员得以保留。

创建 ActiveX 控件时，向导会在属性映射宏之后[BEGIN_PROP_MAP](#begin_prop_map)和属性映射宏[END_PROP_MAP](#end_prop_map)之前插入此宏。

### <a name="example"></a>示例

在下面的示例中，将持久保存对象的范围（`m_sizeExtent`）。

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

##  <a name="prop_entry_type"></a>PROP_ENTRY_TYPE

使用此宏可在对象的属性映射中输入属性说明、属性 DISPID 和属性页 CLSID。

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>parameters

*szDesc*<br/>
中属性说明。

*dispid*<br/>
中属性的 DISPID。

*clsid*<br/>
中关联属性页的 CLSID。 对于没有关联属性页的属性，请使用特殊值 CLSID_NULL。

*vt*<br/>
中属性的类型。

### <a name="remarks"></a>备注

PROP_ENTRY 宏不安全且已弃用。 它已替换为 PROP_ENTRY_TYPE。

[BEGIN_PROP_MAP](#begin_prop_map)宏标记属性映射的开头;[END_PROP_MAP](#end_prop_map)宏标记结尾。

### <a name="example"></a>示例

请参阅[BEGIN_PROP_MAP](#begin_prop_map)的示例。

##  <a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX

与[PROP_ENTRY_TYPE](#prop_entry_type)类似，但如果对象支持多个双重接口，则允许指定特定 IID。

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>parameters

*szDesc*<br/>
中属性说明。

*dispid*<br/>
中属性的 DISPID。

*clsid*<br/>
中关联属性页的 CLSID。 对于没有关联属性页的属性，请使用特殊值 CLSID_NULL。

*iidDispatch*<br/>
中定义属性的双重接口的 IID。

*vt*<br/>
中属性的类型。

### <a name="remarks"></a>备注

PROP_ENTRY_EX 宏不安全且已弃用。 它已替换为 PROP_ENTRY_TYPE_EX。

[BEGIN_PROP_MAP](#begin_prop_map)宏标记属性映射的开头;[END_PROP_MAP](#end_prop_map)宏标记结尾。

### <a name="example"></a>示例

下面的示例将 `IMyDual1` 后跟 `IMyDual2`条目的条目分组。 按双重接口分组将提高性能。

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

##  <a name="prop_page"></a>PROP_PAGE

使用此宏在对象的属性映射中输入属性页 CLSID。

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>parameters

*clsid*<br/>
中属性页的 CLSID。

### <a name="remarks"></a>备注

PROP_PAGE 类似于[PROP_ENTRY_TYPE](#prop_entry_type)，但不需要属性说明或 DISPID。

> [!NOTE]
>  如果已输入 PROP_ENTRY_TYPE 或[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)的 CLSID，则不需要使用 PROP_PAGE 创建附加条目。

[BEGIN_PROP_MAP](#begin_prop_map)宏标记属性映射的开头;[END_PROP_MAP](#end_prop_map)宏标记结尾。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

##  <a name="end_prop_map"></a>END_PROP_MAP

标记对象的属性映射的结尾。

```
END_PROP_MAP()
```

### <a name="remarks"></a>备注

使用 ATL 项目向导创建对象时，向导将通过指定[BEGIN_PROP_MAP](#begin_prop_map)后跟 END_PROP_MAP 来创建一个空属性映射。

### <a name="example"></a>示例

请参阅[BEGIN_PROP_MAP](#begin_prop_map)的示例。

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)
