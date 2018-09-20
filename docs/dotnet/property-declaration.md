---
title: 属性声明 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __property keyword
- declaring properties, C++
- property keyword [C++]
ms.assetid: de169378-a8b8-49f4-a586-76bffc9b5c9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 019b8eae17952bfe53fd8fbf14db4bafce1bf463
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438296"
---
# <a name="property-declaration"></a>属性声明

若要声明托管类中的属性的方式已从托管扩展中的 c + + 更改为 Visual c + +。

在托管扩展设计时，每个`set`或`get`属性访问器被指定为独立的方法。 每个方法的声明前缀为`__property`关键字。 方法名称开头`set_`或`get_`跟属性 （如对用户可见） 的实际名称。 因此，`Vector`提供`x`协调`get`属性将对其进行命名`get_x`和用户一样调用它`x`。 此命名约定和方法的单独规范实际反映了该属性的基础运行时实现。 例如，下面是我们`Vector`具有一组坐标的属性：

```
public __gc __sealed class Vector {
public:
   __property double get_x(){ return _x; }
   __property double get_y(){ return _y; }
   __property double get_z(){ return _z; }

   __property void set_x( double newx ){ _x = newx; }
   __property void set_y( double newy ){ _y = newy; }
   __property void set_z( double newz ){ _z = newz; }
};
```

这与属性相关联的功能可以分散，要求用户从词法上统一的关联的集和获取。 此外，它是 verbose。 在新语法中，这是更类似于 C#，`property`关键字后面的属性，且其未修饰的名称的类型。 `set`和`get`访问方法放置在块中的属性名后面。 请注意，与 C# 中，指定访问方法的签名。 例如，下面是上面的代码示例转换为新的语法。

```
public ref class Vector sealed {
public:
   property double x {
      double get() {
         return _x;
      }

      void set( double newx ) {
         _x = newx;
      }
   } // Note: no semi-colon
};
```

如果该属性的访问方法反映不同访问级别-例如`public get`和一个`private`或`protected set`，可以指定一个明确的访问权限的标签。 默认情况下，该属性的访问级别反映的封闭的访问级别。 例如，在上面的定义`Vector`，这两个`get`并`set`方法都是`public`。 若要使`set`方法`protected`或`private`，定义将进行如下修改：

```
public ref class Vector sealed {
public:
   property double x {
      double get() {
         return _x;
      }

   private:
      void set( double newx ) {
         _x = newx;
      }

   } // note: extent of private culminates here

// note: dot is a public method of Vector
double dot( const Vector^ wv );

// etc.
};
```

属性内的访问关键字的作用域扩展到该属性的右大括号或其他访问关键字的规范。 它不会超过在其中定义该属性的封闭访问级别的属性的定义。 在上面的声明中，例如，`Vector::dot()`是公共方法。

写入三个设置/获取属性`Vector`坐标涉及三个步骤：

1. 声明适当类型的私有状态成员。

1. 当用户想要获取其值时，请将其返回。

1. 将其分配新值。

在新语法的速记属性语法是可用来自动化此使用模式：

```
public ref class Vector sealed {
public:
   // equivalent shorthand property syntax
   property double x;
   property double y;
   property double z;
};
```

有趣的速记属性语法的副作用是，尽管后台状态成员由编译器生成的但它是不可访问除通过 set/get 访问器的类中。

## <a name="see-also"></a>请参阅

[类或接口中的成员声明 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[属性](../windows/property-cpp-component-extensions.md)