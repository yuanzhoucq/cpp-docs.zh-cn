---
title: "类别宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
dev_langs:
- C++
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 752a0c0c9de5c726a106ca08a574844369c6bdc5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="category-macros"></a>类别宏
这些宏定义类别映射。  
  
|||  
|-|-|  
|[BEGIN_CATEGORY_MAP](#begin_category_map)|标记类别映射开始。|  
|[END_CATEGORY_MAP](#end_category_map)|标记类别映射的末尾。|  
|[IMPLEMENTED_CATEGORY](#implemented_category)|指示由 COM 对象实现的类别。|  
|[REQUIRED_CATEGORY](#required_category)|指示所需的容器的 COM 对象的类别。|  

## <a name="requirements"></a>惠?  
 **标头：** atlcom.h  

##  <a name="begin_category_map"></a>BEGIN_CATEGORY_MAP  
 标记类别映射开始。  
  
```
BEGIN_CATEGORY_MAP(theClass)
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 [in]包含类别映射的类名称。  
  
### <a name="remarks"></a>备注  
 类别映射用于指定哪些组件类别的 COM 类将实现和从其容器它需要的类别。  
  
 添加[IMPLEMENTED_CATEGORY](#implemented_category)进入实现的 COM 类的每个类别的映射。 添加[REQUIRED_CATEGORY](#required_category)进入类要求其客户端实现的每个类别的映射。 标记的末尾对地图[END_CATEGORY_MAP](#end_category_map)宏。  
  
 如果类具有一个关联注册模块时将自动注册图中列出的组件类别[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto).  
  
> [!NOTE]
>  ATL 使用标准组件类别管理器注册组件类别。 如果注册模块时，该管理器不存在系统上，注册成功，但组件类别将不会注册为该类。  
  
 有关组件类别的详细信息，请参阅[什么是组件类别以及它们如何工作](http://msdn.microsoft.com/library/windows/desktop/ms694322)Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="end_category_map"></a>END_CATEGORY_MAP  
 标记类别映射的末尾。  
  
```
END_CATEGORY_MAP()
```  
  
### <a name="example"></a>示例  
 请参阅示例[BEGIN_CATEGORY_MAP](#begin_category_map)。  
  
##  <a name="implemented_category"></a>IMPLEMENTED_CATEGORY  
 添加`IMPLEMENTED_CATEGORY`宏为组件的[类别映射](#begin_category_map)来指定应注册为实现由类别`catID`参数。  
  
```
IMPLEMENTED_CATEGORY(catID)
```  
  
### <a name="parameters"></a>参数  
 `catID`  
 [in]A **CATID**常量或变量用于实现类别存放的全局唯一标识符 (GUID)。 地址`catID`将执行并添加到映射。 请参阅下表中的选择的常用的类别。  
  
### <a name="remarks"></a>备注  
 如果类具有一个关联注册模块时将自动注册图中列出的组件类别[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)宏。  
  
 客户端可以使用为类注册的类别信息以确定其功能和要求，而无需创建它的实例。  
  
 有关组件类别的详细信息，请参阅[什么是组件类别以及它们如何工作](http://msdn.microsoft.com/library/windows/desktop/ms694322)Windows SDK 中。  
  
### <a name="a-selection-of-stock-categories"></a>选择的常用的类别  
  
|描述|符号|注册表 GUID|  
|-----------------|------------|-------------------|  
|用于脚本编写的安全|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|对初始化是安全|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|简单框架站点包容|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|简单数据绑定|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|高级的数据绑定|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|无窗口控件|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|Internet 可识别的对象|请参阅[Internet 感知对象](http://msdn.microsoft.com/library/windows/desktop/ms690561)Windows SDK for 示例列表中。||  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="required_category"></a>REQUIRED_CATEGORY  
 添加`REQUIRED_CATEGORY`宏为组件的[类别映射](#begin_category_map)来指定应注册为需要由类别`catID`参数。  
  
```
REQUIRED_CATEGORY( catID )
```  
  
### <a name="parameters"></a>参数  
 `catID`  
 [in]A **CATID**常量或变量所需的类别用于存放的全局唯一标识符 (GUID)。 地址`catID`将执行并添加到映射。 请参阅下表中的选择的常用的类别。  
  
### <a name="remarks"></a>备注  
 如果类具有一个关联注册模块时将自动注册图中列出的组件类别[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)宏。  
  
 客户端可以使用为类注册的类别信息以确定其功能和要求，而无需创建它的实例。 例如，控件可能需要容器支持数据绑定。 容器可以找出它是否有必要以通过查询该控件所需的类别的类别管理器承载控件的功能。 如果容器不支持所需的功能，它可以拒绝托管的 COM 对象。  
  
 详细了解组件类别，包括示例列表，请参阅[什么是组件类别以及它们如何工作](http://msdn.microsoft.com/library/windows/desktop/ms694322)Windows SDK 中。  
  
### <a name="a-selection-of-stock-categories"></a>选择的常用的类别  
  
|描述|符号|注册表 GUID|  
|-----------------|------------|-------------------|  
|用于脚本编写的安全|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|对初始化是安全|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|简单框架站点包容|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|简单数据绑定|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|高级的数据绑定|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|无窗口控件|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|Internet 可识别的对象|请参阅[Internet 感知对象](http://msdn.microsoft.com/library/windows/desktop/ms690561)Windows SDK for 示例列表中。||  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]  
  
## <a name="see-also"></a>请参阅  
 [宏](../../atl/reference/atl-macros.md)
