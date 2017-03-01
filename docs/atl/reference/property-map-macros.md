---
title: "属性映射宏 |Microsoft 文档"
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
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
caps.latest.revision: 17
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
ms.openlocfilehash: fbbed22766f9029456f15c4a554ae91322e6a275
ms.lasthandoff: 02/24/2017

---
# <a name="property-map-macros"></a>属性映射宏
这些宏定义属性映射和条目。  
  
|||  
|-|-|  
|[BEGIN_PROP_MAP](#begin_prop_map)|标记开始 ATL 属性映射。|  
|[PROP_DATA_ENTRY](#prop_data_entry)|指示范围内或维度，ActiveX 控件。|  
|[PROP_ENTRY_TYPE](#prop_entry_type)|属性描述、 DISPID，属性和属性页 CLSID 进入属性映射。|  
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|输入的属性说明，DISPID，属性页 CLSID、 属性和`IDispatch`属性映射到 IID。|  
|[PROP_PAGE](#prop_page)|属性页 CLSID 进入属性映射。|  
|[END_PROP_MAP](#end_prop_map)|将标记 ATL 属性映射的结尾。|  

## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
   
##  <a name="a-namebeginpropmapa--beginpropmap"></a><a name="begin_prop_map"></a>BEGIN_PROP_MAP  
 标记对象的属性映射的开始。  
  
```
BEGIN_PROP_MAP(theClass)
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 [in]指定包含该属性映射的类。  
  
### <a name="remarks"></a>备注  
 属性映射存储属性说明，属性 Dispid，属性页的 Clsid，和`IDispatch`Iid。 类[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)， [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)， [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)，和[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)属性映射用于检索和设置此信息。  
  
 当使用 ATL 项目向导创建一个对象时，该向导将创建空属性映射，通过指定`BEGIN_PROP_MAP`跟[END_PROP_MAP](#end_prop_map)。  
  
 `BEGIN_PROP_MAP`不会保存出属性映射的程度 （维度），因为使用属性映射的对象可能没有用户界面，因此它必须没有扩展盘区。 如果对象是具有用户界面的 ActiveX 控件，则必须扩展盘区。 在这种情况下，必须指定[PROP_DATA_ENTRY](#prop_data_entry)属性映射提供此扩展盘区中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&103;](../../atl/codesnippet/cpp/property-map-macros_1.h)]  
  
##  <a name="a-namepropdataentrya--propdataentry"></a><a name="prop_data_entry"></a>PROP_DATA_ENTRY  
 指示范围内或维度，ActiveX 控件。  
  
```
PROP_DATA_ENTRY( szDesc, member, vt)
```    
  
### <a name="parameters"></a>参数  
 `szDesc`  
 [in]属性说明。  
  
 `member`  
 [in]包含此扩展盘区; 的数据成员例如， `m_sizeExtent`。  
  
 *vt*  
 [in]指定该属性的变体类型。  
  
### <a name="remarks"></a>备注  
 此宏会导致要保留的指定的数据成员。  
  
 在创建 ActiveX 控件时，该向导会将此宏插入之后属性映射宏[BEGIN_PROP_MAP](#begin_prop_map)和属性映射宏之前[END_PROP_MAP](#end_prop_map)。  
  
### <a name="example"></a>示例  
 在下面的示例中，对象的范围 ( `m_sizeExtent`) 正在保持不变。  
  
 [!code-cpp[NVC_ATL_Windowing #&131;](../../atl/codesnippet/cpp/property-map-macros_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing #&132;](../../atl/codesnippet/cpp/property-map-macros_3.h)]  
  
##  <a name="a-namepropentrytypea--propentrytype"></a><a name="prop_entry_type"></a>PROP_ENTRY_TYPE  
 使用此宏的属性描述、 DISPID，属性和属性页 CLSID 进入对象的属性映射。  
  
```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```  
  
### <a name="parameters"></a>参数  
 `szDesc`  
 [in]属性说明。  
  
 `dispid`  
 [in]该属性的 DISPID。  
  
 `clsid`  
 [in]关联的属性页上的 CLSID。 使用特殊值`CLSID_NULL`不具有关联的属性页的属性。  
  
 `vt`  
 [in]该属性的类型。  
  
### <a name="remarks"></a>备注  
 `PROP_ENTRY`宏是不安全，而且不推荐使用。 已经替换为`PROP_ENTRY_TYPE`。  
  
 [BEGIN_PROP_MAP](#begin_prop_map)宏标记开头的属性映射; [END_PROP_MAP](#end_prop_map)宏标记的末尾。  
  
### <a name="example"></a>示例  
 请参阅示例[BEGIN_PROP_MAP](#begin_prop_map)。  
  
##  <a name="a-namepropentrytypeexa--propentrytypeex"></a><a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX  
 类似于[PROP_ENTRY_TYPE](#prop_entry_type)，但允许您指定特定的 IID，如果您的对象支持多个双重接口。  
  
```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```    
  
### <a name="parameters"></a>参数  
 `szDesc`  
 [in]属性说明。  
  
 `dispid`  
 [in]该属性的 DISPID。  
  
 `clsid`  
 [in]关联的属性页上的 CLSID。 使用特殊值`CLSID_NULL`不具有关联的属性页的属性。  
  
 `iidDispatch`  
 [in]定义属性的双重接口的 IID。  
  
 `vt`  
 [in]该属性的类型。  
  
### <a name="remarks"></a>备注  
 `PROP_ENTRY_EX`宏是不安全，而且不推荐使用。 已经替换为`PROP_ENTRY_TYPE_EX`。  
  
 [BEGIN_PROP_MAP](#begin_prop_map)宏标记开头的属性映射; [END_PROP_MAP](#end_prop_map)宏标记的末尾。  
  
### <a name="example"></a>示例  
 下面的示例进行分组的项`IMyDual1`的条目后跟`IMyDual2`。 双重接口通过分组会提高性能。  
  
 [!code-cpp[NVC_ATL_Windowing #&133;](../../atl/codesnippet/cpp/property-map-macros_4.h)]  
  
##  <a name="a-nameproppagea--proppage"></a><a name="prop_page"></a>PROP_PAGE  
 使用此宏属性页 CLSID 进入对象的属性映射。  
  
```
PROP_PAGE(clsid)
```  
  
### <a name="parameters"></a>参数  
 `clsid`  
 [in]属性页的 CLSID。  
  
### <a name="remarks"></a>备注  
 `PROP_PAGE`类似于[PROP_ENTRY_TYPE](#prop_entry_type)，但不需要的属性说明或 DISPID。  
  
> [!NOTE]
>  如果您已经输入有 CLSID`PROP_ENTRY_TYPE`或[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)，不需要进行额外的项与`PROP_PAGE`。  
  
 [BEGIN_PROP_MAP](#begin_prop_map)宏标记开头的属性映射; [END_PROP_MAP](#end_prop_map)宏标记的末尾。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&134;](../../atl/codesnippet/cpp/property-map-macros_5.h)]  
  
##  <a name="a-nameendpropmapa--endpropmap"></a><a name="end_prop_map"></a>END_PROP_MAP  
 将标记该对象的属性映射的结尾。  
  
```
END_PROP_MAP()
```  
  
### <a name="remarks"></a>备注  
 当使用 ATL 项目向导创建一个对象时，该向导将创建空属性映射，通过指定[BEGIN_PROP_MAP](#begin_prop_map)跟`END_PROP_MAP`。  
  
### <a name="example"></a>示例  
 请参阅示例[BEGIN_PROP_MAP](#begin_prop_map)。  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)

