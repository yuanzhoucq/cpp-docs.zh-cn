---
title: "枚举 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
caps.latest.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 14
---
# 枚举 (C++/CX)
[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 支持 `public enum class` 关键字，该关键字类似于标准 C\+\+ `scoped  enum`。 当你使用通过 `public enum class` 关键字声明的枚举数时，必须使用枚举标识符确定每个枚举值的范围。  
  
## 备注  
 没有访问说明符（如 `public enum class`）的 `public` 将作为标准 C\+\+ [范围枚举](~/cpp/enumerations-cpp.md)处理。  
  
 `public enum class` 或 `public enum struct` 声明可以有任何整数类型的基础类型，尽管 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]本身要求类型是 int32 或者 uint32（对于标志枚举）。 以下语法描述 `public enum class` 或 `public enum struct` 的一部分。 有关详细信息，请参阅[enum class](~/windows/enum-class-cpp-component-extensions.md)。  
  
 此示例演示如何定义公共枚举类：  
  
 [!code-cpp[cx_enums#01](../snippets/cpp/VS_Snippets_Misc/cx_enums/cpp/class1.h#01)]  
  
 下一个示例演示如何使用枚举类：  
  
 [!code-cpp[cx_enums#02](../snippets/cpp/VS_Snippets_Misc/cx_enums/cpp/class1.h#02)]  
  
## 示例  
 后续示例演示如何声明枚举。  
  
 [!code-cpp[cx_enums#03](../snippets/cpp/VS_Snippets_Misc/cx_enums/cpp/class1.h#03)]  
  
 下一个示例演示如何强制转换为数字等效值和执行比较。 请注意，枚举数 `One` 的使用通过 `Enum1` 枚举标识符来确定范围，枚举数 `First` 通过 `Enum2` 来确定范围。  
  
 [!code-cpp[cx_enums#04](../snippets/cpp/VS_Snippets_Misc/cx_enums/cpp/class1.h#04)]  
  
## 请参阅  
 [类型系统](../cppcx/type-system-c-cx.md)   
 [Visual C\+\+ 语言参考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空间参考](../cppcx/namespaces-reference-c-cx.md)