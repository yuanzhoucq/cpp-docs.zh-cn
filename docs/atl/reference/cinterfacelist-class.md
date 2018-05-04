---
title: CInterfaceList 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1fc523b1eccc88678cda48a0c7e429ea0fc09f9b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
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
 指向 IID 的`I`。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CInterfaceList::CInterfaceList](#cinterfacelist)|接口列表构造函数。|  
  
## <a name="remarks"></a>备注  
 此类提供一个构造函数和派生的方法用于创建 COM 接口指针的列表。 使用[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)需要数组时。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CInterfaceList`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcoll.h  
  
##  <a name="cinterfacelist"></a>  CInterfaceList::CInterfaceList  
 接口列表构造函数。  
  
```
CInterfaceList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>参数  
 `nBlockSize`  
 块的大小，默认值为 10。  
  
### <a name="remarks"></a>备注  
 块大小是内存的分配需要一个新的元素时量的度量值。 更大的块大小减少到内存分配例程的调用，但使用更多资源。  
  
## <a name="see-also"></a>请参阅  
 [CAtlList 类](../../atl/reference/catllist-class.md)   
 [CComQIPtr 类](../../atl/reference/ccomqiptr-class.md)   
 [CComQIPtrElementTraits 类](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [类概述](../../atl/atl-class-overview.md)
