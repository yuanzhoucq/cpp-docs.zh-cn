---
title: "Object::GetType 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Object::GetType"
ms.assetid: f633d71a-ff80-49f9-931d-189c00b1f6c5
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Object::GetType 方法
返回描述对象的运行时类型的 [Platform::Type](../cppcx/platform-type-class.md) 对象。  
  
## 语法  
  
```vb  
Object::GetType()  
```  
  
```csharp  
  
```  
  
## 属性值\/返回值  
 描述对象的运行时类型的 [Platform::Type](../cppcx/platform-type-class.md) 对象。  
  
## 备注  
 静态 [Type::GetTypeCode 方法](../cppcx/type-gettypecode-method.md)可用于获取表示当前类型的 [Platform::TypeCode 枚举](../cppcx/platform-typecode-enumeration.md)值。 这对于内置类型通常很有用。 任何 ref 类（[Platform::String](../cppcx/platform-string-class.md) 除外）的类型代码均为对象 \(1\)。  
  
 [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) 类在 Windows API 中用作在 Windows 组件和应用之间传递类型信息的一种独立于语言的方式。 T[Platform::Type 类](../cppcx/platform-type-class.md) 具有用于在 `Type` 和 `TypeName` 之间进行转换的运算符。  
  
 使用 [typeid](~/windows/typeid-cpp-component-extensions.md) 运算符可返回类名称的 `Platform::Type` 对象，例如在 XAML 页面之间导航时：  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
## 请参阅  
 [Platform::Type 类](../cppcx/platform-type-class.md)   
 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)   
 [类型系统](../cppcx/type-system-c-cx.md)