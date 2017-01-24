---
title: "SimpleClassFactory 类 | Microsoft Docs"
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
  - "module/Microsoft::WRL::SimpleClassFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SimpleClassFactory 类"
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SimpleClassFactory 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供基本机制创建基类。  
  
## 语法  
  
```  
template<  
   typename Base  
>  
class SimpleClassFactory : public ClassFactory<>;  
```  
  
#### 参数  
 `Base`  
 （基类）  
  
## 备注  
 此类必须具有默认构造函数。  
  
 下面的代码示例演示如何使用带有 [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) 宏的 SimpleClassFactory。  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[SimpleClassFactory::CreateInstance 方法](../windows/simpleclassfactory-createinstance-method.md)|创建指定接口的实例。|  
  
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
  
 `SimpleClassFactory`  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)