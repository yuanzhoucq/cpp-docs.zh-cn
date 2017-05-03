---
title: "Platform::Object 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Object"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Object 类"
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# Platform::Object 类
提供 ref 类和 ref 结构在 Windows 应用商店应用程序中的通用行为。 所有 ref 类和 ref 结构实例都可以隐式转换为 Platform::Object^，并且可以重写其虚拟 ToString 方法。  
  
## 语法  
  
```scr  
public ref class Object : Object  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[Object::Object 构造函数](../cppcx/object-object-constructor.md)|初始化该对象类的新实例。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[Object::Equals 方法](../cppcx/object-equals-method.md)|确定指定的对象是否等于当前对象。|  
|[Object::GetHashCode 方法](../cppcx/object-gethashcode-method.md)|返回此实例的哈希代码。|  
|[Object::ReferenceEquals 方法](../cppcx/object-referenceequals-method.md)|确定指定对象实例是否为同一实例。|  
|[ToString 方法](../cppcx/object-tostring-method-c-cx.md)|返回表示当前对象的字符串。 可重写。|  
|[GetType 方法](../cppcx/object-gettype-method.md)|获取描述当前实例的 [Platform::Type](../cppcx/platform-type-class.md)。|  
  
## 继承层次结构  
 `Object`  
  
 `Object`  
  
## 要求  
 **标头：**vccorlib.h  
  
 **命名空间：**Platform  
  
## 请参阅  
 [\(NOTINBUILD\) Platform 命名空间](http://msdn.microsoft.com/zh-cn/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)