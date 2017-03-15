---
title: "属性索引声明 | Microsoft Docs"
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
  - "默认索引器"
  - "默认值, 索引器"
  - "索引属性, C++"
  - "索引器"
ms.assetid: d898fdbc-2106-4b6a-8c5c-9f511d80fc2f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 属性索引声明
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，用于声明索引属性的语法已发生了更改。  
  
 索引属性的托管扩展语言支持的两个主要的缺点是：其一是无法提供类级下标；也就是说，要求为所有的索引属性赋予一个名称，因此，例如，无法提供可直接应用于 `Vector` 或 `Matrix` 类对象的托管下标运算符。  另一个不太重要的缺点是难以区分属性和索引属性 — 参数的数目是唯一的指示。  最后，索引属性遇到与非索引属性相同的问题 — 不将访问器视为一个原子单元，而将其分隔为各个方法。例如：  
  
```  
public __gc class Vector;  
public __gc class Matrix {  
   float mat[,];  
  
public:   
   __property void set_Item( int r, int c, float value);  
   __property float get_Item( int r, int c );  
  
   __property void set_Row( int r, Vector* value );  
   __property Vector* get_Row( int r );  
};  
```  
  
 如此处所示，仅通过附加参数指定两个或单个维索引来区分索引器。  在新语法中，通过在索引器的名称后跟括号 \(\[,\]\) 指示每个索引的数目和类型来区分索引器：  
  
```  
public ref class Vector {};  
public ref class Matrix {  
private:  
   array<float, 2>^ mat;  
  
public:  
   property float Item [int,int] {  
      float get( int r, int c );  
      void set( int r, int c, float value );  
   }  
  
   property Vector^ Row [int] {  
      Vector^ get( int r );  
      void set( int r, Vector^ value );  
   }  
};  
```  
  
 要在新的语法中指示可直接应用于类对象的类级索引器，请重复使用 `default` 来代替显式名称。  例如：  
  
```  
public ref class Matrix {  
private:  
   array<float, 2>^ mat;  
  
public:  
   // ok: class level indexer now  
   //  
   //     Matrix mat …  
   //     mat[ 0, 0 ] = 1;   
   //  
   // invokes the set accessor of the default indexer …  
  
   property float default [int,int] {  
      float get( int r, int c );  
      void set( int r, int c, float value );  
   }  
  
   property Vector^ Row [int] {  
      Vector^ get( int r );  
      void set( int r, Vector^ value );  
   }  
};  
```  
  
 在新的语法中，指定默认索引属性时保留了以下两个名称：`get_Item` 和 `set_Item`。  这是因为生成了默认索引属性的基础名称。  
  
 请注意，不存在与简单属性语法相似的简单索引语法。  
  
## 请参阅  
 [类或接口中的成员声明 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [如何：使用索引属性](../misc/how-to-use-indexed-properties.md)