---
title: "CInterfaceList 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
dev_langs:
- C++
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 50d86163080c5a0d0a7bb9ed6d77a40ac73722e7
ms.lasthandoff: 02/24/2017

---
# <a name="cinterfacelist-class"></a>CInterfaceList 类
构造的 COM 接口指针的列表时，此类提供有用的方法。  
  
## <a name="syntax"></a>语法  
  
```
template<class I, const IID* piid =& __uuidof(I)>  
class CInterfaceList 
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```  
  
#### <a name="parameters"></a>参数  
 `I`  
 COM 接口，指定要存储的指针的类型。  
  
 `piid`  
 指向的指针的 IID `I`。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CInterfaceList::CInterfaceList](#cinterfacelist)|有关接口列表构造函数。|  
  
## <a name="remarks"></a>备注  
 此类提供一个构造函数和派生的方法，用于创建 COM 接口指针的列表。 使用[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)需要数组时。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CInterfaceList`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcoll.h  
  
##  <a name="cinterfacelist"></a>CInterfaceList::CInterfaceList  
 有关接口列表构造函数。  
  
```
CInterfaceList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>参数  
 `nBlockSize`  
 块的大小，默认值为 10。  
  
### <a name="remarks"></a>备注  
 块大小为分配一个新元素时所需的内存量的度量值。 更大的块大小减少对内存分配例程的调用，但使用更多的资源。  
  
## <a name="see-also"></a>另请参阅  
 [CAtlList 类](../../atl/reference/catllist-class.md)   
 [CComQIPtr 类](../../atl/reference/ccomqiptr-class.md)   
 [CComQIPtrElementTraits 类](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [类概述](../../atl/atl-class-overview.md)

