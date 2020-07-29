---
title: 输出文件流成员函数
ms.date: 11/04/2016
helpviewer_keywords:
- output streams [C++], member functions
ms.assetid: 38aaf710-8035-4a34-a0c4-123a5327f28a
ms.openlocfilehash: f20ed4e238d23211a6eeec4a3091daeb4d02a9b3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217670"
---
# <a name="output-file-stream-member-functions"></a>输出文件流成员函数

输出流成员函数具有三种类型：等效于操控器的类型、执行未格式化的写操作的类型，以及其他修改流状态且不具有等效的操控器或插入运算符的类型。 对于连续的格式化输出，可仅使用插入运算符和操控器。 对于随机访问二进制磁盘输出，在无论是否具有插入运算符，都可使用其他成员函数。

## <a name="the-open-function-for-output-streams"></a>输出流的 open 函数

若要使用输出文件流（[ofstream](../standard-library/basic-ofstream-class.md)），则必须将该流与构造函数或函数中的特定磁盘文件相关联 `open` 。 如果使用 `open` 函数，则可以对一系列文件重复使用同一个流对象。 在任一情况下，描述该文件的参数是相同的。

打开与输出流关联的文件时，通常会指定一个 `open_mode` 标志。 可以将在 `ios` 类中定义为枚举器的这些标志与按位 OR ( &#124; ) 运算符合并。 有关枚举器的列表，请参阅 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。

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

`write`函数将内存块写入输出文件流。 长度参数指定写入的字节数。 此示例可创建输出文件流，并向其写入 `Date` 结构的二进制值：

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

`write`函数在达到 null 字符后不会停止，因此会写入完整的类结构。 函数采用两个参数：一个 **`char`** 指针和一个要写入的字符计数。 请注意 **`char`** <strong>\*</strong> 结构对象地址前面的必需强制转换。

## <a name="the-seekp-and-tellp-functions"></a>seekp 和 tellp 函数

输出文件流保留指向下一次写入数据的位置的内部指针。 `seekp` 成员函数将设置此指针，从而提供随机访问磁盘文件输出。 `tellp` 成员函数将返回文件位置。 有关使用与 `seekp` 和 `tellp` 等效的输入流的示例，请参阅 [seekg 和 tellg 函数](../standard-library/input-stream-member-functions.md)。

## <a name="the-close-function-for-output-streams"></a>输出流的 close 函数

`close`成员函数关闭与输出文件流关联的磁盘文件。 若要完成所有磁盘输出，则必须关闭该文件。 如有必要， `ofstream` 析构函数将关闭该文件，但 `close` 如果需要为同一个流对象打开另一个文件，则可以使用函数。

仅当构造函数或 `open` 成员函数打开文件时，输出流析构函数才会自动关闭流的文件。 如果向构造函数传递已打开文件的文件描述符或使用 `attach` 成员函数，则必须显式关闭该文件。

## <a name="error-processing-functions"></a><a name="vclrferrorprocessingfunctionsanchor10"></a>错误处理函数

使用这些成员函数来测试写入流时是否出现错误：

|函数|返回值|
|--------------|------------------|
|[无效](basic-ios-class.md#bad)|**`true`** 如果出现不可恢复的错误，则返回。|
|[失败](basic-ios-class.md#fail)|**`true`** 如果出现不可恢复的错误或 "预期" 条件（如转换错误），或者如果找不到该文件，则返回。 使用零参数对的调用后，处理通常可以恢复 `clear` 。|
|[良好](basic-ios-class.md#good)|**`true`** 如果没有错误条件（不可恢复或其他），并且未设置文件尾标志，则返回。|
|[eof](basic-ios-class.md#eof)|返回 **`true`** 文件尾条件。|
|[清除](basic-ios-class.md#clear)|设置内部错误状态。 如果通过默认参数调用，则它会清除所有错误位。|
|rdstate（基本-ios-类 md # rdstate|返回当前错误状态。|

**！** 重载运算符以执行与函数相同的函数 `fail` 。 因此表达式：

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

**Void \* （）** 运算符不等效于， `good` 因为它不会测试文件的结尾。

## <a name="see-also"></a>另请参阅

[输出流](../standard-library/output-streams.md)
