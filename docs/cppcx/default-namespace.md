---
title: "default 命名空间 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "default_CPP"
dev_langs: 
  - "C++"
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# default 命名空间
`default` 命名空间限定 [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) 支持的内置类型的范围。  
  
## 语法  
  
```  
namespace default;  
```  
  
## 成员  
 所有内置类型都继承以下成员。  
  
|||  
|-|-|  
|[default::\(type\_name\)::Equals 方法](../cppcx/default-type-name-equals-method.md)|确定指定的对象是否等于当前对象。|  
|[default::\(type\_name\)::GetHashCode 方法](../cppcx/default-type-name-gethashcode-method.md)|返回此实例的哈希代码。|  
|[default::\(type\_name\)::GetType 方法](../cppcx/default-type-name-gettype-method.md)|返回表示当前类型的字符串。|  
|[default::\(type\_name\)::ToString 方法](../cppcx/default-type-name-tostring-method.md)|返回表示当前类型的字符串。|  
  
### 内置类型  
  
|名称|描述|  
|--------|--------|  
|`char16`|表示 Unicode \(UTF\-16\) 码位的 16 位非数字值。|  
|`float32`|32 位 IEEE 754 浮点数。|  
|`float64`|64 位 IEEE 754 浮点数。|  
|`int16`|16 位带符号整数。|  
|`int32`|32 位带符号整数。|  
|`int64`|64 位带符号整数。|  
|`int8`|8 位带符号数值。|  
|`uint16`|16 位无符号整数。|  
|`uint32`|32 位无符号整数。|  
|`uint64`|64 位无符号整数。|  
|`uint8`|8 位无符号数值。|  
  
## 要求  
 **标头：**vccorlib.h  
  
## 请参阅  
 [Visual C\+\+ 语言参考](../cppcx/visual-c-language-reference-c-cx.md)