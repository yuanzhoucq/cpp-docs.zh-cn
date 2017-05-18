---
title: "CComQIPtr 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
dev_langs:
- C++
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: e2060a0be3f9780191c316c2df41115e66033d4d
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ccomqiptr-class"></a>CComQIPtr 类
智能指针类，用于管理 COM 接口指针。  
  
## <a name="syntax"></a>语法  
  
```
template<class T, const IID* piid= &__uuidof(T)>  
class CComQIPtr: public CComPtr<T>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 COM 接口，指定要存储的指针的类型。  
  
 `piid`  
 指向的指针的 IID `T`。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComQIPtr::CComQIPtr](#ccomqiptr)|构造函数。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CComQIPtr::operator =](#operator_eq)|将一个指针分配给成员指针。|  
  
## <a name="remarks"></a>备注  
 ATL 使用`CComQIPtr`和[CComPtr](../../atl/reference/ccomptr-class.md)若要管理 COM 接口指针，这两个派生自[CComPtrBase](../../atl/reference/ccomptrbase-class.md)。 这两个类执行自动引用计数通过调用`AddRef`和**版本**。 重载的运算符处理指针操作。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 [CComPtr](../../atl/reference/ccomptr-class.md)  
  
 `CComQIPtr`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcomcli.h  
  
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
 指向的指针的 IID `T`。  
  
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
 指向的指针的 IID `T`。  
  
### <a name="return-value"></a>返回值  
 返回一个指向已更新`CComQIPtr`对象。  
  
## <a name="see-also"></a>另请参阅  
 [CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)   
 [CComQIPtr::CComQIPtr](#ccomqiptr)   
 [CComPtrBase 类](../../atl/reference/ccomptrbase-class.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [CComQIPtrElementTraits 类](../../atl/reference/ccomqiptrelementtraits-class.md)

