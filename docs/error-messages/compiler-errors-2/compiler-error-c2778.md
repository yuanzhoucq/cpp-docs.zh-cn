---
title: "编译器错误 C2778 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2778"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2778"
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2778
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\_\_declspec\(uuid\(\)\) 中的 GUID 格式不正确  
  
 将错误的 GUID 提供给了 [uuid](../../cpp/uuid-cpp.md) 扩展特性。  
  
 GUID 必须是下列格式的十六进制数字字符串：  
  
```  
// C2778a.cpp  
// compile with: /c  
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};  
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};  
```  
  
 `uuid` 扩展特性接受 [CLSIDFromString](http://msdn.microsoft.com/library/windows/desktop/ms680589) 识别的字符串，带或不带大括号分隔符均可。  
  
 下面的示例生成 C2778：  
  
```  
// C2778b.cpp  
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778  
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778  
```