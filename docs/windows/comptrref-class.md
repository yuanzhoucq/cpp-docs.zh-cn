---
title: ComPtrRef 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRef class
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7f7f392df62892ea0e053e9d243f85772fa0605d
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463072"
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
 *T*  
 一个[ComPtr\<T >](../windows/comptr-class.md)类型派生自它，而不仅仅是所表示接口`ComPtr`。  
  
## <a name="remarks"></a>备注  
 表示类型的对象的引用`ComPtr<T>`。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[ComPtrRef::ComPtrRef 构造函数](../windows/comptrref-comptrref-constructor.md)|初始化的新实例**ComPtrRef**到另一个类从指定的指针**ComPtrRef**对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[ComPtrRef::GetAddressOf 方法](../windows/comptrref-getaddressof-method.md)|检索指向当前 ComPtrRef 对象所表示接口的指针的地址。|  
|[ComPtrRef::ReleaseAndGetAddressOf 方法](../windows/comptrref-releaseandgetaddressof-method.md)|删除当前**ComPtrRef**对象并返回到由表示的接口的指针到-的指针**ComPtrRef**对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[ComPtrRef::operator InterfaceType** 运算符](../windows/comptrref-operator-interfacetype-star-star-operator.md)|删除当前**ComPtrRef**对象并返回到由表示的接口的指针到-的指针**ComPtrRef**对象。|  
|[ComPtrRef::operator T* 运算符](../windows/comptrref-operator-t-star-operator.md)|返回的值[ptr_](../windows/comptrrefbase-ptr-data-member.md)当前 ComPtrRef 对象的数据成员。|  
|[ComPtrRef::operator void** 运算符](../windows/comptrref-operator-void-star-star-operator.md)|删除当前**ComPtrRef**对象，将强制转换到由表示的接口指针**ComPtrRef**对象作为指针-到-指针-若要**void**，，然后返回转换的指针。|  
|[ComPtrRef::operator* 运算符](../windows/comptrref-operator-star-operator.md)|检索指向当前所表示接口的指针**ComPtrRef**对象。|  
|[ComPtrRef::operator== 运算符](../windows/comptrref-operator-equality-operator.md)|指示两个**ComPtrRef**对象是否相等。|  
|[ComPtrRef::operator!= 运算符](../windows/comptrref-operator-inequality-operator.md)|指示两个**ComPtrRef**对象是否不相等。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ComPtrRefBase`  
  
 `ComPtrRef`  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)