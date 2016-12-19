---
title: "链接器工具错误 LNK1179 | Microsoft Docs"
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
  - "LNK1179"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1179"
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK1179
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无效或损坏的文件: 重复的 COMDAT“filename”  
  
 对象模块包含两个或更多同名的 COMDAT。  
  
 使用 [\/H](../../build/reference/h-restrict-length-of-external-names.md)（用于限制外部名称长度）和 [\/Gy](../../build/reference/gy-enable-function-level-linking.md)（用于将函数打包到 COMDAT 中）将导致此错误。  
  
## 示例  
 在下面的代码中，`function1` 和 `function2` 的前八个字符相同。  用 **\/Gy** 和 **\/H8** 进行编译将产生链接错误。  
  
```  
void function1(void);  
void function2(void);  
  
int main() {  
    function1();  
    function2();  
}  
  
void function1(void) {}  
void function2(void) {}  
```