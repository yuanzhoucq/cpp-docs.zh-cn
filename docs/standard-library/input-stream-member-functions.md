---
title: 输入流成员函数
ms.date: 11/04/2016
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
ms.openlocfilehash: b046ea1995d5a8eaa39dced9feb7a5e4c422c253
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663978"
---
# <a name="input-stream-member-functions"></a>输入流成员函数

输入流成员函数用于磁盘输入。 成员函数包括：

- [输入流的 open 函数](#vclrftheopenfunctionforinputstreamsanchor11)

- [Get](#vclrfthegetfunctionanchor12)

- [Getline](#vclrfthegetlinefunctionanchor13)

- [只读](#vclrfthereadfunctionanchor14)

- [seekg 和 tellg 函数](#vclrftheseekgandtellgfunctionsanchor7)

- [输入流的 close 函数](#vclrftheclosefunctionforinputstreamsanchor15)

## <a name="vclrftheopenfunctionforinputstreamsanchor11"></a>输入流的 open 函数

如果使用输入文件流 (ifstream)，则必须将该流与特定磁盘文件关联。 您可以执行此操作在构造函数中，也可以使用`open`函数。 在这两种情况下，参数都相同。

通常指定[ios_base:: openmode](../standard-library/ios-base-class.md#openmode)标志，打开与输入流关联的文件时 (默认模式是`ios::in`)。 有关一系列`open_mode`标记，请参阅[打开](#vclrftheopenfunctionforinputstreamsanchor11)。 这些标志可与按位 OR ( &#124; ) 运算符组合。

若要读取的文件，首先使用`fail`成员函数来确定是否存在：

```cpp
istream ifile("FILENAME");

if (ifile.fail())
// The file does not exist ...
```

## <a name="vclrfthegetfunctionanchor12"></a> Get

未格式化`get`成员函数的工作方式类似于`>>`运算符有两个例外。 首先，`get`函数包括空白字符，而提取程序不包括空白时`skipws`标志设置 （默认值）。 第二个，`get`函数是不太可能会导致绑定的输出流 (`cout`，例如) 刷新。

一个变体`get`函数指定缓冲区地址和要读取的字符最大数量。 这在限制发送给特定变量的字符数时非常有用，如本例所示：

```cpp
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

```Input
1234
```

### <a name="sample-output"></a>示例输出

```Output
1234
```

## <a name="vclrfthegetlinefunctionanchor13"></a> Getline

`getline`成员函数是类似于`get`函数。 这两个函数均允许用于指定输入终止字符的第三个参数。 默认值为换行字符。 这两个函数均会保留一个字符作为所需终止字符。 但是，`get`将终止字符留在流中和`getline`删除结尾的字符。

如下示例为输入流指定了一个终止字符：

```cpp
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

```Input
test
```

## <a name="vclrfthereadfunctionanchor14"></a> 只读

`read`成员函数到指定的内存区域从文件读取字节数。 长度参数决定了所读取字节的数量。 如果未包含该参数，则到达文件物理末尾时，或在文本模式文件的情况下读取到嵌入的 `EOF` 字符时，将停止读取。

本示例将工资单文件中的二进制记录读取到一个结构中：

```cpp
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

## <a name="vclrftheseekgandtellgfunctionsanchor7"></a>seekg 和 tellg 函数

输入文件流会使内部指针保持处于文件中接下来要读取数据的位置。 使用 `seekg` 函数设置此指针，如此处所示：

```cpp
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

若要使用`seekg`若要实现面向记录的数据管理系统，固定长度记录大小乘以记录数来获取相对于该文件末尾的字节位置，然后使用`get`对象读取记录。

`tellg` 成员函数会返回读取的当前文件位置。 该值为 `streampos` 类型，即 \<iostream> 中定义的一个 `typedef`。 如下示例会读取文件并显示指示空格位置的消息。

```cpp
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

## <a name="vclrftheclosefunctionforinputstreamsanchor15"></a>输入流的 close 函数

`close`成员函数关闭与输入的文件流关联的磁盘文件，并释放操作系统文件句柄。 [Ifstream](../standard-library/basic-ifstream-class.md)析构函数将关闭该文件，但你可以使用`close`函数如果您需要打开同一流对象的另一个文件。

## <a name="see-also"></a>请参阅

[输入流](../standard-library/input-streams.md)<br/>
