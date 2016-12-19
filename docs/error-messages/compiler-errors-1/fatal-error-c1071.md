---
title: "错误 C1071 | Microsoft Docs"
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
  - "C1071"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1071"
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1071
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在注释中遇到意外的文件结束  
  
 编译器在扫描注释时到达了文件尾。  
  
### 通过检查以下可能的原因进行修复  
  
1.  缺少注释结束符 \(\*\/\)。  
  
2.  源文件最后一行的注释后缺少换行符。  
  
 下面的示例生成 C1071：  
  
```  
// C1071.cpp  
int main() {  
}  
  
/* this comment is fine */  
/* forgot the closing tag        // C1071  
```