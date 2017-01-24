---
title: "pair (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::pair"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pair 类 [STL/CLR]"
ms.assetid: 3326b4d9-a52a-49e5-8103-9aa5e8b352de
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# pair (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模板类描述一个包装对值的对象。  
  
## 语法  
  
```  
template<typename Value1,  
    typename Value2>  
    ref class pair;  
```  
  
#### 参数  
 Value1  
 首先包装的值类型。  
  
 Value2  
 第二个包装值的类型。  
  
## 成员  
  
|类型定义|说明|  
|----------|--------|  
|[pair::first\_type](../dotnet/pair-first-type-stl-clr.md)|第一个包装值的类型。|  
|[pair::second\_type](../dotnet/pair-second-type-stl-clr.md)|第二个包装值的类型。|  
  
|成员对象|说明|  
|----------|--------|  
|[pair::first](../dotnet/pair-first-stl-clr.md)|第一个存储值。|  
|[pair::second](../dotnet/pair-second-stl-clr.md)|第二个存储值。|  
  
|成员函数|说明|  
|----------|--------|  
|[pair::pair](../dotnet/pair-pair-stl-clr.md)|构造一对对象。|  
|[pair::swap](../dotnet/pair-swap-stl-clr.md)|交换两个对的内容。|  
  
|运算符|说明|  
|---------|--------|  
|[pair::operator\=](../dotnet/pair-operator-assign-stl-clr.md)|替换存储对的值。|  
  
## 备注  
 对象存储一对值。  使用此模板类合并两值到单个对象。  注意 `cliext::pair` \(详见这里\) 只存储管理的类型;存储一对非托管类型的使用`std::pair`，在 `<utility>`中声明。  
  
## 要求  
 **标头:** \<cliext\/utility\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [make\_pair](../dotnet/make-pair-stl-clr.md)