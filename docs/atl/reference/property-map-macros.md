---
title: "属性映射宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dfd99fa59fc5e1d97011ac3dba4d16dd222c35b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="property-map-macros"></a>属性映射宏
这些宏定义属性映射和条目。  
  
|||  
|-|-|  
|[BEGIN_PROP_MAP](#begin_prop_map)|标记 ATL 属性映射的开始。|  
|[PROP_DATA_ENTRY](#prop_data_entry)|指示的范围内或维度，ActiveX 控件。|  
|[PROP_ENTRY_TYPE](#prop_entry_type)|输入属性映射属性说明、 属性 DISPID，和属性页的 CLSID。|  
|[改用 PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|输入的属性说明，属性 DISPID，属性页 CLSID，和`IDispatch`属性映射到的 IID。|  
|[PROP_PAGE](#prop_page)|输入属性映射属性页的 CLSID。|  
|[END_PROP_MAP](#end_prop_map)|将标记 ATL 属性映射的末尾。|  

## <a name="requirements"></a>惠?  
 **标头：** atlcom.h  
   
##  <a name="begin_prop_map"></a>BEGIN_PROP_MAP  
 标记对象的属性映射的开始。  
  
```
BEGIN_PROP_MAP(theClass)
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 [in]指定包含属性映射的类。  
  
### <a name="remarks"></a>备注  
 属性映射存储属性 Dispid，属性页 Clsid 的属性描述和`IDispatch`Iid。 类[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)， [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)， [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)，和[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)属性映射用于检索和设置此信息。  
  
 当使用 ATL 项目向导创建对象时，向导将创建的空属性映射，通过指定`BEGIN_PROP_MAP`跟[END_PROP_MAP](#end_prop_map)。  
  
 `BEGIN_PROP_MAP`不保存出的属性映射，程度 （维度），因为使用属性映射的对象可能没有用户界面，使其将不包含任何扩展盘区。 如果对象是具有用户界面的 ActiveX 控件，它具有扩展盘区。 在这种情况下，必须指定[PROP_DATA_ENTRY](#prop_data_entry)属性映射提供范围中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]  
  
##  <a name="prop_data_entry"></a>PROP_DATA_ENTRY  
 指示的范围内或维度，ActiveX 控件。  
  
```
PROP_DATA_ENTRY( szDesc, member, vt)
```    
  
### <a name="parameters"></a>参数  
 `szDesc`  
 [in]属性说明中。  
  
 `member`  
 [in]包含范围; 数据成员例如， `m_sizeExtent`。  
  
 *vt*  
 [in]指定的属性的变体类型。  
  
### <a name="remarks"></a>备注  
 此宏会导致要保留的指定的数据成员。  
  
 在创建 ActiveX 控件时，向导会将此宏插入之后属性映射宏[BEGIN_PROP_MAP](#begin_prop_map)和属性映射宏之前[END_PROP_MAP](#end_prop_map)。  
  
### <a name="example"></a>示例  
 在下面的示例中，该对象的范围 ( `m_sizeExtent`) 正在保持不变。  
  
 [!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]  
  
##  <a name="prop_entry_type"></a>PROP_ENTRY_TYPE  
 使用此宏若要输入对象的属性映射到的属性说明、 属性 DISPID，和属性页的 CLSID。  
  
```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```  
  
### <a name="parameters"></a>参数  
 `szDesc`  
 [in]属性说明中。  
  
 `dispid`  
 [in]该属性的 DISPID。  
  
 `clsid`  
 [in]关联的属性页的 CLSID。 使用特殊值`CLSID_NULL`没有关联的属性页的属性。  
  
 `vt`  
 [in]该属性的类型。  
  
### <a name="remarks"></a>备注  
 `PROP_ENTRY`宏是不安全的和已弃用。 它已替换`PROP_ENTRY_TYPE`。  
  
 [BEGIN_PROP_MAP](#begin_prop_map)宏标记的属性映射开始; [END_PROP_MAP](#end_prop_map)宏标记的结束。  
  
### <a name="example"></a>示例  
 请参阅示例[BEGIN_PROP_MAP](#begin_prop_map)。  
  
##  <a name="prop_entry_type_ex"></a>改用 PROP_ENTRY_TYPE_EX  
 类似于[PROP_ENTRY_TYPE](#prop_entry_type)，但允许你指定特定的 IID，如果你的对象支持多个双重接口。  
  
```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```    
  
### <a name="parameters"></a>参数  
 `szDesc`  
 [in]属性说明中。  
  
 `dispid`  
 [in]该属性的 DISPID。  
  
 `clsid`  
 [in]关联的属性页的 CLSID。 使用特殊值`CLSID_NULL`没有关联的属性页的属性。  
  
 `iidDispatch`  
 [in]定义属性的双重接口的 IID。  
  
 `vt`  
 [in]该属性的类型。  
  
### <a name="remarks"></a>备注  
 `PROP_ENTRY_EX`宏是不安全的和已弃用。 它已替换`PROP_ENTRY_TYPE_EX`。  
  
 [BEGIN_PROP_MAP](#begin_prop_map)宏标记的属性映射开始; [END_PROP_MAP](#end_prop_map)宏标记的结束。  
  
### <a name="example"></a>示例  
 下面的示例进行分组的条目`IMyDual1`跟的条目`IMyDual2`。 双重接口通过分组将提高性能。  
  
 [!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]  
  
##  <a name="prop_page"></a>PROP_PAGE  
 使用此宏若要输入对象的属性映射到的属性页 CLSID。  
  
```
PROP_PAGE(clsid)
```  
  
### <a name="parameters"></a>参数  
 `clsid`  
 [in]属性页的 CLSID。  
  
### <a name="remarks"></a>备注  
 `PROP_PAGE`类似于[PROP_ENTRY_TYPE](#prop_entry_type)，但不需要的属性说明或 DISPID。  
  
> [!NOTE]
>  如果你已经输入与 CLSID`PROP_ENTRY_TYPE`或[改用 PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)，不需要与其他输入`PROP_PAGE`。  
  
 [BEGIN_PROP_MAP](#begin_prop_map)宏标记的属性映射开始; [END_PROP_MAP](#end_prop_map)宏标记的结束。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]  
  
##  <a name="end_prop_map"></a>END_PROP_MAP  
 将标记对象的属性映射的末尾。  
  
```
END_PROP_MAP()
```  
  
### <a name="remarks"></a>备注  
 当使用 ATL 项目向导创建对象时，向导将创建的空属性映射，通过指定[BEGIN_PROP_MAP](#begin_prop_map)跟`END_PROP_MAP`。  
  
### <a name="example"></a>示例  
 请参阅示例[BEGIN_PROP_MAP](#begin_prop_map)。  
  
## <a name="see-also"></a>请参阅  
 [宏](../../atl/reference/atl-macros.md)
