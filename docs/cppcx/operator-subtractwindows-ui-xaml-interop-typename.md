---
title: "运算符 Windows::UI::Xaml::Interop::TypeName | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# 运算符 Windows::UI::Xaml::Interop::TypeName
实现从 `Platform::Type` 到 [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) 的转换。  
  
## 语法  
  
```cpp  
Operator TypeName(Platform::Type^ type)  
```  
  
## 返回值  
 给定 `Platform::Type^` 时返回 [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx)。  
  
## 备注  
 `TypeName` 是表示类型信息的中性语言 Windows 运行时结构。[Platform::Type](../cppcx/platform-type-class.md) 特定于 C\+\+，无法通过应用程序二进制接口 \(ABI\) 传递。 下面是 `TypeName` 在 [Navigate](http://msdn.microsoft.com/library/windows/apps/hh702394.aspx) 函数中的一种用法：  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
## 示例  
 下一示例演示如何在 `TypeName` 和`Type` 之间转换。  
  
```  
  
// Convert from Type to TypeName Windows::UI::Xaml::Interop::TypeName tn = TypeName(MainPage::typeid); // Convert back from TypeName to Type Type^ tx2 = (Type^)(tn);  
  
```  
  
## .NET Framework 等效项  
 .NET Framework 程序将 `TypeName` 投影为 [System.Type](assetId:///System.Type?qualifyHint=False&amp;autoUpgrade=True)。  
  
## 要求  
  
## 请参阅  
 [operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-subtractwindows-ui-xaml-interop-typename.md)   
 [Platform::Type 类](../cppcx/platform-type-class.md)