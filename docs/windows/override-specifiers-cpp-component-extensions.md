---
title: "重写说明符（C++ 组件扩展） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "重写说明符, Visual C++"
  - "重写说明符"
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 重写说明符（C++ 组件扩展）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“重写说明符”修改继承类型和继承类型成员在派生类型中的行为方式。  
  
## 所有运行时  
 **备注**  
  
 有关重写说明符的详细信息，请参阅：  
  
-   [abstract](../windows/abstract-cpp-component-extensions.md)  
  
-   [新（vtable 中的新槽）](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
-   [override](../windows/override-cpp-component-extensions.md)  
  
-   [sealed](../windows/sealed-cpp-component-extensions.md)  
  
-   [重写说明符和本机编译](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)  
  
 `abstract` 和 `sealed` 也对类型声明有效，在类型声明中它们不用作重写说明符。  
  
 有关显式重写基类函数的信息，请参阅[显式重写](../windows/explicit-overrides-cpp-component-extensions.md)。  
  
## Windows 运行时  
 \(此语言功能没有只适用于 Windows 运行时的备注。）  
  
### 要求  
 编译器选项：**\/ZW**  
  
## 公共语言运行时  
 （此语言功能没有只适用于公共运行时的备注。）  
  
### 要求  
 编译器选项：**\/clr**  
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)