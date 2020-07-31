---
title: 输入流成员函数
ms.date: 07/19/2019
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
ms.openlocfilehash: 8aa211a03bb6e9b1d910db360066b4a2ca76571a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233166"
---
# <a name="input-stream-member-functions"></a>输入流成员函数

输入流成员函数用于磁盘输入。

## <a name="open"></a><a name="vclrftheopenfunctionforinputstreamsanchor11"></a>未

如果使用的是输入文件流（ `ifstream` ），则必须将该流与特定磁盘文件相关联。 您可以在构造函数中执行此操作，也可以使用 `open` 函数。 在这两种情况下，参数都相同。

当你打开与输入流关联的文件时，通常会指定[ios_base：： openmode](../standard-library/ios-base-class.md#openmode)标志（默认模式为 `ios::in` ）。 有关标志的列表 `openmode` ，请参阅[ios_base：： openmode](../standard-library/ios-base-class.md#openmode)。 这些标志可与按位 OR ( &#124; ) 运算符组合。

若要读取文件，请首先使用 `fail` 成员函数来确定该文件是否存在：

```cpp
istream ifile("FILENAME");

if (ifile.fail())
// The file does not exist ...
```

## <a name="get"></a><a name="vclrfthegetfunctionanchor12"></a>获取

无格式的 `get` 成员函数的工作方式与运算符类似， `>>` 但有两个例外。 首先，该 `get` 函数包括空白字符，而提取程序在设置标志时不包括空格 `skipws` （默认值）。 其次， `get` 函数不太可能导致绑定的输出流（ `cout` 例如）被刷新。

函数的变体 `get` 指定缓冲区地址和要读取的最大字符数。 这在限制发送给特定变量的字符数时非常有用，如本例所示：

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

## <a name="getline"></a><a name="vclrfthegetlinefunctionanchor13"></a>getline

`getline`成员函数类似于 `get` 函数。 这两个函数均允许用于指定输入终止字符的第三个参数。 默认值为换行字符。 这两个函数均会保留一个字符作为所需终止字符。 但是，会将 `get` 终止字符保留在流中，并 `getline` 删除终止字符。

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

## <a name="read"></a><a name="vclrfthereadfunctionanchor14"></a>读取

该 `read` 成员函数将字节从文件读取到指定的内存区域。 长度参数决定了所读取字节的数量。 如果未包含该参数，则到达文件物理末尾时，或在文本模式文件的情况下读取到嵌入的 `EOF` 字符时，将停止读取。

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

该程序假定数据记录的格式设置与结构指定的格式完全相同，无终止回车符或换行符。

## <a name="seekg-and-tellg"></a><a name="vclrftheseekgandtellgfunctionsanchor7"></a>seekg 和 tellg

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

若要使用 `seekg` 来实现面向记录的数据管理系统，请将固定长度记录大小乘以记录号以获取相对于文件末尾的字节位置，然后使用 `get` 对象读取记录。

`tellg` 成员函数会返回读取的当前文件位置。 此值的类型为 `streampos` ，它是 **`typedef`** 在中定义的 \<iostream> 。 如下示例会读取文件并显示指示空格位置的消息。

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

## <a name="close"></a><a name="vclrftheclosefunctionforinputstreamsanchor15"></a>封闭

该 `close` 成员函数将关闭与输入文件流关联的磁盘文件，并释放操作系统文件句柄。 [`ifstream`](../standard-library/basic-ifstream-class.md)析构函数将关闭该文件，但 `close` 如果您需要为同一个流对象打开另一个文件，则可以使用函数。

## <a name="see-also"></a>另请参阅

[输入流](../standard-library/input-streams.md)
