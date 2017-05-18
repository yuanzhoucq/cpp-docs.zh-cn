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
dev_langs:
- C++
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 26eea5cc8ce8e18af84a9ca89e5ddc94272be44c
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="category-macros"></a>类别宏
这些宏定义类别映射。  
  
|||  
|-|-|  
|[BEGIN_CATEGORY_MAP](#begin_category_map)|标记类别映射开始。|  
|[END_CATEGORY_MAP](#end_category_map)|标记类别映射的末尾。|  
|[IMPLEMENTED_CATEGORY](#implemented_category)|指示由 COM 对象实现的类别。|  
|[REQUIRED_CATEGORY](#required_category)|指示所需容器的 COM 对象的类别。|  

## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  

##  <a name="begin_category_map"></a>BEGIN_CATEGORY_MAP  
 标记类别映射开始。  
  
```
BEGIN_CATEGORY_MAP(theClass)
```  
  
### <a name="parameters"></a>参数  
 `theClass`  
 [in]包含分类映射的类的名称。  
  
### <a name="remarks"></a>备注  
 类别映射用于指定哪些组件类别 COM 类将实现，并且从它的容器需要哪些类别。  
  
 添加[IMPLEMENTED_CATEGORY](#implemented_category)到由 COM 类实现每个类别的映射条目。 添加[REQUIRED_CATEGORY](#required_category)到此类需要其客户端来实现每个类别的映射条目。 将标记与映射的结尾[END_CATEGORY_MAP](#end_category_map)宏。  
  
 如果该类有一个关联中注册该模块时将会自动登记在映射中列出的组件类别[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)。  
  
> [!NOTE]
>  ATL 使用标准组件类别管理器注册组件类别。 如果管理器不存在于系统中注册该模块时，注册成功，但不是会为该类注册组件类别。  
  
 有关组件类别的详细信息，请参阅[什么是组件类别以及它们是如何工作](http://msdn.microsoft.com/library/windows/desktop/ms694322)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&100;](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="end_category_map"></a>END_CATEGORY_MAP  
 标记类别映射的末尾。  
  
```
END_CATEGORY_MAP()
```  
  
### <a name="example"></a>示例  
 请参阅示例[BEGIN_CATEGORY_MAP](#begin_category_map)。  
  
##  <a name="implemented_category"></a>IMPLEMENTED_CATEGORY  
 添加`IMPLEMENTED_CATEGORY`宏的组件的[类别映射](#begin_category_map)来指定应注册为实现由该类别`catID`参数。  
  
```
IMPLEMENTED_CATEGORY(catID)
```  
  
### <a name="parameters"></a>参数  
 `catID`  
 [in]一个**CATID**常量或变量持有的用于实现类别的全局唯一标识符 (GUID)。 地址`catID`将执行并添加到映射。 请参阅下表中选定的股票的类别。  
  
### <a name="remarks"></a>备注  
 如果该类有一个关联中注册该模块时将会自动登记在映射中列出的组件类别[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)宏。  
  
 客户端可以使用为类注册的类别信息以确定其功能和要求，而无需创建它的一个实例。  
  
 有关组件类别的详细信息，请参阅[什么是组件类别以及它们是如何工作](http://msdn.microsoft.com/library/windows/desktop/ms694322)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="a-selection-of-stock-categories"></a>所选的股票类别  
  
|描述|符号|注册表 GUID|  
|-----------------|------------|-------------------|  
|对于脚本是安全|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|对初始化是安全|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|简单框架站点包容|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|简单数据绑定|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|高级的数据绑定|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|无窗口控件|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|Internet 感知对象|请参阅[Internet 感知对象](http://msdn.microsoft.com/library/windows/desktop/ms690561)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]示例列表。||  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&100;](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="required_category"></a>REQUIRED_CATEGORY  
 添加`REQUIRED_CATEGORY`宏的组件的[类别映射](#begin_category_map)来指定应注册为需要由标识类别`catID`参数。  
  
```
REQUIRED_CATEGORY( catID )
```  
  
### <a name="parameters"></a>参数  
 `catID`  
 [in]一个**CATID**常量或变量所需的类别用于存放的全局唯一标识符 (GUID)。 地址`catID`将执行并添加到映射。 请参阅下表中选定的股票的类别。  
  
### <a name="remarks"></a>备注  
 如果该类有一个关联中注册该模块时将会自动登记在映射中列出的组件类别[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)宏。  
  
 客户端可以使用为类注册的类别信息以确定其功能和要求，而无需创建它的一个实例。 例如，一个控件可能要求容器支持数据绑定。 容器可以找出自己是否通过查询该控件所需的类别的类别管理器中承载该控件所需的功能。 如果容器不支持要求的功能，它可以拒绝托管的 COM 对象。  
  
 有关组件类别，包括示例列表，请参阅[什么是组件类别以及它们是如何工作](http://msdn.microsoft.com/library/windows/desktop/ms694322)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="a-selection-of-stock-categories"></a>所选的股票类别  
  
|描述|符号|注册表 GUID|  
|-----------------|------------|-------------------|  
|对于脚本是安全|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|对初始化是安全|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|简单框架站点包容|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|简单数据绑定|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|高级的数据绑定|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|无窗口控件|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|Internet 感知对象|请参阅[Internet 感知对象](http://msdn.microsoft.com/library/windows/desktop/ms690561)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]示例列表。||  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&135;](../../atl/codesnippet/cpp/category-macros_2.h)]  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)

