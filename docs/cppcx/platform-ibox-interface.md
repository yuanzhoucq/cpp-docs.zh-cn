---
title: "Platform::IBox 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::IBox"
dev_langs: 
  - "C++"
ms.assetid: 774df45d-f8a7-45a3-ae24-eecc3c681040
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# Platform::IBox 接口
[Platform::IBox](../cppcx/platform-ibox-interface.md) 接口是 `Windows::Foundation::IReference` 接口的 C\+\+ 名称。  
  
## 语法  
  
```cpp  
template <typename T>  
interface class IBox  
```  
  
#### 参数  
 `T`  
 装箱值的类型。  
  
## 备注  
 `IBox<T>` 接口主要用于在内部表示可以为 null 的值类型，如[值类和结构 \(C\+\+\/CX\)](../cppcx/value-classes-and-structs-c-cx.md) 中所述。 该接口还用于对传递给采用参数类型 `Object^` 的 C\+\+ 方法的值类型进行装箱。 可以将输入参数显式声明为 `IBox<SomeValueType>`。 有关示例，请参见 [装箱](../cppcx/boxing-c-cx.md)。  
  
## 要求  
  
## 成员  
 `Platform::IBox` 接口继承自 [Platform::IValueType](../cppcx/platform-ivaluetype-interface.md) 接口。`IBox` 包括以下成员：  
  
 **属性**  
  
|方法|描述|  
|--------|--------|  
|值|返回此 `IBox` 实例以前存储的未装箱值。|  
  
## 请参阅  
 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)