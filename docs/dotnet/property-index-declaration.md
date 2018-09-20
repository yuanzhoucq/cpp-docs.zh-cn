---
title: 属性索引声明 |Microsoft Docs
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
ms.openlocfilehash: a6917742b285b3700548b54fef164d01c0594e5e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380460"
---
# <a name="property-index-declaration"></a>属性索引声明

声明索引的属性的语法已从托管扩展中的 c + + 更改为 Visual c + +。

索引属性的托管扩展语言支持的两个主要的缺点是无法提供类级别子脚本;也就是说，所有索引的属性所需提供一个名称，并因此没有任何方法，例如，若要提供可直接应用于托管下标运算符`Vector`或`Matrix`类对象。 另一个不太明显的缺陷是它是以可视方式难以区分属性和索引属性-参数的数目是唯一的指示。 最后，索引的属性会受到这些非索引化属性与相同的问题-访问器将不视为原子单元，而分为各个方法。  例如：

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

可以如下所示，索引器的区别仅的其他参数来指定两个或单个维度的索引。 在新语法中，由方括号 （[、]） 的索引器的名称后面，并指示的数量和每个索引的类型来区分索引器：

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

若要指示可以直接应用于在新语法中，类的对象的类级别索引器`default`关键字重复使用，以将替换为一个显式的名称。 例如：

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

在新语法中，默认索引时指定属性，保留两个以下名称：`get_Item`和`set_Item`。 这是因为这些是基础生成的默认索引属性的名称。

请注意，没有简单索引的语法类似于简单的属性语法。

## <a name="see-also"></a>请参阅

[类或接口中的成员声明 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)
