---
title: "typeof 转到 T::typeid | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__typeof 关键字"
  - "typeid 关键字 [C++]"
  - "typeid 运算符"
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# typeof 转到 T::typeid
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 托管扩展中使用的 `typeof` 运算符已由 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 中的 `typeid` 关键字所取代。  
  
 在托管扩展中，`__typeof()` 运算符在传递了托管类型的名称时返回关联的 `Type*` 对象。  例如：  
  
```  
// Creates and initializes a new Array instance.  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 在新语法中，`__typeof` 已由其他形式的 `typeid`（当指定了托管类型时它返回 `Type^`）替换。  
  
```  
// Creates and initializes a new Array instance.  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
## 请参阅  
 [常规语言更改](../dotnet/general-language-changes-cpp-cli.md)   
 [typeid](../windows/typeid-cpp-component-extensions.md)