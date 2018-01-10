---
title: "CComQIPtr 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
dev_langs: C++
helpviewer_keywords: CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b63e584b7c4620be0e77da034a2a419b80cf741
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccomqiptr-class"></a>CComQIPtr 类
用于管理 COM 接口指针的智能指针类。  
  
## <a name="syntax"></a>语法  
  
```
template<class T, const IID* piid= &__uuidof(T)>  
class CComQIPtr: public CComPtr<T>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 COM 接口，指定要存储的指针的类型。  
  
 `piid`  
 指向 IID 的`T`。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComQIPtr::CComQIPtr](#ccomqiptr)|构造函数。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CComQIPtr::operator =](#operator_eq)|将指针分配给成员指针。|  
  
## <a name="remarks"></a>备注  
 使用 ATL`CComQIPtr`和[CComPtr](../../atl/reference/ccomptr-class.md)来管理 COM 接口指针，这两种派生自[CComPtrBase](../../atl/reference/ccomptrbase-class.md)。 这两个类执行自动引用计数通过对调用`AddRef`和**版本**。 重载的运算符处理指针操作。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 [CComPtr](../../atl/reference/ccomptr-class.md)  
  
 `CComQIPtr`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcomcli.h  
  
##  <a name="ccomqiptr"></a>CComQIPtr::CComQIPtr  
 构造函数。  
  
```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```  
  
### <a name="parameters"></a>参数  
 `lp`  
 用于初始化的接口指针。  
  
 `T`  
 COM 接口。  
  
 `piid`  
 指向 IID 的`T`。  
  
##  <a name="operator_eq"></a>CComQIPtr::operator =  
 赋值运算符中。  
  
```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```  
  
### <a name="parameters"></a>参数  
 `lp`  
 用于初始化的接口指针。  
  
 `T`  
 COM 接口。  
  
 `piid`  
 指向 IID 的`T`。  
  
### <a name="return-value"></a>返回值  
 将指针返回到更新`CComQIPtr`对象。  
  
## <a name="see-also"></a>请参阅  
 [CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)   
 [CComQIPtr::CComQIPtr](#ccomqiptr)   
 [CComPtrBase 类](../../atl/reference/ccomptrbase-class.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [CComQIPtrElementTraits 类](../../atl/reference/ccomqiptrelementtraits-class.md)
