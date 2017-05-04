---
title: "Agile::Agile 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::Agile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::Agile"
ms.assetid: 33c1df82-f5db-4750-98cc-0daa03be4e59
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::Agile 构造函数
初始化 Agile 类的新实例。  
  
## 语法  
  
```cpp  
  
 Agile();  
  
Agile(T^ object);   
  
Agile(const Agile<T>& object);  
  
Agile(Agile<T>&& object);  
  
```  
  
#### 参数  
 `T`  
 模板类型名称参数指定的类型。  
  
 `object`  
 在此构造函数的第二个版本中，用于初始化新的 Agile 实例的对象。 在第三个版本中，复制到新的 Agile 实例的对象。 在第四个版本中，移动到新的 Agile 实例的对象。  
  
## 备注  
 此构造函数的第一个版本是默认构造函数。 第二个版本从 `object` 参数指定的对象初始化新实例 Agile 类。 第三个版本是复制构造函数。 第四个版本是移动构造函数。 此构造函数不能引发异常。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **标头：**vccorlib.h  
  
## 请参阅  
 [Platform::Agile 类](../cppcx/platform-agile-class.md)