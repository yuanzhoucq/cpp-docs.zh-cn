---
title: "RuntimeClass 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::RuntimeClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RuntimeClass 类"
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClass 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示实例化类，该类继承特定接口数量，并提供指定的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]、传统性 COM 和弱引用支持。  
  
 通常情况下，你从 `RuntimeClass` 派生你的 WRL 类型，因为此类可以实现 `AddRef`、`Release` 和 `QueryInterface`，并且有助于管理模块的整体引用计数。  
  
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
class RuntimeClass : public Details::RuntimeClass<typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8, I9>::TypeT, RuntimeClassFlags<WinRt>>;  
  
template <  
   unsigned int classFlags,  
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
class RuntimeClass<RuntimeClassFlags<classFlags>, I0, I1, I2, I3, I4, I5, I6, I7, I8> : public Details::RuntimeClass<typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8>::TypeT, RuntimeClassFlags<classFlags> >;  
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
  
 `classFlags`  
 一个或多个 [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) 枚举值的组合。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[RuntimeClass::RuntimeClass 构造函数](../windows/runtimeclass-runtimeclass-constructor.md)|初始化 RuntimeClass 类的当前实例。|  
|[RuntimeClass::~RuntimeClass 析构函数](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|取消初始化 RuntimeClass 类的当前实例。|  
  
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
  
 `RuntimeClass`  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)