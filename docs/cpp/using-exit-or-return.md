---
title: 使用退出或返回 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
- return keyword [C++], using for program termination
ms.assetid: b5136c5c-2505-4229-8691-2a1d6a98760b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45885cc6dbac50a693bb84abb797469d8aff93a3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="using-exit-or-return"></a>使用 exit 或 return
当调用**退出**或执行`return`语句从**主要**，静态对象会被销毁其初始化的相反顺序。 以下示例演示如何进行此类初始化和清理工作。  
  
## <a name="example"></a>示例  
  
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
  
 在前面的示例中，在进入 `sd1` 之前，将创建和初始化静态对象 `sd2` 和 `main`。 使用 `return` 语句终止此程序后，首先销毁 `sd2`，然后销毁 `sd1`。 `ShowData` 类的析构函数将关闭与这些静态对象关联的文件。   
  
 另一种编写此代码的方式为，使用块范围声明 `ShowData` 对象，并允许在它们超出范围时将其销毁：  
  
```  
int main() {  
   ShowData sd1, sd2( "hello.dat" );  
  
   sd1.Disp( "hello to default device\n" );  
   sd2.Disp( "hello to file hello.dat\n" );  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [附加终止注意事项](../cpp/additional-termination-considerations.md)