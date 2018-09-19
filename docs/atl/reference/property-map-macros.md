---
title: 属性映射宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
dev_langs:
- C++
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 594b02d777d87decfc218064678dbecdf8ecf0c9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106345"
---
# <a name="property-map-macros"></a>属性映射宏

这些宏定义属性映射和条目。

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|表示 ATL 属性映射的开头。|
|[PROP_DATA_ENTRY](#prop_data_entry)|指示范围内或维度，ActiveX 控件。|
|[PROP_ENTRY_TYPE](#prop_entry_type)|输入属性映射的属性说明、 属性的 DISPID，和属性页 CLSID。|
|[改用 PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|输入的属性说明，属性的 DISPID，CLSID 的属性页和`IDispatch`属性映射到 IID。|
|[PROP_PAGE](#prop_page)|输入属性映射的属性页 CLSID。|
|[END_PROP_MAP](#end_prop_map)|将标记 ATL 属性映射的结尾。|  

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="begin_prop_map"></a>  BEGIN_PROP_MAP

表示对象的属性映射的开头。

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>参数

*类*<br/>
[in]指定包含该属性映射的类。

### <a name="remarks"></a>备注

属性映射将存储的属性说明，属性 Dispid，Clsid 的属性页和`IDispatch`Iid。 类[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)， [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)， [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)，和[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)属性映射用于检索和设置此信息。

当使用 ATL 项目向导创建一个对象时，该向导将通过指定 BEGIN_PROP_MAP 跟创建空属性映射[END_PROP_MAP](#end_prop_map)。

BEGIN_PROP_MAP 不保存出程度 （维度） 的属性映射，因为使用属性映射的对象可能没有用户界面，因此它必须无盘区。 如果对象是使用用户界面的 ActiveX 控件，它具有某个扩展盘区。 在这种情况下，必须指定[PROP_DATA_ENTRY](#prop_data_entry)属性映射可提供此盘区中。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

##  <a name="prop_data_entry"></a>  PROP_DATA_ENTRY

指示范围内或维度，ActiveX 控件。

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>参数

*szDesc*<br/>
[in]属性说明。

*成员*<br/>
[in]包含范围; 数据成员例如， `m_sizeExtent`。

*vt*<br/>
[in]指定属性的变体类型。

### <a name="remarks"></a>备注

此宏会导致要保留的指定的数据成员。

该向导创建的 ActiveX 控件时，属性映射宏后插入此宏[BEGIN_PROP_MAP](#begin_prop_map)和属性映射宏之前[END_PROP_MAP](#end_prop_map)。

### <a name="example"></a>示例

在下面的示例，该对象的范围 (`m_sizeExtent`) 正在保持不变。

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

##  <a name="prop_entry_type"></a>  PROP_ENTRY_TYPE

使用此宏对象的属性映射到输入的属性说明、 属性的 DISPID，和属性页 CLSID。

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>参数

*szDesc*<br/>
[in]属性说明。

*dispid*<br/>
[in]该属性的 DISPID。

*clsid*<br/>
[in]关联的属性页的 CLSID。 不具有关联的属性页的属性使用特殊值 CLSID_NULL。

*vt*<br/>
[in]属性的类型。

### <a name="remarks"></a>备注

PROP_ENTRY 宏是不安全，不推荐使用。 它已替换 PROP_ENTRY_TYPE。

[BEGIN_PROP_MAP](#begin_prop_map)宏表示的属性映射的开头; [END_PROP_MAP](#end_prop_map)宏标记末尾。

### <a name="example"></a>示例

有关示例，请参阅[BEGIN_PROP_MAP](#begin_prop_map)。

##  <a name="prop_entry_type_ex"></a>  改用 PROP_ENTRY_TYPE_EX

类似于[PROP_ENTRY_TYPE](#prop_entry_type)，但允许你指定某个特定 IID，如果您的对象支持多个双重接口。

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>参数

*szDesc*<br/>
[in]属性说明。

*dispid*<br/>
[in]该属性的 DISPID。

*clsid*<br/>
[in]关联的属性页的 CLSID。 不具有关联的属性页的属性使用特殊值 CLSID_NULL。

*iidDispatch*<br/>
[in]将属性定义的双重接口的 IID。

*vt*<br/>
[in]属性的类型。

### <a name="remarks"></a>备注

PROP_ENTRY_EX 宏是不安全，不推荐使用。 它已替换改用 PROP_ENTRY_TYPE_EX。

[BEGIN_PROP_MAP](#begin_prop_map)宏表示的属性映射的开头; [END_PROP_MAP](#end_prop_map)宏标记末尾。

### <a name="example"></a>示例

下面的示例进行分组的条目`IMyDual1`的条目后跟`IMyDual2`。 双重接口通过分组会提高性能。

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

##  <a name="prop_page"></a>  PROP_PAGE

使用此宏输入对象的属性映射到属性页 CLSID。

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>参数

*clsid*<br/>
[in]属性页的 CLSID。

### <a name="remarks"></a>备注

PROP_PAGE 是类似于[PROP_ENTRY_TYPE](#prop_entry_type)，但不需要的属性说明或 DISPID。

> [!NOTE]
>  如果您已经输入与 PROP_ENTRY_TYPE CLSID 或[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)，不需要生成与 PROP_PAGE 其他条目。

[BEGIN_PROP_MAP](#begin_prop_map)宏表示的属性映射的开头; [END_PROP_MAP](#end_prop_map)宏标记末尾。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

##  <a name="end_prop_map"></a>  END_PROP_MAP

表示对象的属性映射的结尾。

```
END_PROP_MAP()
```

### <a name="remarks"></a>备注

当使用 ATL 项目向导创建一个对象时，该向导将通过指定创建空属性映射[BEGIN_PROP_MAP](#begin_prop_map)跟 END_PROP_MAP。

### <a name="example"></a>示例

有关示例，请参阅[BEGIN_PROP_MAP](#begin_prop_map)。

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)
