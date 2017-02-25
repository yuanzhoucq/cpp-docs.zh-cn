---
title: "ComPtr::operator Microsoft::WRL::Details::BoolType 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: cfba6521-fb30-4fb8-afb2-cfab1cb5e0b8
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# ComPtr::operator Microsoft::WRL::Details::BoolType 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示是否 ComPtr 管理接口的对象生存期。  
  
## 语法  
  
```  
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;  
```  
  
## 返回值  
 如果接口与此 ComPtr，[BoolStruct::Member](../windows/boolstruct-member-data-member.md) 数据成员的地址；否则，返回 `nullptr`。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ComPtr 类](../windows/comptr-class.md)   
 [ComPtr::Get 方法](../windows/comptr-get-method.md)