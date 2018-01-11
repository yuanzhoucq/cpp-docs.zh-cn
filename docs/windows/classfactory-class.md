---
title: "ClassFactory 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ClassFactory
dev_langs: C++
helpviewer_keywords: ClassFactory class
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c37c016809d31fcb072f23768e9f54313331016
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="classfactory-class"></a>ClassFactory 类
实现 IClassFactory 接口的基本功能。  
  
## <a name="syntax"></a>语法  
  
```  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ClassFactory : public Details::RuntimeClass<  
   typename Details::InterfaceListHelper<IClassFactory,   
   I0,   
   I1,   
   I2,   
   Details::Nil>::TypeT,   
   RuntimeClassFlags<ClassicCom | InhibitWeakReference>,   
      false>;  
```  
  
#### <a name="parameters"></a>参数  
 `I0`  
 第零个接口中。  
  
 `I1`  
 第一个接口。  
  
 `I2`  
 第二个接口。  
  
## <a name="remarks"></a>备注  
 利用`ClassFactory`能够提供的用户定义的工厂实现。  
  
 以下编程模式演示如何使用[实现](../windows/implements-structure.md)结构，以指定多个三个接口的类工厂。  
  
 `struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[ClassFactory::ClassFactory 构造函数](../windows/classfactory-classfactory-constructor.md)||  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[ClassFactory::AddRef 方法](../windows/classfactory-addref-method.md)|递增当前 ClassFactory 对象的引用计数。|  
|[ClassFactory::LockServer 方法](../windows/classfactory-lockserver-method.md)|递增或递减当前 ClassFactory 对象跟踪的基础对象数量。|  
|[ClassFactory::QueryInterface 方法](../windows/classfactory-queryinterface-method.md)|检索指向指定参数的接口的指针。|  
|[ClassFactory::Release 方法](../windows/classfactory-release-method.md)|递减当前 ClassFactory 对象的引用计数。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `RuntimeClassBase`  
  
 `ImplementsHelper`  
  
 `DontUseNewUseMake`  
  
 `RuntimeClassFlags`  
  
 `RuntimeClassBaseT`  
  
 `RuntimeClass`  
  
 `ClassFactory`  
  
## <a name="requirements"></a>惠?  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft:: wrl Namespace](../windows/microsoft-wrl-namespace.md)   
 [RuntimeClassType 枚举](../windows/runtimeclasstype-enumeration.md)