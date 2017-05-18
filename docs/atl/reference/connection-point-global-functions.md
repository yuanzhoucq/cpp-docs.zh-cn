---
title: "连接点的全局函数 |Microsoft 文档"
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
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
caps.latest.revision: 20
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
ms.openlocfilehash: 8271f512141e4d2cc274d180b31e1ad33bfc354e
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="connection-point-global-functions"></a>连接点的全局函数
这些函数提供对连接点的支持和接收器映射。  
  
> [!IMPORTANT]
>  下表中列出的函数不能用于应用程序中执行[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
|||  
|-|-|  
|[AtlAdvise](#atladvise)|在对象的连接点和客户端的接收器间创建连接。|  
|[AtlUnadvise](#atlunadvise)|通过建立的连接将终止`AtlAdvise`。|  
|[AtlAdviseSinkMap](#atladvisesinkmap)|建议或取消通知事件接收器映射中的条目。|  

## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
   
##  <a name="atladvise"></a>AtlAdvise  
 在对象的连接点和客户端的接收器间创建连接。  
  
> [!IMPORTANT]
>  此函数不能用于应用程序中执行[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```  
  
### <a name="parameters"></a>参数  
 `pUnkCP`  
 [in]一个指向**IUnknown**客户端希望与连接的对象。  
  
 *pUnk*  
 [in]一个指向客户端的**IUnknown**。  
  
 `iid`  
 [in]连接点的 GUID。 通常情况下，这是管理由连接点的输出接口相同。  
  
 `pdw`  
 [out]Cookie 的唯一标识该连接指向的指针。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 接收器会实现连接点所支持的输出接口。 客户端使用`pdw`cookie 以删除该连接将其传递给[AtlUnadvise](#atlunadvise)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&91;](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]  
  
##  <a name="atlunadvise"></a>AtlUnadvise  
 通过建立的连接将终止[AtlAdvise](#atladvise)。  
  
> [!IMPORTANT]
>  此函数不能用于应用程序中执行[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```  
  
### <a name="parameters"></a>参数  
 `pUnkCP`  
 [in]一个指向**IUnknown**客户端连接使用的对象。  
  
 `iid`  
 [in]连接点的 GUID。 通常情况下，这是管理由连接点的输出接口相同。  
  
 `dw`  
 [in]唯一标识连接的 cookie。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&96;](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]  
  
##  <a name="atladvisesinkmap"></a>AtlAdviseSinkMap  
 调用此函数可在对象的接收器事件映射中建议或不建议所有条目。  
  
> [!IMPORTANT]
>  此函数不能用于应用程序中执行[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```  
  
### <a name="parameters"></a>参数  
 *pT*  
 [in]指向包含接收器映射的对象的指针。  
  
 `bAdvise`  
 [in]**true**接收器的所有项是否可以收到通知。**false**如果将要 unadvised 接收器的所有条目。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&92;](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]  
  
## <a name="see-also"></a>另请参阅  
 [函数](../../atl/reference/atl-functions.md)   
 [连接点宏](../../atl/reference/connection-point-macros.md)

