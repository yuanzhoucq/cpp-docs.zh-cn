---
title: "COM 映射全局函数 |Microsoft 文档"
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
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
caps.latest.revision: 19
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
ms.openlocfilehash: c37f722267107ad06fb51dc78bd682603161a476
ms.lasthandoff: 02/24/2017

---
# <a name="com-map-global-functions"></a>COM 映射全局函数
这些函数提供对 COM 映射支持**IUnknown**实现。  
  
|||  
|-|-|  
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|委托给**IUnknown**的非聚合对象。|  
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|生成高效的代码，用于比较接口与**IUnknown**。|  

  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  

##  <a name="a-nameatlinternalqueryinterfacea--atlinternalqueryinterface"></a><a name="atlinternalqueryinterface"></a>AtlInternalQueryInterface  
 检索指向所请求的接口的指针。  
  
```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 `pThis`  
 [in]指向包含向公开的接口的 COM 映射的对象的指针`QueryInterface`。  
  
 `pEntries`  
 [in]一个数组**_ATL_INTMAP_ENTRY**访问可用的接口映射的结构。  
  
 `iid`  
 [in]正在请求的接口的 GUID。  
  
 `ppvObject`  
 [out]中指定的接口指针指向的指针`iid`，或**NULL**如果找不到该接口。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 `AtlInternalQueryInterface` 仅处理 COM 映射表中的接口。 如果您的对象进行了聚合，`AtlInternalQueryInterface`不将委派给未知的外部对象。 接口输入到 COM 映射表与宏[COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/19dcb768-2e1f-4b8d-a618-453a01a4bd00)或其变化版本之一。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&94;](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]  
  
##  <a name="a-nameinlineisequaliunknowna--inlineisequaliunknown"></a><a name="inlineisequaliunknown"></a>InlineIsEqualIUnknown  
 有关测试的特例调用此函数， **IUnknown**。  
  
```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```  
  
### <a name="parameters"></a>参数  
 *rguid1*  
 [in]要比较的 GUID **IID_IUnknown**。  
  
## <a name="see-also"></a>另请参阅  
 [函数](../../atl/reference/atl-functions.md)   
 [COM 映射宏](../../atl/reference/com-map-macros.md)

