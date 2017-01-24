---
title: "多义性解析 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 3d773ee7-bbea-47de-80c2-cb0a9d4ec0b9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 多义性解析
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要执行从一种类型到另一种类型的显式转换，您必须使用强制转换并指定所需的类型名称。  某些类型转换会导致句法歧义。  下面的函数样式类型转换是不明确的：  
  
```  
char *aName( String( s ) );  
```  
  
 不明确的地方是，它是函数声明还是将函数样式转换作为初始值设定项的对象声明：它可以声明采用一个 `String` 类型的参数的函数返回类型 **char \***，也可以声明 `aName` 对象并使用到类型 `String` 的 `s` 转换的值对其进行初始化。  
  
 如果声明可被视为有效的函数声明，则会以相同的方式处理。  只有当它不能是函数声明时（即句法不正确时），才会查看语句是否为函数样式类型转换。  因此，编译器将语句视为函数的声明并忽略标识符 `s` 周围的括号。  另一方面，语句：  
  
```  
char *aName( (String)s );  
```  
  
 和  
  
```  
char *aName = String( s );  
```  
  
 是对象的明确声明，并将调用从 `String` 类型到 **char \*** 类型的用户定义的转换来执行 `aName` 的初始化。  
  
## 请参阅  
 [C\+\+ Abstract Declarators](http://msdn.microsoft.com/zh-cn/e7e18c18-0cad-4450-942b-d27e1d4dd088)