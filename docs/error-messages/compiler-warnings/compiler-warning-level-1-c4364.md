---
title: "编译器警告（等级 1）C4364 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4364"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4364"
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 1）C4364
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以前在 location\(line\_number\) 上看到“file”程序集的 \#using 没有 as\_friend 特性；未应用 as\_friend  
  
 `#using` 指令对给定的元数据文件重复，但是在第一个匹配项中没有使用该 `as_friend` 限定符；编译器将忽略第二个 `as_friend`。  
  
 有关详细信息，请参阅[友元程序集 \(C\+\+\)](../../dotnet/friend-assemblies-cpp.md)。  
  
## 示例  
 下面的示例创建了一个组件。  
  
```  
// C4364.cpp  
// compile with: /clr /LD  
ref class A {};  
```  
  
## 示例  
 下面的示例生成 C4364。  
  
```  
// C4364_b.cpp  
// compile with: /clr /W1 /c  
#using " C4364.dll"  
#using " C4364.dll" as_friend   // C4364  
```