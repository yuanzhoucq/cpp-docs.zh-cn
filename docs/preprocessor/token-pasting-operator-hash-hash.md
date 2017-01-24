---
title: "标记粘贴运算符 (##) | Microsoft Docs"
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
  - "##"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "## 预处理器运算符"
  - "预处理器, 运算符"
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
caps.latest.revision: 10
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 标记粘贴运算符 (##)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

双数字符号或“token\-pasting”运算符 \(**\#\#**\)（有时称为“合并”运算符）可在类似对象和类似函数的宏中使用。  它允许将不同的标记加入到单个标记中，因此不能是宏定义中的第一个或最后一个标记。  
  
 如果宏定义中的形参的前面或后面带有 token\-pasting 运算符，则会立即将形参替换为未扩展的实参。  在替换前将不会对参数执行宏扩展。  
  
 之后，将删除 *token\-string* 中出现的每个 token\-pasting 运算符，并将其前后的标记连接在一起。  生成的标记必须是有效的标记。  如果标记有效，则在它表示宏名称时扫描其中可能的替换。  标识符表示连接在一起的标记在替换前在程序中已知的名称。  每个标记表示在别处（在程序中或在编译器命令行上）定义的标记。  运算符前后的空白是可选的。  
  
 此示例演示了在指定程序输出时对 stringizing 和 token\-pasting 运算符的使用：  
  
```  
#define paster( n ) printf_s( "token" #n " = %d", token##n )  
int token9 = 9;  
```  
  
 如果使用类似如下的数值参数调用一个宏  
  
```  
paster( 9 );  
```  
  
 宏将生成  
  
```  
printf_s( "token" "9" " = %d", token9 );  
```  
  
 它将变为  
  
```  
printf_s( "token9 = %d", token9 );  
```  
  
## 示例  
  
```  
// preprocessor_token_pasting.cpp  
#include <stdio.h>  
#define paster( n ) printf_s( "token" #n " = %d", token##n )  
int token9 = 9;  
  
int main()  
{  
   paster(9);  
}  
```  
  
  **token9 \= 9**   
## 请参阅  
 [预处理器运算符](../preprocessor/preprocessor-operators.md)