---
title: "Platform::WeakReference 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform::WeakReference"
ms.assetid: 8cfe1977-a8c7-4b7b-b539-25c77ed4c5f1
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::WeakReference 类
表示对 ref 类实例的弱引用。  
  
## 语法  
  
```vb  
class WeakReference  
```  
  
#### 参数  
  
## 成员  
  
### 构造函数  
  
|成员|说明|  
|--------|--------|  
|[WeakReference::WeakReference 构造函数](../cppcx/weakreference-weakreference-constructor-c-cx.md)|初始化 WeakReference 类的新实例。|  
  
### 方法  
  
|成员|描述|  
|--------|--------|  
|[WeakReference::Resolve 方法](../cppcx/weakreference-resolve-method-platform-namespace.md)|如果对象不再存在，则返回基础 ref 类的句柄或 nullptr。|  
  
### 运算符  
  
|成员|说明|  
|--------|--------|  
|[WeakReference::operator\=](../cppcx/weakreference-operator-assign.md)|给 WeakReference 对象赋新值。|  
  
## 备注  
 WeakReference 类本身不是 ref 类，因此不从 Platform::Object^ 继承，也不能在公共方法的签名中使用。  
  
## 请参阅  
 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)