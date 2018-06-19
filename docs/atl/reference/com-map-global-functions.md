---
title: COM 映射全局函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 509479a923203acd80eaac1ef90aa64125d208c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359874"
---
# <a name="com-map-global-functions"></a>COM 映射全局函数
这些函数提供支持 COM 映射**IUnknown**实现。  
  
|||  
|-|-|  
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|委托给**IUnknown**的非聚合对象。|  
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|生成高效的代码，用于比较针对接口**IUnknown**。|  

  
## <a name="requirements"></a>要求  
 **标头：** atlbase.h  

##  <a name="atlinternalqueryinterface"></a>  AtlInternalQueryInterface  
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
 [in]数组 **_ATL_INTMAP_ENTRY**访问可用接口映射的结构。  
  
 `iid`  
 [in]所请求接口的 GUID。  
  
 `ppvObject`  
 [out]指向中指定的接口指针的指针`iid`，或**NULL**如果找不到该接口。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 `AtlInternalQueryInterface` 仅处理 COM 映射表中的接口。 如果你的对象进行了聚合，`AtlInternalQueryInterface`不未将委托给未知的外部对象。 可以接口输入到 COM 映射表与宏[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)或其变化版本之一。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]  
  
##  <a name="inlineisequaliunknown"></a>  InlineIsEqualIUnknown  
 对测试的特例调用此函数， **IUnknown**。  
  
```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```  
  
### <a name="parameters"></a>参数  
 *rguid1*  
 [in]要进行比较的 GUID **IID_IUnknown**。  
  
## <a name="see-also"></a>请参阅  
 [函数](../../atl/reference/atl-functions.md)   
 [COM 映射宏](../../atl/reference/com-map-macros.md)
