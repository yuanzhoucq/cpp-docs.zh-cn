---
title: 'Platform:: type 类 |Microsoft 文档'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
dev_langs:
- C++
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bc70f0a0f714cb6f5a2f4b28d922308d8fe4d645
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="platformtype-class"></a>Platform::Type 类
包含有关类型的运行时信息，尤其是字符串名称和类型代码。 通过调用获取[object:: gettype](../cppcx/platform-object-class.md#gettype)任何对象或使用[typeid](../windows/typeid-cpp-component-extensions.md)运算符的类或结构的名称。  
  
## <a name="syntax"></a>语法  
  
```cpp  
public ref class Platform::Type :      
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable  
```  
  
### <a name="remarks"></a>备注  
 对于必须使用基于对象的运行时类型进行分支的 `Type` 或 `if` 语句来直接处理的应用程序， `switch` 类非常有用。 描述类型类别的类型代码通过使用[type:: gettypecode](#gettypecode)成员函数。  
  
## <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|[Type::GetTypeCode 方法](#gettypecode)|返回对象的 [Platform::TypeCode 枚举](../cppcx/platform-typecode-enumeration.md) 值。| 
|[Type::ToString 方法](#tostring)|返回其元数据中指定类型的名称。| 

 
## <a name="public-properties"></a>公共属性  
  
|||  
|-|-|  
|[Type::FullName](#fullname)|返回表示类型的完全限定名称的 [Platform::String 类](../cppcx/platform-string-class.md)^，并使用 . （点） 作为分隔符，不:: （双冒号） — 例如， `MyNamespace.MyClass`。|  
  
## <a name="conversion-operators"></a>转换运算符  
  
|||  
|-|-|  
|[运算符 Type^](../cppcx/operator-type-hat.md)|实现从 `Windows::UI::Xaml::Interop::TypeName` 到 `Platform::Type`的转换。|  
|[运算符 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)|实现从 `Platform::Type` 到 `Windows::UI::Xaml::Interop::TypeName`的转换。|  
  
### <a name="requirements"></a>要求  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform  
  
 **元数据：** platform.winmd  

 
## <a name="fullname"></a> Type::FullName 属性
检索窗体中的当前类型的完全限定名称`Namespace.Type`。  
  
### <a name="syntax"></a>语法  
  
```cpp  
String^ FullName();  
```  
  
### <a name="return-value"></a>返回值  
 类型的名称。  
### <a name="example"></a>示例  
  
```  
  
//  namespace is TestApp  
MainPage::MainPage()  
{  
    InitializeComponent();  
    Type^ t = this->GetType();  
    auto s = t->FullName; // returns "TestApp.MainPage"  
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"  
}  
```  
  


## <a name="gettypecode"></a> Type::GetTypeCode 方法
检索内置类型数值类型类别。  
  
### <a name="syntax"></a>语法  
  
```cpp  
Platform::TypeCode GetTypeCode();  
```  
  
### <a name="return-value"></a>返回值  
 Platform::TypeCode 枚举值之一。  
  
### <a name="remarks"></a>备注  
 Gettypecode （） 成员方法等效于`typeid`属性。

## <a name="tostring"></a> Type::ToString 方法
检索类型的名称。  
  
### <a name="syntax"></a>语法  
  
```cpp  
Platform::String^ ToString();  
```  
  
### <a name="return-value"></a>返回值  
 作为其元数据中指定类型的名称。    
  
## <a name="see-also"></a>请参阅  
 [平台命名空间](../cppcx/platform-namespace-c-cx.md)