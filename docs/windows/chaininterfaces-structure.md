---
title: "ChainInterfaces 结构 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::ChainInterfaces"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ChainInterfaces 结构"
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ChainInterfaces 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定可能应用于一组接口 ID 的验证和初始化函数。  
  
## 语法  
  
```  
template <  
   typename I0,  
   typename I1,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct ChainInterfaces : I0;  
template <  
   typename DerivedType,  
   typename BaseType,  
   bool hasImplements,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8,  
   typename I9  
>  
struct ChainInterfaces<MixIn<DerivedType, BaseType, hasImplements>, I1, I2, I3, I4, I5, I6, I7, I8, I9>;  
```  
  
#### 参数  
 `I0`  
 必需的接口ID 0。  
  
 `I1`  
 必需的接口ID 1。  
  
 `I2`  
 \(可选\) 接口 ID 2。  
  
 `I3`  
 \(可选\) 接口 ID 3。  
  
 `I4`  
 \(可选\) 接口 ID 4。  
  
 `I5`  
 \(可选\) 接口 ID 5。  
  
 `I6`  
 \(可选\) 接口 ID 6。  
  
 `I7`  
 \(可选\) 接口 ID 7。  
  
 `I8`  
 \(可选\) 接口 ID 8。  
  
 `I9`  
 \(可选\) 接口 ID 9。  
  
 `DerivedType`  
 派生类型  
  
 `BaseType`  
 的派生类型的基类型。  
  
 `hasImplements`  
 布尔值，如果 `true`，这意味着不能使用从 [实现](../windows/implements-structure.md) 结构不从派生的类中的 [MixIn](../windows/mixin-structure.md) 结构。  
  
## 成员  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[ChainInterfaces::CanCastTo 方法](../windows/chaininterfaces-cancastto-method.md)|指示指定接口 ID 是否可以转换为主要接口的模板参数定义的每一专用化。|  
|[ChainInterfaces::CastToUnknown 方法](../windows/chaininterfaces-casttounknown-method.md)|转换定义 `I0` 模板参数类型的接口指针的指针到指向 IUnknown。|  
|[ChainInterfaces::FillArrayWithIid 方法](../windows/chaininterfaces-fillarraywithiid-method.md)|存储 `I0` 模板参数定义的接口 ID 到指定的数组中的指定位置设置接口 ID。|  
|[ChainInterfaces::Verify 方法](../windows/chaininterfaces-verify-method.md)|验证模板参数定义的每个接口 `I0` 通过 `I9` 和 IInspectable 由从继承，因此，通过 `I0` 从 `I1` 继承 `I9`。|  
  
### 保护的常量  
  
|名称|说明|  
|--------|--------|  
|[ChainInterfaces::IidCount 常量](../windows/chaininterfaces-iidcount-constant.md)|接口 ID 的总数。包含接口的模板通过指定的参数 `I0` `I9`。|  
  
## 继承层次结构  
 `I0`  
  
 `ChainInterfaces`  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)