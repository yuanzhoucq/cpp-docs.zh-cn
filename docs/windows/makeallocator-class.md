---
title: "MakeAllocator 类 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::MakeAllocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MakeAllocator 类"
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MakeAllocator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
  
template<  
   typename T,  
   bool hasWeakReferenceSupport =   
         !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,   
   T)> , T)> class MakeAllocator;  
  
template<  
   typename T  
>  
class MakeAllocator<T, false>;  
  
template<  
   typename T  
>  
class MakeAllocator<T, true>;  
```  
  
#### 参数  
 `T`  
 类型名称。  
  
 `hasWeakReferenceSupport`  
 分配支持弱引用的对象的内存。`true` ;将不支持弱引用对象的内存中。`false`  
  
## 备注  
 分配一 activatable 类的内存，无论是否使用弱引用支持。  
  
 重写 MakeAllocator 类实现一种用户定义的内存分配模式。  
  
 MakeAllocator 通常用于在构造期间防止内存泄漏，则对象将引发。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[MakeAllocator::MakeAllocator 构造函数](../windows/makeallocator-makeallocator-constructor.md)|初始化 MakeAllocator 类的新实例。|  
|[MakeAllocator::~MakeAllocator 析构函数](../windows/makeallocator-tilde-makeallocator-destructor.md)|Deinitializes MakeAllocator 类的当前实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[MakeAllocator::Allocate 方法](../windows/makeallocator-allocate-method.md)|分配内存并将它与当前 MakeAllocator 对象。|  
|[MakeAllocator::Detach 方法](../windows/makeallocator-detach-method.md)|离散从当前对象 MakeAllocator 的 [分配](../windows/makeallocator-allocate-method.md) 方法分配的内存。|  
  
## 继承层次结构  
 `MakeAllocator`  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)