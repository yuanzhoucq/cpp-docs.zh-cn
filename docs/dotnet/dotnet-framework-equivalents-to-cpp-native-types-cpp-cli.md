---
title: "对应于 C++ 本机类型的 .NET Framework 类型 (C++/CLI) | Microsoft Docs"
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
helpviewer_keywords: 
  - ".NET Framework [C++], C++ 等效项"
ms.assetid: 7f116a9a-26cd-46db-9877-a63ffdc88723
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 对应于 C++ 本机类型的 .NET Framework 类型 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表显示了内置 Visual C\+\+ 类型的关键字，这些类型是 **System** 命名空间中预定义类型的别名。  
  
|Visual C\+\+ 类型|.NET Framework 类型|  
|---------------------|-----------------------|  
|**bool**|**System.Boolean**|  
|**signed char**（有关更多信息，请参见 [\/J](../build/reference/j-default-char-type-is-unsigned.md)）|**System.SByte**|  
|**unsigned char**|**System.Byte**|  
|**wchar\_t**|**System.Char**|  
|**double** 和 **long double**|**System.Double**|  
|**float**|**System.Single**|  
|**int**、**signed int**、**long** 和 **signed long**|**System.Int32**|  
|**unsigned int** 和 **unsigned long**|**System.UInt32**|  
|**\_\_int64** 和 **signed \_\_int64**|**System.Int64**|  
|**unsigned \_\_int64**|**System.UInt64**|  
|**short** 和 **signed short**|**System.Int16**|  
|**unsigned short**|**System.UInt16**|  
|**void**|**System.Void**|  
  
## 请参阅  
 [托管类型](../dotnet/managed-types-cpp-cli.md)