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
ms.openlocfilehash: 56fdb02939a99e396b9000705753e2475b80f6dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326092"
---
# <a name="property-map-macros"></a>属性映射宏

这些宏定义属性映射和条目。

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|标记 ATL 属性映射的开头。|
|[PROP_DATA_ENTRY](#prop_data_entry)|指示 ActiveX 控件的范围或尺寸。|
|[PROP_ENTRY_TYPE](#prop_entry_type)|在属性映射中输入属性说明、属性 DISPID 和属性页 CLSID。|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|在属性映射中输入属性说明、属性 DISPID、属性页`IDispatch`CLSID 和 IID。|
|[PROP_PAGE](#prop_page)|在属性映射中输入属性页 CLSID。|
|[END_PROP_MAP](#end_prop_map)|标记 ATL 属性映射的末尾。|

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="begin_prop_map"></a><a name="begin_prop_map"></a>BEGIN_PROP_MAP

标记对象属性映射的开头。

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>参数

*类*<br/>
[在]指定包含属性映射的类。

### <a name="remarks"></a>备注

属性映射存储属性描述、属性 DISPID、属性页 CLSID 和`IDispatch`ID。 类[IPerProperty 浏览](../../atl/reference/iperpropertybrowsingimpl-class.md)Impl、IPersistPropertyBagimpl、IPersistStreamInitimpl 和[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)[I指定属性PagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)使用属性映射来检索和设置此信息。 [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)

使用 ATL 项目向导创建对象时，向导将通过指定BEGIN_PROP_MAP后跟[END_PROP_MAP](#end_prop_map)创建空属性映射。

BEGIN_PROP_MAP不会保存属性映射的范围（即维度），因为使用属性映射的对象可能没有用户界面，因此它将没有范围。 如果对象是具有用户界面的 ActiveX 控件，则具有扩展区。 在这种情况下，必须在属性映射中指定[PROP_DATA_ENTRY](#prop_data_entry)以提供范围。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

## <a name="prop_data_entry"></a><a name="prop_data_entry"></a>PROP_DATA_ENTRY

指示 ActiveX 控件的范围或尺寸。

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>参数

*什德斯茨*<br/>
[在]属性描述。

*成员*<br/>
[在]包含范围的数据成员;例如， `m_sizeExtent`.

*vt*<br/>
[在]指定属性的 VARIANT 类型。

### <a name="remarks"></a>备注

此宏会导致保留指定的数据成员。

创建 ActiveX 控件时，向导在属性映射宏[BEGIN_PROP_MAP](#begin_prop_map)和属性映射宏[END_PROP_MAP](#end_prop_map)之前插入此宏。

### <a name="example"></a>示例

在下面的示例中，对象 （`m_sizeExtent`） 的范围正在持久化。

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

## <a name="prop_entry_type"></a><a name="prop_entry_type"></a>PROP_ENTRY_TYPE

使用此宏在对象的属性映射中输入属性说明、属性 DISPID 和属性页 CLSID。

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>参数

*什德斯茨*<br/>
[在]属性描述。

*不一部分*<br/>
[在]酒店的 DISPID。

*Clsid*<br/>
[在]关联属性页的 CLSID。 对于没有关联属性页的属性，请使用特殊值CLSID_NULL。

*vt*<br/>
[在]属性的类型。

### <a name="remarks"></a>备注

PROP_ENTRY宏不安全且弃用。 它已替换为PROP_ENTRY_TYPE。

[BEGIN_PROP_MAP](#begin_prop_map)宏标记属性映射的开头;[END_PROP_MAP](#end_prop_map)宏标记结束。

### <a name="example"></a>示例

请参阅[BEGIN_PROP_MAP](#begin_prop_map)的示例。

## <a name="prop_entry_type_ex"></a><a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX

与[PROP_ENTRY_TYPE](#prop_entry_type)类似 ，但允许您指定特定的 IID，如果对象支持多个双接口。

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>参数

*什德斯茨*<br/>
[在]属性描述。

*不一部分*<br/>
[在]酒店的 DISPID。

*Clsid*<br/>
[在]关联属性页的 CLSID。 对于没有关联属性页的属性，请使用特殊值CLSID_NULL。

*iidDispatch*<br/>
[在]定义属性的双接口的 IID。

*vt*<br/>
[在]属性的类型。

### <a name="remarks"></a>备注

PROP_ENTRY_EX宏不安全且弃用。 它已被替换为PROP_ENTRY_TYPE_EX。

[BEGIN_PROP_MAP](#begin_prop_map)宏标记属性映射的开头;[END_PROP_MAP](#end_prop_map)宏标记结束。

### <a name="example"></a>示例

以下示例将 条目分组`IMyDual1`，后跟`IMyDual2`的条目。 按双接口分组将提高性能。

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

## <a name="prop_page"></a><a name="prop_page"></a>PROP_PAGE

使用此宏将属性页 CLSID 输入到对象的属性映射中。

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>参数

*Clsid*<br/>
[在]属性页的 CLSID。

### <a name="remarks"></a>备注

PROP_PAGE与[PROP_ENTRY_TYPE](#prop_entry_type)类似，但不需要属性描述或 DISPID。

> [!NOTE]
> 如果您已输入具有PROP_ENTRY_TYPE或[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)的 CLSID，则无需使用PROP_PAGE进行附加条目。

[BEGIN_PROP_MAP](#begin_prop_map)宏标记属性映射的开头;[END_PROP_MAP](#end_prop_map)宏标记结束。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

## <a name="end_prop_map"></a><a name="end_prop_map"></a>END_PROP_MAP

标记对象的属性映射的末尾。

```
END_PROP_MAP()
```

### <a name="remarks"></a>备注

使用 ATL 项目向导创建对象时，向导将通过指定[BEGIN_PROP_MAP](#begin_prop_map)后跟END_PROP_MAP创建空属性映射。

### <a name="example"></a>示例

请参阅[BEGIN_PROP_MAP](#begin_prop_map)的示例。

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)
