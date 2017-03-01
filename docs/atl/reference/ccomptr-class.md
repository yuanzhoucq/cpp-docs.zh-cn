---
title: "CComPtr 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPtr
dev_langs:
- C++
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
caps.latest.revision: 21
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ae7bb5e85f23492bdbef4af86d9f68fa83c991e2
ms.lasthandoff: 02/24/2017

---
# <a name="ccomptr-class"></a>CComPtr 类
智能指针类，用于管理 COM 接口指针。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>  
class CComPtr
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 COM 接口，指定要存储的指针的类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComPtr::CComPtr](#ccomptr)|构造函数。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CComPtr::operator =](#operator_eq)|将一个指针分配给成员指针。|  
  
## <a name="remarks"></a>备注  
 ATL 使用`CComPtr`和[CComQIPtr](../../atl/reference/ccomqiptr-class.md)来管理 COM 接口指针。 派生自[CComPtrBase](../../atl/reference/ccomptrbase-class.md)，并同时执行自动引用计数。  
  
 **CComPtr**和[CComQIPtr](../../atl/reference/ccomqiptr-class.md)类可帮助避免内存泄漏，通过执行自动引用计数。  以下函数这两个执行相同的逻辑操作;但是，请注意如何第二个版本可能是更不易于出错使用**CComPtr**类︰  
  
 [!code-cpp[NVC_ATL_Utilities #&130;](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities #&131;](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]  
  
 在调试版本链接代码跟踪的 atlsd.lib。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 `CComPtr`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="a-nameccomptra--ccomptrccomptr"></a><a name="ccomptr"></a>CComPtr::CComPtr  
 构造函数。  
  
```
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```  
  
### <a name="parameters"></a>参数  
 `lp`  
 用于初始化的接口指针。  
  
 `T`  
 COM 接口。  
  
##  <a name="a-nameoperatoreqa--ccomptroperator-"></a><a name="operator_eq"></a>CComPtr::operator =  
 赋值运算符。  
  
```
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向已更新`CComPtr`对象  
  
### <a name="remarks"></a>备注  
 现有对象，如果存在此操作 AddRefs 新对象和版本。  
  
## <a name="see-also"></a>另请参阅  
 [CComPtr::CComPtr](#ccomptr)   
 [CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)   
 [类概述](../../atl/atl-class-overview.md)

