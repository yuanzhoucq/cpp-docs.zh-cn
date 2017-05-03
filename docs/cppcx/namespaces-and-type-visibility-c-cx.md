---
title: "命名空间和类型可见性 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cbc01a3a-3b69-4ded-9c42-ecbf0fd0a00e
caps.latest.revision: 13
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 13
---
# 命名空间和类型可见性 (C++/CX)
命名空间为标准 C\+\+ 构造，用于分组具有相关功能的类型和阻止库中发生名称冲突。[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型系统要求必须在命名空间范围内的命名空间中声明所有公共 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型（包括您自己的代码中的那些类型）。 在全局范围内声明的或嵌套在其他类中的公共类型将导致编译时错误。  
  
 .winmd 文件必须具有和根命名空间相同的名称。 例如，名为 A.B.C.MyClass 的类只有在名为 A.winmd 或 A.B.winmd 或 A.B.C.winmd 的元数据文件中定义后才能实例化。 可执行文件的名称不必与 .winmd 文件名匹配。  
  
## 类型可见性  
 在命名空间中，[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 类型（不同于标准 C\+\+ 类型）具有私有或公共可访问性。 默认情况下，可访问性是私有的。 仅公共类型对元数据可见，因此可以从可能用 C\+\+ 之外的语言编写的应用程序和组件使用该类型。 通常，可见类型的规则比不可见类型的规则具有更强的限制，因为可见类型无法公开在 .NET 语言或 JavaScript 中不受支持的 C\+\+ 特定的概念。  
  
> [!NOTE]
>  元数据仅在运行时由 .NET 语言和 JavaScript 使用。 如果一个 C\+\+ 应用程序或组件与另一个 C\+\+ 应用程序或组件（这包括用 C\+\+ 编写的 Windows 组件）通信，则无需在运行时使用元数据。  
  
## 成员可访问性和可见性  
 在私有 ref 类、接口或委托中，不会将成员发送到元数据，即使它们具有公共可访问性。 在公共 ref 类中，您可以独立于成员在源代码中的可访问性控制成员在元数据中的可见性。 与在标准 C\+\+ 中一样，应用最小特权原则；除非成员必须可见，否则不要使成员在元数据中可见。  
  
 使用以下访问修饰符控制元数据可见性和源代码可访问性。  
  
||||  
|-|-|-|  
|修饰符|含义|是否发送到元数据|  
|private|默认可访问性。 与在标准 C\+\+ 中的含义一样。|No|  
|protected|与在标准 C\+\+ 中的含义一样（在应用程序或组件中以及元数据中）。|是|  
|public|与在标准 C\+\+ 中的含义一样。|是|  
|`public protected` –或\- `protected public`。|元数据中的受保护的可访问性，应用程序或组件中的公共可访问性。|是|  
|`protected private` 或 `private protected`|在元数据中不可见；应用程序或组件中的受保护的可访问性。||  
|`internal` 或 `private public`|成员在应用程序或组件中是公共的，但在元数据中不可见。|No|  
  
## [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 命名空间  
 Windows API 由在 Windows::\* 命名空间中声明的类型组成。 这些命名空间为 Windows 所保留，因此，不能在其中添加类型。 在**“对象浏览器”**中，您可以在 windows.winmd 文件中查看这些命名空间。 有关这些命名空间的文档，请参见 [Windows API](http://msdn.microsoft.com/library/windows/apps/br211377)。  
  
## [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 命名空间  
 [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) 定义这些命名空间中的某些类型作为 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 类型系统投影的一部分。  
  
|||  
|-|-|  
|**命名空间**|**描述**|  
|default|包含内置数值和 char16 类型。 这些类型在每个命名空间的范围中，而且从来不需要 `using` 语句。|  
|平台|包含对应于 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型（如 `Array<T>`、`String`、`Guid` 和 `Boolean`）的主要公共类型。 另外还包括专用帮助程序类型（如 `Platform::Agile<T>` 和 `Platform::Box<T>`）。|  
|Platform::Collections|包含实现 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]集合接口 `IVector`、`IMap` 等的具体集合类。 这些类型在标头文件 collection.h 而非 platform.winmd 中定义。|  
|Platform::Details|包含编译器使用而不适合公共使用的类型。|  
  
## 请参阅  
 [类型系统 \(C\+\+\/CX\)](../cppcx/type-system-c-cx.md)