---
title: "使用 exit 或 return | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Exit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exit 函数"
  - "return 关键字 [C++], 用于程序终止"
ms.assetid: b5136c5c-2505-4229-8691-2a1d6a98760b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 使用 exit 或 return
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在从 **main** 调用 **exit** 或执行 `return` 语句时，静态对象将以与其初始化相反的顺序被销毁。  以下示例演示如何进行此类初始化和清理工作。  
  
## 示例  
  
```  
// using_exit_or_return1.cpp  
#include <stdio.h>  
class ShowData {  
public:  
   // Constructor opens a file.  
   ShowData( const char *szDev ) {  
   errno_t err;  
      err = fopen_s(&OutputDev, szDev, "w" );  
   }  
  
   // Destructor closes the file.  
   ~ShowData() { fclose( OutputDev ); }  
  
   // Disp function shows a string on the output device.  
   void Disp( char *szData ) {   
      fputs( szData, OutputDev );  
   }  
private:  
   FILE *OutputDev;  
};  
  
//  Define a static object of type ShowData. The output device  
//   selected is "CON" -- the standard output device.  
ShowData sd1 = "CON";  
  
//  Define another static object of type ShowData. The output  
//   is directed to a file called "HELLO.DAT"  
ShowData sd2 = "hello.dat";  
  
int main() {  
   sd1.Disp( "hello to default device\n" );  
   sd2.Disp( "hello to file hello.dat\n" );  
}  
```  
  
 在前面的示例中，在进入 `main` 之前，将创建和初始化静态对象 `sd1` 和 `sd2`。  使用 `return` 语句终止此程序后，首先销毁 `sd2`，然后销毁 `sd1`。  `ShowData` 类的析构函数将关闭与这些静态对象关联的文件。（有关初始化、构造函数和析构函数的详细信息，请参阅[特殊成员函数](../misc/special-member-functions-cpp.md)。）  
  
 另一种编写此代码的方式为，使用块范围声明 `ShowData` 对象，并允许在它们超出范围时将其销毁：  
  
```  
int main() {  
   ShowData sd1, sd2( "hello.dat" );  
  
   sd1.Disp( "hello to default device\n" );  
   sd2.Disp( "hello to file hello.dat\n" );  
}  
```  
  
## 请参阅  
 [附加终止注意事项](../cpp/additional-termination-considerations.md)