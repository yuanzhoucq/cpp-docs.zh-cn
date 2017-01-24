---
title: "输入流成员函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "输入流对象"
  - "输入流, 成员函数"
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
caps.latest.revision: 7
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 输入流成员函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

输入流成员函数为磁盘输入使用。  成员函数包括：  
  
-   [输入流打开的函数](#vclrftheopenfunctionforinputstreamsanchor11)  
  
-   [获取函数](#vclrfthegetfunctionanchor12)  
  
-   [getline 函数](#vclrfthegetlinefunctionanchor13)  
  
-   [读取函数](#vclrfthereadfunctionanchor14)  
  
-   [seekg 和 tellg 函数](#vclrftheseekgandtellgfunctionsanchor7)  
  
-   [输入流的接近的函数](#vclrftheclosefunctionforinputstreamsanchor15)  
  
##  <a name="vclrftheopenfunctionforinputstreamsanchor11"></a> 输入流打开的函数  
 如正在使用输入文件流 \(ifstream\)，则必须将该流与一个特定磁盘文件。  可以执行此操作。构造函数，或者可以使用 **打开** 函数。  在任何情况下，参数相同。  
  
 通常指定 [ios\_base::openmode](../Topic/ios_base::openmode.md) 标志，在打开文件与输入流时 \(默认模式为 **ios::in**\)。  有关 **open\_mode** 标志的列表，请参见 [函数打开](#vclrftheopenfunctionforinputstreamsanchor11)。  标志可以按位组合使用或 \(&#124;\) 运算符。  
  
 若要读取文件，请先使用 **失败** 成员函数确定它是否存在：  
  
```  
istream ifile( "FILENAME" );  
if ( ifile.fail() )  
// The file does not exist ...  
```  
  
##  <a name="vclrfthegetfunctionanchor12"></a> 获取函数  
 无格式的 **get** 成员函数的工作原理与 **\>\>** 运算符有两个异常。  首先，**get** 函数包含空白，提取器，而不包括空白，在 [skipws](../Topic/skipws.md) 标志设置时 \(默认\)。  接下来，**get** 函数不太可能导致附加的输出流 \(例如，`cout`\) 刷新。  
  
 **get** 函数的地址和差异指定缓冲区的最大字符数。  因为此示例演示，对于绑定字符数是有用发送到的变量：  
  
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
  
### 输入  
  
```  
1234  
```  
  
### 示例输出  
  
```  
1234  
```  
  
##  <a name="vclrfthegetlinefunctionanchor13"></a> getline 函数  
 **getline** 成员函数类似于 **get** 函数。  两个用于输入函数允许指定终止字符的第三个参数。  默认值为换行符。  两个函数。所需的终止字符保留一个字符。  但是，**get**。流将终止字符保留，并且 **getline** 取消终止字符。  
  
 下面的示例适用于内容指定了一个终止的字符：  
  
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
  
### 输入  
  
```  
test  
```  
  
##  <a name="vclrfthereadfunctionanchor14"></a> 读取函数  
 **读取** 成员函数读取字节从文件到内存的指定区域。  长度参数标识读取的字节数。  如果不包括该参数，读取，在实际停止文件结束为止，或者对于文本方式文件时，在嵌入的 `EOF` 读取字符时。  
  
 此示例读取二进制记录工资单文件到结构：  
  
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
  
 假定程序，数据记录正确格式根据结构不终止回车和换行符。  
  
##  <a name="vclrftheseekgandtellgfunctionsanchor7"></a> seekg 和 tellg 函数  
 输入文件流将在内部指向接下来将数据读取文件的位置。  如下所设置的与 `seekg` 函数的指针，此所示：  
  
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
  
 若要使用 `seekg` 实现面向记录管理系统，则将定长记录大小数字乘以记录获取字节位置相对于文件的末尾，然后使用 **get** 对象读取记录。  
  
 `tellg` 成员函数返回读取的当前文件位置。  在 \<iostream\>为 `streampos`类型，`typedef` 定义中使用此值。  下面的示例读取文件并显示空间中的位置的信息。  
  
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
  
##  <a name="vclrftheclosefunctionforinputstreamsanchor15"></a> 输入流的接近的函数  
 **关闭** 成员函数关闭磁盘文件与输入文件流和释放操作系统句柄的文件。  [ifstream](../standard-library/basic-ifstream-class.md) 析构函数关闭您的文件，但是，您可以使用 **关闭** 函数是否需要打开相同的流对象的其他文件。  
  
## 请参阅  
 [输入流](../standard-library/input-streams.md)