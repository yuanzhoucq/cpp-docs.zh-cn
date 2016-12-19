---
title: "Implements 结构 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Implements"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Implements 结构"
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implements 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

实现 QueryInterface 和 GetIid 指定的接口。  
  
## 语法  
  
```  
template <  
   typename I0,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct __declspec(novtable) Implements : Details::ImplementsHelper<RuntimeClassFlags<WinRt>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8, I9>::TypeT>, Details::ImplementsBase;  
template <  
   int flags,  
   typename I0,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8  
>  
struct __declspec(novtable) Implements<RuntimeClassFlags<flags>, I0, I1, I2, I3, I4, I5, I6, I7, I8> : Details::ImplementsHelper<RuntimeClassFlags<flags>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8>::TypeT>, Details::ImplementsBase;  
```  
  
#### 参数  
 `I0`  
 第零个接口 ID。（必需）  
  
 `I1`  
 第一个接口 ID。（可选）  
  
 `I2`  
 第二个接口 ID。（可选）  
  
 `I3`  
 第三个接口 ID。（可选）  
  
 `I4`  
 第四个接口 ID。（可选）  
  
 `I5`  
 第五个接口 ID。（可选）  
  
 `I6`  
 第六个接口 ID。（可选）  
  
 `I7`  
 第七个接口 ID。（可选）  
  
 `I8`  
 第八个接口 ID。（可选）  
  
 `I9`  
 第九个接口 ID。（可选）  
  
 `flags`  
 配置类的标志。  在 [RuntimeClassFlags](../windows/runtimeclassflags-structure.md) 结构指定的一个或多个枚举。[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)  
  
## 备注  
 从指定接口列表派生并实现 QueryInterface 和 GetIid 的帮助程序模板。  
  
 每个 `I0` 通过 `I9` 接口变量必须从 IInspectable [ChainInterfaces](../windows/chaininterfaces-structure.md) IUnknown，或者模板派生。  确定支持 `flags` 参数是否为 IInspectable 由或生成。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`ClassFlags`|`RuntimeClassFlags<WinRt>`的同义词.|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[Implements::CanCastTo 方法](../windows/implements-cancastto-method.md)|获取特定接口的指针。|  
|[Implements::CastToUnknown 方法](../windows/implements-casttounknown-method.md)|一个指向基础 IUnknown 接口。|  
|[Implements::FillArrayWithIid 方法](../windows/implements-fillarraywithiid-method.md)|用于插入当前 zeroth 模板参数指定的接口 ID 到指定的数组元素。|  
  
### 保护的常量  
  
|名称|说明|  
|--------|--------|  
|[Implements::IidCount 常量](../windows/implements-iidcount-constant.md)|包含已实现的接口 ID 的数量。|  
  
## 继承层次结构  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `ImplementsBase`  
  
 `ImplementsHelper`  
  
 `Implements`  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)