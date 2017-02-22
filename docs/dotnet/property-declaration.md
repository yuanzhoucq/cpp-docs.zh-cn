---
title: "属性声明 | Microsoft Docs"
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
  - "__property 关键字"
  - "声明属性, C++"
  - "property 关键字 [C++]"
ms.assetid: de169378-a8b8-49f4-a586-76bffc9b5c9f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 属性声明
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，在托管类中声明属性的方式已发生了更改。  
  
 在托管扩展设计中，将各个 `set` 或 `get` 属性访问器指定为独立的方法。  各个方法的声明以 `__property` 关键字作为前缀。  方法名称以 `set_` 或 `get_` 后跟属性的实际名称（如向用户显示的一样）开头。  因此，提供 `x` 坐标 `get` 属性的 `Vector` 将其命名为 `get_x`，用户如调用 `x` 一样调用它。  此命名约定和方法的分隔规范实际上反映了属性的基础运行时实现。  例如，下面是具有一组坐标属性的 `Vector`：  
  
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
  
 这可以扩展与属性相关的功能，并要求用户在词汇上统一关联的 set 和 get。  此外，其内容是详细的。  在新语法中，`property` 关键字后跟属性的类型及其原来的名称，这与 C\# 更类似。  `set` 和 `get` 访问方法放置在属性名称后面的某块内。  请注意，与 C\# 不同，新语法中指定了访问方法的签名。  例如，下面是上述代码示例转换为新语法后的代码。  
  
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
  
 如果属性的访问方法反映了截然不同的访问级别 — 如 `public` `get` 和 `private` 或 `protected` `set`，则可指定显式访问标签。  默认情况下，属性的访问级别反映封闭访问级别。  例如，在上述 `Vector` 的定义中，`get` 和 `set` 方法是 `public`。  若要使 `set` 方法为 `protected` 或 `private`，将定义修改为如下所示：  
  
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
  
   } // note: extent of private culminates here …  
  
// note: dot is a public method of Vector  
double dot( const Vector^ wv );  
  
// etc.  
};  
```  
  
 属性内的访问关键字的范围扩展到了属性的右大括号或其他访问关键字的规范。  此范围不扩展超出属性的定义到在其中定义属性的封闭访问级别。  例如，在上述声明中，`Vector::dot()` 是一个公共方法。  
  
 编写三个 `Vector` 坐标的 set\/get 属性分三个步骤：  
  
1.  声明适当类型的私有状态成员。  
  
2.  在用户希望获取其值时返回它。  
  
3.  为其分配新值。  
  
 在新的语法中，简写属性语法可用来自动化此使用模式：  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   property double x;   
   property double y;  
   property double z;  
};  
```  
  
 简写属性语法有趣的副作用是：虽然编译器生成后台状态成员，但它在类内是无法访问的（除非通过 set\/get 访问器访问）。  
  
## 请参阅  
 [类或接口中的成员声明 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [属性](../windows/property-cpp-component-extensions.md)