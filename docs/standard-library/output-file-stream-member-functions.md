---
title: 输出文件流成员函数
ms.date: 11/04/2016
helpviewer_keywords:
- output streams [C++], member functions
ms.assetid: 38aaf710-8035-4a34-a0c4-123a5327f28a
ms.openlocfilehash: eba627c69437754a9c0a819167443aa00c025fef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370835"
---
# <a name="output-file-stream-member-functions"></a>输出文件流成员函数

输出流成员函数具有三种类型：等效于操控器的类型、执行未格式化的写操作的类型，以及其他修改流状态且不具有等效的操控器或插入运算符的类型。 对于连续的格式化输出，可仅使用插入运算符和操控器。 对于随机访问二进制磁盘输出，在无论是否具有插入运算符，都可使用其他成员函数。

## <a name="the-open-function-for-output-streams"></a>输出流的 open 函数

若要使用输出文件流 ([ofstream](../standard-library/basic-ofstream-class.md))，必须将该流关联与构造函数中的特定磁盘文件或`open`函数。 如果使用`open`函数，可以重复使用具有一系列文件的同一个流对象。 在任一情况下，描述该文件的参数是相同的。

当您打开与输出流关联的文件时，您通常会指定`open_mode`标志。 可以将在 `ios` 类中定义为枚举器的这些标志与按位 OR ( &#124; ) 运算符合并。 有关枚举器的列表，请参阅 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。

三种常见的输出流情况涉及模式选项：

- 创建文件。 如果该文件已存在，将删除旧版本。

   ```cpp
   ostream ofile("FILENAME");
   // Default is ios::out

   ofstream ofile("FILENAME", ios::out);
   // Equivalent to above
   ```

- 将记录追加到现有文件，或者如果文件尚不存在，创建一个文件。

   ```cpp
   ofstream ofile("FILENAME", ios::app);
   ```

- 在同一个流中打开两个文件，一次打开一个。

   ```cpp
   ofstream ofile();
   ofile.open("FILE1", ios::in);
   // Do some output
   ofile.close();    // FILE1 closed
   ofile.open("FILE2", ios::in);
   // Do some more output
   ofile.close();    // FILE2 closed
   // When ofile goes out of scope it is destroyed.
   ```

## <a name="the-put"></a>Put

**put** 函数将一个字符写入到输出流。 默认情况下，以下两个语句相同，但第二个受流的格式化参数的影响：

```cpp
cout.put('A');

// Exactly one character written
cout <<'A'; // Format arguments 'width' and 'fill' apply
```

## <a name="the-write"></a>写入

`write`函数将内存块写入到输出文件流。 长度参数指定写入的字节数。 此示例可创建输出文件流，并向其写入 `Date` 结构的二进制值：

```cpp
// write_function.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;

struct Date
{
   int mo, da, yr;
};

int main( )
{
   Date dt = { 6, 10, 92 };
   ofstream tfile( "date.dat" , ios::binary );
   tfile.write( (char *) &dt, sizeof dt );
}
```

`write`到达 null 字符，因此，编写完整的类结构时，函数不会停止。 该函数采用两个参数： **char**指针和要写入的字符计数。 请注意需要强制转换为**char** <strong>\*</strong>之前对结构对象的地址。

## <a name="the-seekp-and-tellp-functions"></a>seekp 和 tellp 函数

输出文件流保留指向下一次写入数据的位置的内部指针。 `seekp` 成员函数将设置此指针，从而提供随机访问磁盘文件输出。 `tellp` 成员函数将返回文件位置。 有关使用与 `seekp` 和 `tellp` 等效的输入流的示例，请参阅 [seekg 和 tellg 函数](../standard-library/input-stream-member-functions.md)。

## <a name="the-close-function-for-output-streams"></a>输出流的 close 函数

`close`成员函数将关闭与输出文件流关联的磁盘文件。 若要完成所有磁盘输出，则必须关闭该文件。 如果有必要，请`ofstream`析构函数将关闭该文件，但你可以使用`close`函数如果您需要打开同一流对象的另一个文件。

输出流析构函数会自动关闭流的文件仅当构造函数或`open`成员函数打开该文件。 如果您将构造函数传递已打开文件或使用的文件描述符`attach`成员函数，必须显式关闭该文件。

## <a name="vclrferrorprocessingfunctionsanchor10"></a>错误处理函数

使用这些成员函数来测试写入流时是否出现错误：

|函数|返回值|
|--------------|------------------|
|[bad](basic-ios-class.md#bad)|如果存在不可恢复的错误，则返回 **true**。|
|[fail](basic-ios-class.md#fail)|如果出现不可恢复的错误或“预期”条件（例如出现转换错误），或者如果找不到该文件，则返回 **true**。 通常可以在调用后恢复处理`clear`使用零个自变量。|
|[good](basic-ios-class.md#good)|如果没有任何错误条件（不可恢复的或其他的条件），且未设置文件结束标志，则返回 **true**。|
|[eof](basic-ios-class.md#eof)|在文件结尾时返回 **true**。|
|[clear](basic-ios-class.md#clear)|设置内部错误状态。 如果通过默认参数调用，则它会清除所有错误位。|
|[rdstate](basic-ios-class.md#rdstate|返回当前错误状态。|

重载 **!** 运算符重载来执行相同的功能`fail`函数。 因此表达式：

```cpp
if(!cout)...
```

等效于：

```cpp
if(cout.fail())...
```

将 **void\*()** 运算符重载为 **!** 运算符 的反义词；因此表达式：

```cpp
if(cout)...
```

等效于：

```cpp
if(!cout.fail())...
```

**Void\*（)** 运算符并不等同于`good`因为不会测试文件尾。

## <a name="see-also"></a>请参阅

[输出流](../standard-library/output-streams.md)<br/>
