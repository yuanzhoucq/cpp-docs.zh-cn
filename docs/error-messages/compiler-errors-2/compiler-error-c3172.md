---
title: "编译器错误 C3172 | Microsoft Docs"
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
  - "C3172"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3172"
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3172
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“module\_name”: 在一个项目中无法指定不同的 idl\_module 特性  
  
 在一次编译中的两个文件内发现了名称相同、但 `dllname` 或 `version`参数不同的 [idl\_module](../../windows/idl-module.md) 特性。  每次编译只能指定一个唯一的 `idl_module` 特性。  
  
 可在一个以上的源代码文件中指定相同的 `idl_module` 特性。  
  
 例如，如果找到以下 `idl_module` 特性：  
  
```  
// C3172.cpp  
[module(name="MyMod")];  
[ idl_module(name="x", dllname="file.dll", version="1.1") ];  
int main() {}  
```  
  
 然后，  
  
```  
// C3172b.cpp  
// compile with: C3172.cpp  
// C3172 expected  
[ idl_module(name="x", dllname="file.dll", version="1.0") ];  
```  
  
 编译器将生成 C3172（注意不同的版本值）。