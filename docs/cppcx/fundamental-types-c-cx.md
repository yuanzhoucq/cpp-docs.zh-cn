---
title: "基本类型 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
caps.latest.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 14
---
# 基本类型 (C++/CX)
除了标准 C\+\+ 内置类型之外，[!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) 还通过为映射到标准 C\+\+ 类型的 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 基本类型提供 typedef，来支持 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 体系结构定义的类型系统。[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 实现了布尔值、字符和数值基本类型。 这些 typedef 在永远不需要显式指定的 `default` 命名空间中进行定义。 此外，[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 为某些 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 类型和接口提供了包装和具体实现。  
  
## 布尔值和字符类型  
 下表列出了内置布尔值和字符类型及其的标准 C\+\+ 等效项。  
  
|命名空间|[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 名称|定义|标准 C\+\+ 名称|值的范围|  
|----------|---------------------------------------------------------------------|--------|-----------------|----------|  
|平台|Boolean|8 位布尔值。|bool|`true`（非零）和 `false`（零）|  
|default|char16|表示 Unicode \(UTF\-16\) 码位的 16 位非数字值。|wchar\_t<br /><br /> \- 或 \-<br /><br /> L'c'|（由 Unicode 标准指定）|  
  
## 数值类型  
 下表列出了内置数值类型。 数值类型在 `default` 命名空间中进行声明，是用于对应 C\+\+ 内置类型的 typedef。[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 中并不支持所有 C\+\+ 内置类型（例如 long）。 为了保持一致并简单明了，建议使用 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 名称。  
  
|[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 名称|定义|标准 C\+\+ 名称|值的范围|  
|---------------------------------------------------------------------|--------|-----------------|----------|  
|int8|8 位带符号数值。|signed char|–128 到 127|  
|uint8|8 位无符号数值。|unsigned char|0 到 255|  
|int16|16 位带符号整数。|short|–32,768 到 32,767|  
|uint16|16 位无符号整数。|unsigned short|0 到 65,535|  
|int32|32 位带符号整数。|int|–2,147,483,648 到 2,147,483,647|  
|uint32|32 位无符号整数。|unsigned int|0 到 4,294,967,295|  
|int64|64 位带符号整数。|long long 或 \_\_int64|–9,223,372,036,854, 775,808 到 9,223,372,036,854,775,807|  
|uint64|64 位无符号整数。|unsigned long long 或 unsigned \_\_int64|0 到 18,446,744,073,709,551,615|  
|float32|32 位 IEEE 754 浮点数。|float|3.4E \+\/\- 38（7 位数）|  
|float64|64 位 IEEE 754 浮点数。|double|1.7E \+\/\- 308（15 位数）|  
  
## [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 类型  
 下表列出了由 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 体系结构定义并内置在 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中的一些其他类型。 Object 和 String 是引用类型。 其他类型是值类型。 所有这些类型都在 `Platform` 命名空间中进行声明。 有关完整列表，请参见 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)。  
  
|名称|定义|  
|--------|--------|  
|对象|表示任何 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 类型。|  
|String|一系列表示文本的字符。|  
|Rect|一组浮点数，共四个，表示一个矩形的位置和大小。|  
|SizeT|指定高度和宽度的一对有序浮点数。|  
|点|定义二维平面中的点的一对有序浮点 x 坐标和 y 坐标。|  
|Guid|用作唯一标识符的 128 位非数字值。|  
|UIntPtr|（仅限内部使用。） 用作指针的 64 位无符号值。|  
|IntPtr|（仅限内部使用。）  用作指针的 64 位带符号值。|  
  
## 请参阅  
 [类型系统](../cppcx/type-system-c-cx.md)