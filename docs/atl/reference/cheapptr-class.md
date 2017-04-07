---
title: "CHeapPtr 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHeapPtr
- ATLCORE/ATL::CHeapPtr
- ATLCORE/ATL::CHeapPtr::CHeapPtr
- ATLCORE/ATL::CHeapPtr::Allocate
- ATLCORE/ATL::CHeapPtr::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtr class
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
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
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 41334cd7497c9e21d1cf047d7ab304864f663758
ms.lasthandoff: 02/24/2017

---
# <a name="cheapptr-class"></a>CHeapPtr 类
智能指针类，用于管理堆指针。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template<typename T, class Allocator=CCRTAllocator>  
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要存储在堆上的对象类型。  
  
 `Allocator`  
 要使用的内存分配类。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CHeapPtr::CHeapPtr](#cheapptr)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CHeapPtr::Allocate](#allocate)|调用此方法以在将对象存储在堆上分配内存。|  
|[CHeapPtr::Reallocate](#reallocate)|调用此方法来重新分配在堆上的内存。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CHeapPtr::operator =](#operator_eq)|赋值运算符中。|  
  
## <a name="remarks"></a>备注  
 `CHeapPtr`派生自[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)和默认情况下使用的 CRT 例程 (在[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)) 来分配和释放内存。 此类[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)可用于构造的堆指针的列表。 另请参阅[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)，它使用 COM 内存分配例程。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)  
  
 `CHeapPtr`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcore.h  
  
##  <a name="allocate"></a>CHeapPtr::Allocate  
 调用此方法以在将对象存储在堆上分配内存。  
  
```
bool Allocate(size_t nElements = 1) throw();
```  
  
### <a name="parameters"></a>参数  
 `nElements`  
 用于计算要分配的内存量的元素数。 默认值为 1。  
  
### <a name="return-value"></a>返回值  
 分配的内存已成功时返回 true，false 失败。  
  
### <a name="remarks"></a>备注  
 分配器例程用于保留足够的内存来存储堆上*nElement*构造函数中定义的类型的对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&77;](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]  
  
##  <a name="cheapptr"></a>CHeapPtr::CHeapPtr  
 构造函数。  
  
```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 现有的堆指针或`CHeapPtr`。  
  
### <a name="remarks"></a>备注  
 （可选） 可以使用现有的指针，创建堆指针或`CHeapPtr`对象。 如果是这样，新`CHeapPtr`对象负责管理的新指针和资源。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&78;](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]  
  
##  <a name="operator_eq"></a>CHeapPtr::operator =  
 赋值运算符。  
  
```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 一个现有的 `CHeapPtr` 对象。  
  
### <a name="return-value"></a>返回值  
 返回对已更新的引用`CHeapPtr`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&80;](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]  
  
##  <a name="reallocate"></a>CHeapPtr::Reallocate  
 调用此方法来重新分配在堆上的内存。  
  
```
bool Reallocate(size_t nElements) throw();
```  
  
### <a name="parameters"></a>参数  
 `nElements`  
 新的用于计算要分配的内存量的元素数。  
  
### <a name="return-value"></a>返回值  
 分配的内存已成功时返回 true，false 失败。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&79;](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CHeapPtrBase 类](../../atl/reference/cheapptrbase-class.md)   
 [CCRTAllocator 类](../../atl/reference/ccrtallocator-class.md)   
 [类概述](../../atl/atl-class-overview.md)

