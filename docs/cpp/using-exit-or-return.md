---
title: 使用退出或返回 |Microsoft Docs
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
ms.openlocfilehash: 47fb8ff09fc50557283a0f4e8ef0e159bc900e86
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39460940"
---
# <a name="using-exit-or-return"></a>使用 exit 或 return
当您调用**退出**或执行**返回**语句从`main`，静态对象与其初始化相反顺序被销毁。 以下示例演示如何进行此类初始化和清理工作。  
  
## <a name="example"></a>示例  
  
```cpp 
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
  
 在前面的示例中，在进入 `sd1` 之前，将创建和初始化静态对象 `sd2` 和 `main`。 使用此程序终止后**返回**语句中，第一个`sd2`销毁，然后`sd1`。 `ShowData` 类的析构函数将关闭与这些静态对象关联的文件。   
  
 另一种编写此代码的方式为，使用块范围声明 `ShowData` 对象，并允许在它们超出范围时将其销毁：  
  
```cpp 
int main() {  
   ShowData sd1, sd2( "hello.dat" );  
  
   sd1.Disp( "hello to default device\n" );  
   sd2.Disp( "hello to file hello.dat\n" );  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [附加终止注意事项](../cpp/additional-termination-considerations.md)