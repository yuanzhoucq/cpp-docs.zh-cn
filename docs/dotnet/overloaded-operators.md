---
title: 重载运算符 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- operator overloading, in a CLR class
- operators [C++], overloading
ms.assetid: 30391426-afe7-4497-bf22-e4816c1e48c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a53b8df6f10a4fb8efcd91ce5d9c3f0125320139
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425855"
---
# <a name="overloaded-operators"></a>重载运算符

运算符重载有了显著变化从托管扩展 c + + Visual c + +。

在声明中的引用类型，示例中，而不使用本机`operator+`语法中，您显式写出的运算符的基础的内部名称在这种情况下， `op_Addition`。 此外，运算符的调用必须在显式调用通过该名称，这样会排除运算符重载的两个主要优点: （a） 的直观的语法，并将混合新类型与现有类型 （b） 的功能。 例如：

```
public __gc __sealed class Vector {
public:
   Vector( double x, double y, double z );

   static bool    op_Equality( const Vector*, const Vector* );
   static Vector* op_Division( const Vector*, double );
   static Vector* op_Addition( const Vector*, const Vector* );
   static Vector* op_Subtraction( const Vector*, const Vector* );
};

int main()
{
   Vector *pa = new Vector( 0.231, 2.4745, 0.023 );
   Vector *pb = new Vector( 1.475, 4.8916, -1.23 );

   Vector *pc1 = Vector::op_Addition( pa, pb );
   Vector *pc2 = Vector::op_Subtraction( pa, pc1 );
   Vector *pc3 = Vector::op_Division( pc1, pc2->x );

   if ( Vector::op_Equality( pc1, pc2 ))
      ;
}
```

在新语法中，将还原的本机 c + + 程序员通常期望，在声明和使用静态运算符。 下面是`Vector`类转换为新的语法：

```
public ref class Vector sealed {
public:
   Vector( double x, double y, double z );

   static bool    operator ==( const Vector^, const Vector^ );
   static Vector^ operator /( const Vector^, double );
   static Vector^ operator +( const Vector^, const Vector^ );
   static Vector^ operator -( const Vector^, const Vector^ );
};

int main()
{
   Vector^ pa = gcnew Vector( 0.231, 2.4745, 0.023 );
   Vector^ pb = gcnew Vector( 1.475,4.8916,-1.23 );

   Vector^ pc1 = pa + pb;
   Vector^ pc2 = pa - pc1;
   Vector^ pc3 = pc1 / pc2->x;

   if ( pc1 == pc2 )
      ;
}
```

## <a name="see-also"></a>请参阅

[类或接口中的成员声明 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)