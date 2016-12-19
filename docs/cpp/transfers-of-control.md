---
title: "控制的转移 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控制流, 分支"
  - "控制流, 传输控制"
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 控制的转移
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以在 `goto` 语句中使用  **语句或 `switch`case** 标签来指定分支超出初始值设定项的程序。  此类代码是非法的，除非包含初始值设定项的声明在跳转语句发生的块所封闭的块中。  
  
 下面的示例显示了声明和初始化对象 `total`、`ch` 和 `i` 的循环。  也存在将控制权传递过初始值设定项的错误 `goto` 语句。  
  
```  
// transfers_of_control.cpp  
// compile with: /W1  
// Read input until a nonnumeric character is entered.  
int main()  
{  
   char MyArray[5] = {'2','2','a','c'};  
   int i = 0;  
   while( 1 )  
   {  
      int total = 0;  
  
      char ch = MyArray[i++];  
  
      if ( ch >= '0' && ch <= '9' )  
      {  
         goto Label1;  
  
         int i = ch - '0';  
      Label1:  
         total += i;   // C4700: transfers past initialization of i.  
      } // i would be destroyed here if  goto error were not present  
   else  
      // Break statement transfers control out of loop,  
      //  destroying total and ch.  
      break;  
   }  
}  
```  
  
 在前面的示例中，`goto` 语句尝试将控制权传递过 `i` 的初始化。  但是，如果已声明但未初始化 `i`，则该传递是合法的。  
  
 在用作 `total` 语句的 `ch`statement 的块中声明的对象  *和 `while` 在使用 `break` 语句退出此块时将被销毁。*  
  
## 请参阅  
 [\(NOTINBUILD\) Declaration of Automatic Objects](http://msdn.microsoft.com/zh-cn/81f941e9-c1b1-4d1c-a28d-70b6ee9765db)