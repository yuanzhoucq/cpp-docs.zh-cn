---
title: "Agile::GetAddressOf 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::GetAddressOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::GetAddressOf"
ms.assetid: f015edf9-4155-4992-a6fc-7ff1edcc5d1e
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::GetAddressOf 方法
重新初始化当前敏捷对象，然后返回类型为 `T` 的对象的句柄地址。  
  
## 语法  
  
```cpp  
  
       T^* GetAddressOf()   
throw();  
```  
  
#### 参数  
 `T`  
 模板类型名称参数指定的类型。  
  
## 返回值  
 `T` 类型的对象的句柄地址。  
  
## 备注  
 此操作释放类型为 `T` 的对象的当前表示形式（如果有）；重新初始化敏捷对象的数据成员；获取当前线程处理上下文；然后返回可以表示非敏捷对象的对象句柄变量的地址。 若要使敏捷类实例表示对象，请使用赋值运算符 \([Agile::operator\=](../cppcx/agile-operator-assign-operator.md)\) 将对象分配给敏捷类实例。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **标头：**vccorlib.h  
  
## 请参阅  
 [Platform::Agile 类](../cppcx/platform-agile-class.md)