---
title: "detect_mismatch | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.detect_mismatch"
  - "detect_mismatch_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "detect_mismatch 杂注"
  - "杂注, detect_mismatch"
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# detect_mismatch
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将记录放在一个对象中。  链接器将检查这些记录中的潜在不匹配项。  
  
## 语法  
  
```  
#pragma detect_mismatch( "name", "value"))  
```  
  
## 备注  
 链接项目时，如果项目包含 `name` 相同但 `value` 不同的两个对象，则链接器将引发 `LNK2038` 错误。  使用此杂注可防止链接中存在不一致的对象文件。  
  
 名称和值都是字符串，它们遵循关于转义字符和串联的字符串规则。  它们区分大小写，并且不能包含逗号、等号、引号或 `null` 字符。  
  
## 示例  
 此示例将创建版本标签相同但版本号不同的两个文件。  
  
```  
// pragma_directive_detect_mismatch_a.cpp  
#pragma detect_mismatch("myLib_version", "9")  
int main ()  
{  
   return 0;  
}  
  
// pragma_directive_detect_mismatch_b.cpp  
#pragma detect_mismatch("myLib_version", "1")  
```  
  
 如果使用命令行 `cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp` 编译这两个文件，则会收到错误 `LNK2038`。  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)