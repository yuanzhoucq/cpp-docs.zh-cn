---
title: "ComPtrRef 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::Details::ComPtrRef
dev_langs: C++
helpviewer_keywords: ComPtrRef class
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 34368322da73e7bd0f9e01152fd24fdac52528a8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="comptrref-class"></a>ComPtrRef 类
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
template <  
   typename T  
>  
class ComPtrRef : public ComPtrRefBase<T>;  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 A [ComPtr\<T >](../windows/comptr-class.md)类型派生自它，而不仅仅是 ComPtr 所表示的接口。  
  
## <a name="remarks"></a>备注  
 表示类型 ComPtr 的对象的引用\<T >。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[ComPtrRef::ComPtrRef 构造函数](../windows/comptrref-comptrref-constructor.md)|初始化中的指定指针到另一个 ComPtrRef 对象的 ComPtrRef 类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[ComPtrRef::GetAddressOf 方法](../windows/comptrref-getaddressof-method.md)|检索用当前 ComPtrRef 对象表示的接口的指针的地址。|  
|[ComPtrRef::ReleaseAndGetAddressOf 方法](../windows/comptrref-releaseandgetaddressof-method.md)|删除当前 ComPtrRef 对象并返回指向由 ComPtrRef 对象表示的接口的指针。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[ComPtrRef::operator InterfaceType** 运算符](../windows/comptrref-operator-interfacetype-star-star-operator.md)|删除当前 ComPtrRef 对象并返回指向由 ComPtrRef 对象表示的接口的指针。|  
|[ComPtrRef::operator T* 运算符](../windows/comptrref-operator-t-star-operator.md)|返回的值[ptr_](../windows/comptrrefbase-ptr-data-member.md)当前 ComPtrRef 对象的数据成员。|  
|[ComPtrRef::operator void** 运算符](../windows/comptrref-operator-void-star-star-operator.md)|删除当前 ComPtrRef 对象，作为指针-到-指针-到由 ComPtrRef 对象表示的接口的指针转换`void`，然后返回强制转换指针。|  
|[ComPtrRef::operator* 运算符](../windows/comptrref-operator-star-operator.md)|检索指向由当前 ComPtrRef 对象表示的接口的指针。|  
|[ComPtrRef::operator== 运算符](../windows/comptrref-operator-equality-operator.md)|指示两个 ComPtrRef 对象是否相等。|  
|[ComPtrRef::operator!= 运算符](../windows/comptrref-operator-inequality-operator.md)|指示两个 ComPtrRef 对象是否不相等。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ComPtrRefBase`  
  
 `ComPtrRef`  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)