---
title: "类型转发 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "类型转发, Visual C++"
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 类型转发 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*类型转发* 可以将从一个程序集 \(程序集 A\) 的类型到另一个程序集 \(程序集 B\)，这样中，重新编译使用程序集 A. 的客户端是不必要的。  
  
## 所有平台  
 此功能在中任何没有运行时支持。  
  
## Windows Runtime — Windows 运行时  
 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 不支持此功能。  
  
### 要求  
 编译器选项：**\/ZW**  
  
## 公共语言运行时  
 下面的代码示例演示如何在 MDI 中使用控件。  
  
### 语法  
  
```  
#using "new.dll"  
[assembly:TypeForwardedTo(type::typeid)];  
```  
  
### 参数  
 `new`  
 将类型定义的程序集。  
  
 `type`  
 要移动到另一个程序集中的类型定义。  
  
### 备注  
 在和客户端应用程序使用组件 \(程序集\) 之后计时器，可以使用类型转发将从组件 \(程序集\) 的类型的另一程序集 \(和任何其他组件，提供更新的程序集需要\)，并且，客户端应用程序将运行，而未经重新编译。  
  
 传输组件的类型仅适用于引用由现有的应用程序。  当重新生成应用程序时，必须在应用程序的任何类型相应的程序集引用。  
  
 在传输类型 \(从程序集 A 的类型\)，则必须添加该类型的 `TypeForwardedTo` 特性，以及程序集引用。  所引用的程序集必须包含以下操作之一：  
  
-   A. 类型的定义。  
  
-   类型中的一个 `TypeForwardedTo` 特性，以及程序集引用。  
  
 可以正向包括类型的示例：  
  
-   ref classes  
  
-   value classes  
  
-   枚举  
  
-   接口  
  
 不可以将以下类型：  
  
-   泛型类型  
  
-   本机类型。  
  
-   嵌套类型 \(如果要转发嵌套类型，应该将封闭的类型\)  
  
 您可以将类型转换采用任何语言编写的程序集面向公共语言运行时。  
  
 因此，用于生成 A.dll，如果程序集的源代码文件包含一个类型定义 \(`ref class MyClass`\) 以及要将该类型定义移到程序集时，您将：  
  
1.  移动 `MyClass` 类型定义移到用于的源代码文件生成 B.dll。  
  
2.  生成 B.dll 程序集  
  
3.  删除使用的源代码中 `MyClass` 类型定义生成 A.dll，然后用以下代码替换它：  
  
    ```  
    #using "B.dll"  
    [assembly:TypeForwardedTo(MyClass::typeid)];  
    ```  
  
4.  生成 A.dll 任务程序集。  
  
5.  使用 A.dll，而不必重新编译该客户端应用程序。  
  
### 要求  
 编译器选项：**\/clr**