---
title: "Agile::operator= 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "agile/Platform::Agile::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Agile::operator="
ms.assetid: 2c413bef-f103-4911-afb3-0dac5f6a760e
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Agile::operator= 运算符
将指定对象分配给当前敏捷对象。  
  
## 语法  
  
```cpp  
  
   Agile<T> operator=(  
   T^ object  
) throw();  
  
   Agile<T> operator=(  
      const Agile<T>& object  
) throw();  
  
   Agile<T> operator=(  
      Agile<T>&& object  
) throw();  
  
   T^ operator=(  
      IUnknown* lp  
) throw();  
  
```  
  
#### 参数  
 `T`  
 模板类型名称指定的类型。  
  
 `object`  
 复制或移动到当前敏捷对象的对象或对象句柄。  
  
 `lp`  
 对象的 IUnknown 接口指针。  
  
## 返回值  
 `T` 类型的对象的句柄  
  
## 备注  
 赋值运算符的第一个版本将引用类型的句柄复制到当前敏捷对象。 第二个版本将对敏捷类型的引用复制到当前敏捷对象。 第三个版本将一个敏捷类型移到当前敏捷对象。 第四个版本将 COM 对象的指针移到当前敏捷对象。  
  
 赋值操作自动保存当前敏捷对象的上下文。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **标头：**vccorlib.h  
  
## 请参阅  
 [Platform::Agile 类](../cppcx/platform-agile-class.md)