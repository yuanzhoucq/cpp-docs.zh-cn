---
title: "输入流成员函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96927d7e1a6718f4663ca42248140ac5a7d8fe50
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="input-stream-member-functions"></a>输入流成员函数
输入流成员函数用于磁盘输入。 成员函数包括：  
  
- [输入流的 open 函数](#vclrftheopenfunctionforinputstreamsanchor11)  
  
- [Get](#vclrfthegetfunctionanchor12)  
  
- [Getline](#vclrfthegetlinefunctionanchor13)  
  
- [只读](#vclrfthereadfunctionanchor14)  
  
- [seekg 和 tellg 函数](#vclrftheseekgandtellgfunctionsanchor7)  
  
- [输入流的 close 函数](#vclrftheclosefunctionforinputstreamsanchor15)  
  
##  <a name="vclrftheopenfunctionforinputstreamsanchor11"></a>输入流的 open 函数  
 如果使用输入文件流 (ifstream)，则必须将该流与特定磁盘文件关联。 可在构造函数中实现此操作，或者可使用 **open** 函数。 在这两种情况下，参数都相同。  
  
 打开与输入流关联的文件时，通常要指定一个 [ios_base::openmode](../standard-library/ios-base-class.md#openmode) 标志（默认模式为 **ios::in**）。 有关的列表**open_mode**标记，请参阅[打开](#vclrftheopenfunctionforinputstreamsanchor11)。 这些标志可与按位 OR ( &#124; ) 运算符组合。  
  
 若要读取文件，请首先使用 **fail** 成员函数来确定文件是否存在：  
  
```  
istream ifile("FILENAME");

if (ifile.fail())  
// The file does not exist ...  
```  
  
##  <a name="vclrfthegetfunctionanchor12">Get</a>
 未格式化的 **get** 成员函数作用方式与 **>>** 运算符类似，但存在两个例外。 第一，**get** 函数会将空格字符包含在内，而在设置了 **skipws** 标志（默认设置）时提取符会将空格排除在外。 第二，**get** 函数导致绑定输出流（例如 `cout`）刷新的可能性较小。  
  
 一个 **get** 函数变体可指定缓冲区地址和要读取的最大字符数。 这在限制发送给特定变量的字符数时非常有用，如本例所示：  
  
```  
// ioo_get_function.cpp  
// compile with: /EHsc  
// Type up to 24 characters and a terminating character.   
// Any remaining characters can be extracted later.  
#include <iostream>  
using namespace std;  
  
int main()  
{  
   char line[25];  
   cout << " Type a line terminated by carriage return\n>";  
   cin.get( line, 25 );  
   cout << line << endl;  
}  
```  
  
### <a name="input"></a>输入  
  
```  
1234  
```  
  
### <a name="sample-output"></a>示例输出  
  
```  
1234  
```  
  
##  <a name="vclrfthegetlinefunctionanchor13">Getline</a>
 **getline** 成员函数类似于 **get** 函数。 这两个函数均允许用于指定输入终止字符的第三个参数。 默认值为换行字符。 这两个函数均会保留一个字符作为所需终止字符。 但是，**get** 会将终止字符留在流中，而 **getline** 会删除此终止字符。  
  
 如下示例为输入流指定了一个终止字符：  
  
```  
// getline_func.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   char line[100];  
   cout << " Type a line terminated by 't'" << endl;  
   cin.getline( line, 100, 't' );  
   cout << line;  
}  
```  
  
### <a name="input"></a>输入  
  
```  
test  
```  
  
##  <a name="vclrfthereadfunctionanchor14">只读</a>
 **read** 成员函数会将文件中的字节读取到内存的指定区域。 长度参数决定了所读取字节的数量。 如果未包含该参数，则到达文件物理末尾时，或在文本模式文件的情况下读取到嵌入的 `EOF` 字符时，将停止读取。  
  
 本示例将工资单文件中的二进制记录读取到一个结构中：  
  
```  
#include <fstream>  
#include <iostream>  
using namespace std;  
  
int main()  
{  
   struct  
   {  
      double salary;  
      char name[23];  
   } employee;  
  
   ifstream is( "payroll" );  
   if( is ) {  // ios::operator void*()  
      is.read( (char *) &employee, sizeof( employee ) );  
      cout << employee.name << ' ' << employee.salary << endl;  
   }  
   else {  
      cout << "ERROR: Cannot open file 'payroll'." << endl;  
   }  
}  
```  
  
 程序会假定这些数据记录完全以此结构指定的方式进行格式化，其中不包含任何终止回车或换行字符。  
  
##  <a name="vclrftheseekgandtellgfunctionsanchor7"></a>seekg 和 tellg 函数  
 输入文件流会使内部指针保持处于文件中接下来要读取数据的位置。 使用 `seekg` 函数设置此指针，如此处所示：  
  
```  
#include <iostream>  
#include <fstream>  
using namespace std;  
  
int main( )  
{  
   char ch;  
  
   ifstream tfile( "payroll" );  
   if( tfile ) {  
      tfile.seekg( 8 );        // Seek 8 bytes in (past salary)  
      while ( tfile.good() ) { // EOF or failure stops the reading  
         tfile.get( ch );  
         if( !ch ) break;      // quit on null  
         cout << ch;  
      }  
   }  
   else {  
      cout << "ERROR: Cannot open file 'payroll'." << endl;  
   }  
}  
```  
  
 若要使用 `seekg` 来实现面向记录的数据管理系统，请用固定长度记录大小乘以记录数来获取相对于该文件末尾的字节位置，然后使用 **get** 对象读取记录。  
  
 `tellg` 成员函数会返回读取的当前文件位置。 该值为 `streampos` 类型，即 \<iostream> 中定义的一个 `typedef`。 如下示例会读取文件并显示指示空格位置的消息。  
  
```  
#include <fstream>  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   char ch;  
   ifstream tfile( "payroll" );  
   if( tfile ) {  
       while ( tfile.good( ) ) {  
          streampos here = tfile.tellg();  
          tfile.get( ch );  
          if ( ch == ' ' )  
             cout << "\nPosition " << here << " is a space";  
       }  
   }  
   else {  
      cout << "ERROR: Cannot open file 'payroll'." << endl;  
   }  
}  
```  
  
##  <a name="vclrftheclosefunctionforinputstreamsanchor15"></a>输入流的 close 函数  
 **close** 成员函数会关闭与输入文件流关联的磁盘文件，并释放操作系统文件句柄。 [ifstream](../standard-library/basic-ifstream-class.md) 析构函数将关闭该文件，但如需打开同一流对象的另一个文件，则可以使用 **close** 函数。  
  
## <a name="see-also"></a>请参阅  
 [输入流](../standard-library/input-streams.md)

