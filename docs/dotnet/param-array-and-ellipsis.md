---
title: "参数数组和省略号 | Microsoft Docs"
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
  - "函数重载, 参数匹配"
ms.assetid: 492e3f6c-1c4c-4e0c-a358-72f2d39c30be
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 参数数组和省略号
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，参数数组用于解析重载函数调用的优先级发生了更改。  
  
 在托管扩展和新语法中，都没有对 C\# 和 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 支持的参数数组的显式支持。  而是使用特性标记普通数组，如下所示：  
  
```  
void Trace1( String* format, [ParamArray]Object* args[] );  
void Trace2( String* format, Object* args[] );  
```  
  
 虽然两者看起来是相同的，但是，对于 C\# 或其他 CLR 语言，`ParamArray` 特性将此标记为每次调用时具有可变数量元素的数组。  使用托管扩展的程序和使用新语法的程序中行为的更改是在重载函数集的解析中，其中一个实例声明省略号，另一个实例声明 `ParamArray` 特性，如 Artur Laksberg 提供的以下示例中所示。  
  
```  
int fx(...); // 1  
int fx( [ParamArray] Int32[] ); // 2  
```  
  
 在托管扩展中，省略号的优先级高于特性是合理的，因为特性不是这些语言中的正式用法。  然而，在新语法中，现在该语言内直接支持参数数组，而且由于它的类型更强，它的优先级高于省略号。  这样，在托管扩展中，调用  
  
```  
fx( 1, 2 );  
```  
  
 解析为 `fx(…)`，而在新语法中，它解析为 `ParamArray` 实例。  程序行为取决于省略号实例的调用优先于 `ParamArray` 的调用的可能性极小，一旦发生这种情况，您需要修改签名或调用。  
  
## 请参阅  
 [常规语言更改](../dotnet/general-language-changes-cpp-cli.md)