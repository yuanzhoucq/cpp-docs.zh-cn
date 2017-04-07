---
title: "CComHeapPtr 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
dev_langs:
- C++
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
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
ms.openlocfilehash: 0e5196a98b8fd76b2e7e791fd2cd9549099a1cc9
ms.lasthandoff: 02/24/2017

---
# <a name="ccomheapptr-class"></a>CComHeapPtr 类
智能指针类，用于管理堆指针。  
  
## <a name="syntax"></a>语法  
  
```
template<typename T>  
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要存储在堆上的对象类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|构造函数。|  
  
## <a name="remarks"></a>备注  
 `CComHeapPtr`派生自`CHeapPtr`，但使用[CComAllocator](../../atl/reference/ccomallocator-class.md)以使用 COM 例程分配内存。 请参阅[CHeapPtr](../../atl/reference/cheapptr-class.md)和[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)可用的方法。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md)  
  
 `CComHeapPtr`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="ccomheapptr"></a>CComHeapPtr::CComHeapPtr  
 构造函数。  
  
```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```  
  
### <a name="parameters"></a>参数  
 `pData`  
 一个现有的 `CComHeapPtr` 对象。  
  
### <a name="remarks"></a>备注  
 （可选） 可以使用现有创建堆指针`CComHeapPtr`对象。 如果是这样，新`CComHeapPtr`对象负责管理的新指针和资源。  
  
## <a name="see-also"></a>另请参阅  
 [CHeapPtr 类](../../atl/reference/cheapptr-class.md)   
 [CHeapPtrBase 类](../../atl/reference/cheapptrbase-class.md)   
 [CComAllocator 类](../../atl/reference/ccomallocator-class.md)   
 [类概述](../../atl/atl-class-overview.md)

