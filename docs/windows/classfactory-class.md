---
title: "ClassFactory 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::ClassFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ClassFactory 类"
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ClassFactory 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

实现关键帧 IClassFactory 的基本功能。  
  
## 语法  
  
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
  
#### 参数  
 `I0`  
 第零个接口。  
  
 `I1`  
 第一个接口 ID。  
  
 `I2`  
 第二个接口 ID。  
  
## 备注  
 使用 `ClassFactory` 提供用户定义工厂的实现。  
  
 以下编程模式对类工厂演示如何使用 [实现](../windows/implements-structure.md) 结构指定多个接口。  
  
 `struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[ClassFactory::ClassFactory 构造函数](../windows/classfactory-classfactory-constructor.md)||  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[ClassFactory::AddRef 方法](../windows/classfactory-addref-method.md)|递增ClassFactory 当前对象的引用计数。|  
|[ClassFactory::LockServer 方法](../windows/classfactory-lockserver-method.md)|递增或递减由当前 ClassFactory 对象跟踪基础的对象的数量。|  
|[ClassFactory::QueryInterface 方法](../windows/classfactory-queryinterface-method.md)|检索指向参数指定的接口。|  
|[ClassFactory::Release 方法](../windows/classfactory-release-method.md)|递减 ClassFactory 当前对象的引用计数。|  
  
## 继承层次结构  
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
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)   
 [RuntimeClassType 枚举](../windows/runtimeclasstype-enumeration.md)