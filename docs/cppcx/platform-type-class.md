---
title: "Platform::Type 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Type 类"
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Platform::Type 类
包含有关类型的运行时信息，尤其是字符串名称和类型代码。 通过对任何对象调用 [Object::GetType 方法](../cppcx/object-gettype-method.md)或者对类或结构名称使用 [typeid](~/windows/typeid-cpp-component-extensions.md) 运算符来获取。  
  
## 语法  
  
```cpp  
public ref class Platform::Type :      Platform::Object,      Platform::Details::IEquatable,      Platform::Details::IPrintable  
```  
  
## 备注  
 对于必须使用基于对象的运行时类型进行分支的 `Type` 或 `if` 语句来直接处理的应用程序，`switch` 类非常有用。 描述类型类别的类型代码通过使用 [Type::GetTypeCode 方法](../cppcx/type-gettypecode-method.md)成员函数进行检索。  
  
## 公共方法  
  
|||  
|-|-|  
|[Type::GetTypeCode 方法](../cppcx/type-gettypecode-method.md)|返回对象的 [Platform::TypeCode 枚举](../cppcx/platform-typecode-enumeration.md)值。|  
  
## 公共属性  
  
|||  
|-|-|  
|[Type::FullName 属性](../cppcx/type-fullname-property.md)|返回表示类型的完全限定名称的 [Platform::String 类](../cppcx/platform-string-class.md)^，并使用 . （点）而非 ::（双冒号）作为分隔符（如“MyNamespace.MyClass”）。|  
  
## 转换运算符  
  
|||  
|-|-|  
|[运算符 Type^](../cppcx/operator-subtracttype-hat.md)|实现从 `Windows::UI::Xaml::Interop::TypeName` 到 `Platform::Type` 的转换。|  
|[运算符 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-subtractwindows-ui-xaml-interop-typename.md)|实现从 `Platform::Type` 到 `Windows::UI::Xaml::Interop::TypeName` 的转换。|  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)