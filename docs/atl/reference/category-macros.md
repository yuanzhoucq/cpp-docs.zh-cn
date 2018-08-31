---
title: 分类宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4fdf98e41b552fa759f1aed3e67d531e02bc7f58
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206770"
---
# <a name="category-macros"></a>分类宏
这些宏定义类别映射。  
  
|||  
|-|-|  
|[BEGIN_CATEGORY_MAP](#begin_category_map)|标记类别映射的开头。|  
|[END_CATEGORY_MAP](#end_category_map)|标记类别映射的末尾。|  
|[IMPLEMENTED_CATEGORY](#implemented_category)|指示由 COM 对象实现的类别。|  
|[REQUIRED_CATEGORY](#required_category)|指示所需的容器的 COM 对象的类别。|  

## <a name="requirements"></a>要求  
 **标头：** atlcom.h  

##  <a name="begin_category_map"></a>  BEGIN_CATEGORY_MAP  
 标记类别映射的开头。  
  
```
BEGIN_CATEGORY_MAP(theClass)
```  
  
### <a name="parameters"></a>参数  
 *类*  
 [in]包含类别映射的类的名称。  
  
### <a name="remarks"></a>备注  
 类别映射用于指定 COM 类将实现和从其容器它需要哪些类别的组件类别。  
  
 添加[IMPLEMENTED_CATEGORY](#implemented_category)由 COM 类实现每个类别的映射条目。 添加[REQUIRED_CATEGORY](#required_category)类要求其客户端来实现每个类别的映射条目。 将标记与映射的结尾[END_CATEGORY_MAP](#end_category_map)宏。  
  
 在映射中列出的组件类别将自动注册，注册该模块时，如果类具有一个关联[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto).  
  
> [!NOTE]
>  ATL 使用标准组件类别管理器注册组件类别。 如果管理器不存在于系统中注册该模块时，注册成功，但为该类将不会注册组件类别。  
  
 组件类别的详细信息，请参阅[什么是组件类别以及它们如何工作](/windows/desktop/com/component-categories-and-how-they-work)Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="end_category_map"></a>  END_CATEGORY_MAP  
 标记类别映射的末尾。  
  
```
END_CATEGORY_MAP()
```  
  
### <a name="example"></a>示例  
 有关示例，请参阅[BEGIN_CATEGORY_MAP](#begin_category_map)。  
  
##  <a name="implemented_category"></a>  IMPLEMENTED_CATEGORY  
 将 IMPLEMENTED_CATEGORY 宏添加到你的组件[类别映射](#begin_category_map)以指定应注册为实现由标识类别*catID*参数。  
  
```
IMPLEMENTED_CATEGORY(catID)
```  
  
### <a name="parameters"></a>参数  
 *catID*  
 [in]CATID 常量或变量，保存为实现类别的全局唯一标识符 (GUID)。 地址*catID*将创建并添加到映射。 请参阅下表中选择的股票的类别。  
  
### <a name="remarks"></a>备注  
 在映射中列出的组件类别将自动注册，注册该模块时，如果类具有一个关联[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)宏。  
  
 客户端可以使用为类注册的类别信息以确定其功能和要求，而无需创建它的一个实例。  
  
 组件类别的详细信息，请参阅[什么是组件类别以及它们如何工作](/windows/desktop/com/component-categories-and-how-they-work)Windows SDK 中。  
  
### <a name="a-selection-of-stock-categories"></a>选择的股票类别  
  
|描述|符号|注册表 GUID|  
|-----------------|------------|-------------------|  
|用于编写脚本的安全|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|对初始化是安全|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|简单的框架站点包容|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|简单数据绑定|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|高级的数据绑定|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|无窗口控件|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|可识别 Internet 的对象|请参阅[Internet 注意对象](/windows/desktop/com/internet-aware-objects)Windows SDK for 示例列表中。||  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="required_category"></a>  REQUIRED_CATEGORY  
 将 REQUIRED_CATEGORY 宏添加到你的组件[类别映射](#begin_category_map)以指定应注册为需要由标识类别*catID*参数。  
  
```
REQUIRED_CATEGORY( catID )
```  
  
### <a name="parameters"></a>参数  
 *catID*  
 [in]CATID 常量或变量，保存为所需的类别的全局唯一标识符 (GUID)。 地址*catID*将创建并添加到映射。 请参阅下表中选择的股票的类别。  
  
### <a name="remarks"></a>备注  
 在映射中列出的组件类别将自动注册，注册该模块时，如果类具有一个关联[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)宏。  
  
 客户端可以使用为类注册的类别信息以确定其功能和要求，而无需创建它的一个实例。 例如，控件可能需要一个容器，支持数据绑定。 容器可以找出是否必要的功能来通过查询该控件所需的类别的类别管理器中承载该控件。 如果容器不支持所需的功能，它可以拒绝托管 COM 对象。  
  
 详细了解组件类别，包括示例列表，请参阅[什么是组件类别以及它们如何工作](/windows/desktop/com/component-categories-and-how-they-work)Windows SDK 中。  
  
### <a name="a-selection-of-stock-categories"></a>选择的股票类别  
  
|描述|符号|注册表 GUID|  
|-----------------|------------|-------------------|  
|用于编写脚本的安全|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|对初始化是安全|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|简单的框架站点包容|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|简单数据绑定|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|高级的数据绑定|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|无窗口控件|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|可识别 Internet 的对象|请参阅[Internet 注意对象](/windows/desktop/com/internet-aware-objects)Windows SDK for 示例列表中。||  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]  
  
## <a name="see-also"></a>请参阅  
 [宏](../../atl/reference/atl-macros.md)
