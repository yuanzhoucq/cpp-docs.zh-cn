---
title: "Understanding Backus Nauer Form (BNF) Syntax | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Backus Nauer Form (BNF) syntax"
  - "BNF notation"
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Understanding Backus Nauer Form (BNF) Syntax
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用BNF语法，ATL控制器使用的脚本本主题中所述，使用下表中显示的表示形式。  
  
|常规\/符号|含义|  
|------------|--------|  
|`::=`|等效项|  
|`&#124;`|OR|  
|`X+`|一个或多 `X`s。|  
|`[X]`|`X` 是可选项。  选项分隔符由 `[]`表示。|  
|任何 **bold** 文本|字符串。|  
|任何 *斜体* 文本|如何构造字符串。|  
  
 如上表所示，管理员脚本使用字符串。  这些值是必须出现在您的脚本的实际文本。  下表描述了在ATL注册器脚本的字符串。  
  
|字符串|操作|  
|---------|--------|  
|**ForceRemove**|完全移除下键\(如果存在\)然后重新创建它。|  
|**NoRemove**|在注册过程中，不移除下密钥。|  
|**val**|指定 `<Key Name>` 实际上是命名值。|  
|**Delete**|在注册过程中，删除下密钥。|  
|**s**|指定下一个值是字符串\(**REG\_SZ**）。|  
|**d**|指定下该值为 **DWORD** \(**REG\_DWORD**）。|  
|**m**|指定下该值为multistring \(**REG\_MULTI\_SZ**）。|  
|**b**|指定下一个值是二进制值\(**REG\_BINARY**）。|  
  
## BNF语法示例  
 这是帮助您的几个语法示例了解表示法和字符串如何在ATL注册器脚本工作。  
  
### 语法示例1  
  
```  
<registry expression> ::= <Add Key>  
```  
  
 指定 `registry expression` 与 `Add Key`等效。  
  
### 语法示例2  
  
```  
<registry expression> ::= <Add Key> | <Delete Key>  
```  
  
 指定 `registry expression` 与 `Add Key` 或 `Delete Key`等效。  
  
### 语法示例3  
  
```  
<Key Name> ::= '<AlphaNumeric>+'  
```  
  
 指定 `Key Name` 与一个或多 `AlphaNumerics`等效。  
  
### 语法示例4  
  
```  
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>  
```  
  
 指定 `Add Key` 与 `Key Name`是等效的，因此，字符串，`ForceRemove`、 `NoRemove`和 `val`，是可选的。  
  
### 语法示例5  
  
```  
<AlphaNumeric> ::= any character not NULL, that is, ASCII 0  
```  
  
 指定 `AlphaNumeric` 与任何非null字符是等效的。  
  
### 语法示例6  
  
```  
val 'testmulti' = m 'String 1\0String 2\0'  
```  
  
 指定键名 `testmulti` 是一个multistring的值的方法 `String 1` 和 `String 2`。  
  
### 语法示例7  
  
```  
val 'testhex' = d '&H55'  
```  
  
 指定键名 `testhex` 是 **DWORD** 值设置为十六进制55 \(十进制85）。  请注意此格式遵循 **&H** 表示法在Visual Basic规范中。  
  
## 请参阅  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)