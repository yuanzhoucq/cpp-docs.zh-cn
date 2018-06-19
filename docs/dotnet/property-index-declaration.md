---
title: 属性索引声明 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- indexers
- default indexers
- defaults, indexers
- indexed properties, C++
ms.assetid: d898fdbc-2106-4b6a-8c5c-9f511d80fc2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 76473ce04cdf5860476b7612ddcbf00b40a0fae1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33160831"
---
# <a name="property-index-declaration"></a>属性索引声明
声明索引的属性的语法已从托管扩展中的 c + + 更改为 Visual c + +。  
  
 索引属性的托管扩展语言支持的两个主要的缺点是，无法提供类级别下标;即，所有索引的属性所需为指定的名称，并因此没有任何方法，例如，可提供一种托管的下标运算符，可以直接应用于`Vector`或`Matrix`类对象。 另一个不太重要的缺点是，很直观地难区分属性和索引属性，即参数的数目是唯一的指示。 最后，从与非索引化属性的相同问题的索引的属性会受到影响-访问器将不视为一个原子单元，而分为各个方法。  例如：  
  
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
  
 正如您可以在此处看到，仅按照附加的参数来指定了两个或单个进行区分索引器维索引。 在新语法中，索引器进行区分的括号 （[、]） 以下索引器的名称，并指示每个索引的类型和数量：  
  
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
  
 若要指示可以直接应用到类的新语法中的对象的类级别索引器`default`关键字重用来代替显式名称。 例如：  
  
```  
public ref class Matrix {  
private:  
   array<float, 2>^ mat;  
  
public:  
   // ok: class level indexer now  
   //  
   //     Matrix mat;  
   //     mat[ 0, 0 ] = 1;   
   //  
   // invokes the set accessor of the default indexer  
  
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
  
 在新语法中，当默认索引指定属性时，保留两个以下名称：`get_Item`和`set_Item`。 这是因为这些是生成的默认索引属性的基础名称。  
  
 请注意，没有任何简单索引的语法类似于简单的属性语法。  
  
## <a name="see-also"></a>请参阅  
 [类或接口中的成员声明 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 