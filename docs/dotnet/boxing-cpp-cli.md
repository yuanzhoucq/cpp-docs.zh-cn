---
title: "装箱 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 装箱 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

装箱是转换值类型的过程到类型 `object` 或为由值类型实现的任何接口类型。  在公共语言运行时 \(CLR\) \(CLR\) 对值类型进行装箱，但包装 `System.Object` 的值并将其存储在托管堆上。  取消装箱将从对象中提取值类型。  装箱是隐式的；取消装箱是显式的。  
  
## 相关文章  
  
|标题|说明|  
|--------|--------|  
|[如何：显式请求装箱](../dotnet/how-to-explicitly-request-boxing.md)|描述如何显式请求变量上的装箱。|  
|[如何：使用 gcnew 创建值类型并使用隐式装箱](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|演示如何使用 `gcnew` 创建在承载的装箱值类型，垃圾回收堆可以放置。|  
|[如何：取消装箱](../dotnet/how-to-unbox.md)|演示如何取消装箱和修改值。|  
|[标准转换和隐式装箱](../dotnet/standard-conversions-and-implicit-boxing.md)|表示标准转换，由在需要装箱转换的编译器选项。|  
|[使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Visual C\+\+ 进行编程的文档的" .NET 顶级文章。|