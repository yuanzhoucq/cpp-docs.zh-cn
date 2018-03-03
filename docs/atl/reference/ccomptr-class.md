---
title: "CComPtr 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
dev_langs:
- C++
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ef8c49b04a769fd6202aa58324f20216948cf3a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccomptr-class"></a>CComPtr 类
用于管理 COM 接口指针的智能指针类。  
  
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
  
|名称|描述|  
|----------|-----------------|  
|[CComPtr::CComPtr](#ccomptr)|构造函数。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CComPtr::operator =](#operator_eq)|将指针分配给成员指针。|  
  
## <a name="remarks"></a>备注  
 使用 ATL`CComPtr`和[CComQIPtr](../../atl/reference/ccomqiptr-class.md)来管理 COM 接口指针。 派生自[CComPtrBase](../../atl/reference/ccomptrbase-class.md)，并同时执行自动引用计数。  
  
 **CComPtr**和[CComQIPtr](../../atl/reference/ccomqiptr-class.md)类可以帮助执行自动引用计数，从而消除内存泄漏。  以下函数这两个执行相同的逻辑操作;但是，请注意如何第二个版本可能不太容易出错使用**CComPtr**类：  
  
 [!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]  
  
 在调试版本中，将 atlsd.lib 代码跟踪。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 `CComPtr`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlbase.h  
  
##  <a name="ccomptr"></a>CComPtr::CComPtr  
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
  
##  <a name="operator_eq"></a>CComPtr::operator =  
 赋值运算符。  
  
```
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```  
  
### <a name="return-value"></a>返回值  
 将指针返回到更新`CComPtr`对象  
  
### <a name="remarks"></a>备注  
 现有对象，如果一个存在此操作 AddRefs 新对象和版本。  
  
## <a name="see-also"></a>请参阅  
 [CComPtr::CComPtr](#ccomptr)   
 [CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)   
 [类概述](../../atl/atl-class-overview.md)
