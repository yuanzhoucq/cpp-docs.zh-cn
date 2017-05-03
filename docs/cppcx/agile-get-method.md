---
title: "Agile::Get 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::Get"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::Get"
ms.assetid: d6295e21-ddbe-4302-9158-3498da4d9669
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::Get 方法
返回用当前敏捷对象表示的对象的句柄。  
  
## 语法  
  
```cpp  
  
          T^ Get() const  
;  
```  
  
## 返回值  
 用当前敏捷对象表示的对象的句柄。  
  
 返回值的类型实际是未公开的内部类型。 保留返回值的一种简便方式是将它分配给用 [auto](~/cpp/auto-cpp.md) 类型推导关键字声明的变量。 例如 `auto x = myAgileTvariable->Get();`。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **标头：**vccorlib.h  
  
## 请参阅  
 [Platform::Agile 类](../cppcx/platform-agile-class.md)