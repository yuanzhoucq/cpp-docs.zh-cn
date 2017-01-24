---
title: "HandleT 类 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HandleT 类"
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HandleT 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示指向对象的句柄。  
  
## 语法  
  
```  
template <  
   typename HandleTraits  
>  
class HandleT;  
```  
  
#### 参数  
 `HandleTraits`  
 定义处理的常见特性 [HandleTraits](../windows/handletraits-structure.md) 结构的实例。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`Traits`|`HandleTraits`的同义词.|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[HandleT::HandleT 构造函数](../windows/handlet-handlet-constructor.md)|初始化 HandleT 类的新实例。|  
|[HandleT::~HandleT 析构函数](../windows/handlet-tilde-handlet-destructor.md)|Deinitializes HandleT 类的实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[HandleT::Attach 方法](../windows/handlet-attach-method.md)|关联指定的句柄与当前 HandleT 对象。|  
|[HandleT::Close 方法](../windows/handlet-close-method.md)|关闭当前的 HandleT对象。|  
|[HandleT::Detach 方法](../windows/handlet-detach-method.md)|离散从其当前 HandleT 基础句柄的对象。|  
|[HandleT::Get 方法](../windows/handlet-get-method.md)|获取基础句柄的值。|  
|[HandleT::IsValid 方法](../windows/handlet-isvalid-method.md)|指示当前 HandleT 对象是否表示句柄。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[HandleT::InternalClose 方法](../windows/handlet-internalclose-method.md)|关闭当前的 HandleT对象。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[HandleT::operator\= 运算符](../windows/handlet-operator-assign-operator.md)|将指定的 HandleT 对象的值设置为当前 HandleT 对象。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[HandleT::handle\_ 数据成员](../windows/handlet-handle-data-member.md)|包含由表示 HandleT 对象的句柄。|  
  
## 继承层次结构  
 `HandleT`  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)