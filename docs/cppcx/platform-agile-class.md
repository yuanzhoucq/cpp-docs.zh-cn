---
title: "Platform::Agile 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile"
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::Agile 类
表示将 MashalingBehavior\=Standard 作为敏捷对象（这可以大大降低出现运行时线程处理异常的机率）的对象。`Agile<T>` 使非敏捷对象可以调用相同或不同线程调用，或是从相同或不同线程进行调用。 有关详细信息，请参阅[线程处理和封送处理](../cppcx/threading-and-marshaling-c-cx.md)。  
  
## 语法  
  
```scr  
  
template <typename T>  
    class Agile  
;  
```  
  
#### 参数  
 T  
 非敏捷类的类型名称。  
  
## 备注  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 中的大多数类是敏捷类。 敏捷对象可以调用相同或不同线程中的进程内或进程外对象，或是由该对象进行调用。 如果对象不是敏捷对象，请在 `Agile<T>` 对象（这是敏捷对象）中包装非敏捷对象。 随后可以封送 `Agile<T>` 对象，并且可以使用基础非敏捷对象。  
  
 `Agile<T>` 类是本机标准 C\+\+ 类，需要 `agile.h`。 它表示非敏捷对象和敏捷对象的*上下文*。 上下文指定敏捷对象的线程处理模型和封送处理行为。 操作系统使用上下文来确定如何封送对象。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[Agile::Agile 构造函数](../cppcx/agile-agile-constructor.md)|初始化 Agile 类的新实例。|  
|[Agile::~Agile 析构函数](../cppcx/agile-tilde-agile-destructor.md)|销毁敏捷类的当前实例。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[Agile::Get](../cppcx/agile-get-method.md)|返回用当前敏捷对象表示的对象的句柄。|  
|[Agile::GetAddressOf](../cppcx/agile-getaddressof-method.md)|重新初始化当前敏捷对象，然后返回类型为 `T` 的对象的句柄地址。|  
|[Agile::GetAddressOfForInOut](../cppcx/agile-getaddressofforinout-method.md)|将句柄的地址返回到用当前敏捷对象表示的对象。|  
|[Agile::Release](../cppcx/agile-release-method.md)|放弃当前敏捷对象的基础对象和上下文。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[Agile::operator\-\>](../cppcx/agile-operator-arrow-operator.md)|检索用当前敏捷对象表示的对象的句柄。|  
|[Agile::operator\=](../cppcx/agile-operator-assign-operator.md)|将指定值分配给当前敏捷对象。|  
  
## 继承层次结构  
 `Object`  
  
 `Agile`  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **标头：**agile.h  
  
## 请参阅  
 [\(NOTINBUILD\) Platform 命名空间](http://msdn.microsoft.com/zh-cn/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)