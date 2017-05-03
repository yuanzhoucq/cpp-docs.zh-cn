---
title: "Agile::operator-&gt; 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::operator->"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::operator->"
ms.assetid: 570f4b0b-1735-49b3-8a30-4a302ac57074
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::operator-&gt; 运算符
检索用当前敏捷对象表示的对象的句柄。  
  
## 语法  
  
```cpp  
  
       T^ operator->()   
const throw();  
```  
  
## 返回值  
 用当前敏捷对象表示的对象的句柄。  
  
 此运算符实际返回未公开的内部类型。 保留返回值的一种简便方式是将它分配给用 [auto](~/cpp/auto-cpp.md) 类型推导关键字声明的变量。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **标头：**vccorlib.h  
  
## 请参阅  
 [Platform::Agile 类](../cppcx/platform-agile-class.md)