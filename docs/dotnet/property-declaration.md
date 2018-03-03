---
title: "属性声明 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- __property keyword
- declaring properties, C++
- property keyword [C++]
ms.assetid: de169378-a8b8-49f4-a586-76bffc9b5c9f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c047e1efbe030591e26fb410c9b2df254734e08b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="property-declaration"></a>属性声明
声明托管类中的属性的方法已从托管扩展中的 c + + 更改为 Visual c + +。  
  
 在托管扩展设计时，每个`set`或`get`属性访问器指定为独立的方法。 每个方法声明中的前面带`__property`关键字。 方法名称开头`set_`或`get_`跟 （形式对用户可见） 的属性的实际名称。 因此，`Vector`提供`x`协调`get`属性将对其进行命名`get_x`和用户一样调用它`x`。 此命名约定和方法的单独规范实际反映的基础运行时实现的属性。 例如，下面是我们`Vector`与一组坐标属性：  
  
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
  
 这可以扩展与属性相关联的功能，并要求用户从词法上统一的关联的集和获取。 而且，它更为详细。 在新语法中，这是更类似的 C#，`property`关键字后跟的属性和其未修饰的名称的类型。 `set`和`get`访问方法放置在属性名称后面的块内。 请注意，与不同的是 C# 中，指定访问方法的签名。 例如，下面是上面的代码示例转换为新的语法。  
  
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
  
 如果该属性的访问方法反映截然不同的访问级别-如`public get`和`private`或`protected set`，可以指定一个显式访问权限的标签。 默认情况下，该属性的访问级别反映的封闭的访问级别。 例如，在上面的定义的`Vector`，这两个`get`和`set`方法`public`。 若要使`set`方法`protected`或`private`，定义将进行如下修改：  
  
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
  
 属性内的访问关键字的作用域扩展到属性的右大括号或其他访问关键字的规范。 它未超出在其中定义的属性的封闭访问级别的属性的定义。 在上面的声明中，例如，`Vector::dot()`是一个公共方法。  
  
 编写这三个 set/get 属性`Vector`坐标包括三个步骤：  
  
1.  声明适当类型的私有状态成员。  
  
2.  当用户想要获取其值，则将其返回。  
  
3.  将其分配新值。  
  
 在新语法中，一种速记属性语法是可用来自动化此使用模式：  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   property double x;   
   property double y;  
   property double z;  
};  
```  
  
 速记属性语法的有趣副作用是，尽管 backstage 状态成员由编译器生成的它不是在除通过组/get 访问器的类中访问。  
  
## <a name="see-also"></a>请参阅  
 [在类或接口中的成员声明 (C + + /cli CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [属性](../windows/property-cpp-component-extensions.md)