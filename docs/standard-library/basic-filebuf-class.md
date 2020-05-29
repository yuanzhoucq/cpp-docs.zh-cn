---
title: basic_filebuf 类
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_filebuf
- fstream/std::basic_filebuf::char_type
- fstream/std::basic_filebuf::int_type
- fstream/std::basic_filebuf::off_type
- fstream/std::basic_filebuf::pos_type
- fstream/std::basic_filebuf::traits_type
- fstream/std::basic_filebuf::close
- fstream/std::basic_filebuf::is_open
- fstream/std::basic_filebuf::open
- fstream/std::basic_filebuf::overflow
- fstream/std::basic_filebuf::pbackfail
- fstream/std::basic_filebuf::seekoff
- fstream/std::basic_filebuf::seekpos
- fstream/std::basic_filebuf::setbuf
- fstream/std::basic_filebuf::Swap
- fstream/std::basic_filebuf::sync
- fstream/std::basic_filebuf::uflow
- fstream/std::basic_filebuf::underflow
helpviewer_keywords:
- std::basic_filebuf [C++]
- std::basic_filebuf [C++], char_type
- std::basic_filebuf [C++], int_type
- std::basic_filebuf [C++], off_type
- std::basic_filebuf [C++], pos_type
- std::basic_filebuf [C++], traits_type
- std::basic_filebuf [C++], close
- std::basic_filebuf [C++], is_open
- std::basic_filebuf [C++], open
- std::basic_filebuf [C++], overflow
- std::basic_filebuf [C++], pbackfail
- std::basic_filebuf [C++], seekoff
- std::basic_filebuf [C++], seekpos
- std::basic_filebuf [C++], setbuf
- std::basic_filebuf [C++], Swap
- std::basic_filebuf [C++], sync
- std::basic_filebuf [C++], uflow
- std::basic_filebuf [C++], underflow
ms.assetid: 3196ba5c-bf38-41bd-9a95-70323ddfca1a
ms.openlocfilehash: 35bed08f2495c971df7f79f62e32b3ff68dfb3d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376886"
---
# <a name="basic_filebuf-class"></a>basic_filebuf 类

描述控制*类型Char_T*元素的流缓冲区，该元素的字符特征由类*Tr*决定，并且从存储在外部文件中的元素序列进行。

## <a name="syntax"></a>语法

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_filebuf : public basic_streambuf<Char_T, Tr>
```

### <a name="parameters"></a>参数

*Char_T*\
文件缓冲区的基本元素。

*Tr*\
文件缓冲区的基本元素（通常`char_traits<Char_T>`）的特性。

## <a name="remarks"></a>备注

类模板描述一个流缓冲区，它控制类型*Char_T*的元素的传输，其字符特征由类*Tr*决定，并且从存储在外部文件中的元素序列进行。

> [!NOTE]
> 类型`basic_filebuf`的对象使用__字符\*__ 的内部缓冲区创建，`char_type`而不考虑类型参数*Char_T*指定的对象。 这意味着 Unicode 字符串（包含**wchar_t**字符）在写入内部缓冲区之前将转换为 ANSI 字符串（包含**字符**）。 要将 Unicode 字符串存储在缓冲区中，请创建**类型wchar_t**的新缓冲区，并使用 方法[`basic_streambuf::pubsetbuf`](../standard-library/basic-streambuf-class.md#pubsetbuf)`()`设置它。 若要查看演示此行为的示例，请参阅下面的内容。

类`basic_filebuf<Char_T, Tr>`的对象存储文件指针，该指针指定控制与打开文件`FILE`关联的流的对象。 另外，它还存储指向两个文件转换方面的指针，以供受保护的成员函数 [overflow](#overflow) 和 [underflow](#underflow) 使用。 有关详细信息，请参阅[`basic_filebuf::open`](#open)。

## <a name="example"></a>示例

下面的示例演示如何通过调用 `pubsetbuf()` 方法来强制 `basic_filebuf<wchar_t>` 类型的对象将 Unicode 字符存储在其内部缓冲区中。

```cpp
// unicode_basic_filebuf.cpp
// compile with: /EHsc

#include <iostream>
#include <string>
#include <fstream>
#include <iomanip>
#include <memory.h>
#include <string.h>

#define IBUFSIZE 16

using namespace std;

void hexdump(const string& filename);

int main()
{
    wchar_t* wszHello = L"Hello World";
    wchar_t wBuffer[128];

    basic_filebuf<wchar_t> wOutFile;

    // Open a file, wcHello.txt, then write to it, then dump the
    // file's contents in hex
    wOutFile.open("wcHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wcHello.txt\n";
        return -1;
    }
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "Hex Dump of wcHello.txt - note that output is ANSI chars:\n";
    hexdump(string("wcHello.txt"));

    // Open a file, wwHello.txt, then set the internal buffer of
    // the basic_filebuf object to be of type wchar_t, then write
    // to the file and dump the file's contents in hex
    wOutFile.open("wwHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wwHello.txt\n";
        return -1;
    }
    wOutFile.pubsetbuf(wBuffer, (streamsize)128);
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "\nHex Dump of wwHello.txt - note that output is wchar_t chars:\n";
    hexdump(string("wwHello.txt"));

    return 0;
}

// dump contents of filename to stdout in hex
void hexdump(const string& filename)
{
    fstream ifile(filename.c_str(),
        ios_base::in | ios_base::binary);
    char *ibuff = new char[IBUFSIZE];
    char *obuff = new char[(IBUFSIZE*2)+1];
    int i;

    if(!ifile.is_open())
    {
        cout << "Cannot Open " << filename.c_str()
             << " for reading\n";
        return;
    }
    if(!ibuff || !obuff)
    {
        cout << "Cannot Allocate buffers\n";
        ifile.close();
        return;
    }

    while(!ifile.eof())
    {
        memset(obuff,0,(IBUFSIZE*2)+1);
        memset(ibuff,0,IBUFSIZE);
        ifile.read(ibuff,IBUFSIZE);

        // corner case where file is exactly a multiple of
        // 16 bytes in length
        if(ibuff[0] == 0 && ifile.eof())
            break;

        for(i = 0; i < IBUFSIZE; i++)
        {
            if(ibuff[i] >= ' ')
                obuff[i] = ibuff[i];
            else
                obuff[i] = '.';

            cout << setfill('0') << setw(2) << hex
                 << (int)ibuff[i] << ' ';
        }
        cout << "  " << obuff << endl;
    }
    ifile.close();
}
```

```Output
Hex Dump of wcHello.txt - note that output is ANSI chars:
48 65 6c 6c 6f 20 57 6f 72 6c 64 00 00 00 00 00   Hello World.....

Hex Dump of wwHello.txt - note that output is wchar_t chars:
48 00 65 00 6c 00 6c 00 6f 00 20 00 57 00 6f 00   H.e.l.l.o. .W.o.
72 00 6c 00 64 00 00 00 00 00 00 00 00 00 00 00   r.l.d...........
```

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[basic_filebuf](#basic_filebuf)|构造 `basic_filebuf` 类型的对象。|

### <a name="typedefs"></a>Typedef

|类型名称|说明|
|-|-|
|[char_type](#char_type)|将类型名与 `Char_T` 模板参数关联。|
|[int_type](#int_type)|使 `basic_filebuf` 范围中的此类型等效于 `Tr` 范围中具有相同名称的类型。|
|[off_type](#off_type)|使 `basic_filebuf` 范围中的此类型等效于 `Tr` 范围中具有相同名称的类型。|
|[pos_type](#pos_type)|使 `basic_filebuf` 范围中的此类型等效于 `Tr` 范围中具有相同名称的类型。|
|[traits_type](#traits_type)|将类型名与 `Tr` 模板参数关联。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[关闭](#close)|关闭文件。|
|[is_open](#is_open)|指示文件是否打开。|
|[open](#open)|打开文件。|
|[overflow](#overflow)|将新字符插入到已满缓冲区时可以调用的受保护虚函数。|
|[pbackfail](#pbackfail)|受保护虚拟成员函数尝试将元素放回到输入流中，随后使它成为当前元素（由下一个指针指向）。|
|[seekoff](#seekoff)|受保护虚拟成员函数尝试更改受控制流的当前位置。|
|[seekpos](#seekpos)|受保护虚拟成员函数尝试更改受控制流的当前位置。|
|[setbuf](#setbuf)|受保护虚拟成员函数执行特定于每个派生流缓冲区的操作。|
|[交换](#swap)|为提供的 `basic_filebuf` 参数的内容交换此 `basic_filebuf` 的内容。|
|[sync](#sync)|受保护虚函数尝试将受控制流与任何关联的外部流同步。|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|受保护虚函数从输入流中提取当前元素。|
|[underflow](#underflow)|受保护虚函数从输入流中提取当前元素。|

## <a name="requirements"></a>要求

**标头：** \<fstream>

**命名空间:** std

## <a name="basic_filebufbasic_filebuf"></a><a name="basic_filebuf"></a>basic_filebuf：basic_filebuf

构造 `basic_filebuf` 类型的对象。

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>备注

第一个构造函数将 null 指针存储在控制输入缓冲区和输出缓冲区的所有指针中。 同时它还将 null 指针存储在文件指针中。

第二个构造函数用*右侧*的内容初始化对象，作为 rvalue 引用处理。

## <a name="basic_filebufchar_type"></a><a name="char_type"></a>basic_filebuf：char_type

将类型名与 `Char_T` 模板参数关联。

```cpp
typedef Char_T char_type;
```

## <a name="basic_filebufclose"></a><a name="close"></a>basic_filebuf：关闭

关闭文件。

```cpp
basic_filebuf<Char_T, Tr> *close();
```

### <a name="return-value"></a>返回值

如果文件指针为 null 指针，则该成员函数返回 null 指针。

### <a name="remarks"></a>备注

`close` 调用 `fclose(fp)`。 如果该函数返回一个非零值，则该函数返回 null 指针。 否则，它将返回 **this** 以指示已成功关闭文件。

对于宽流，如果自打开流或自上次调用 后发生任何插入`streampos`，则函数调用[`overflow`](#overflow)。 它还通过根据需要使用文件转换面`fac`来调用`fac.unshift`，插入还原初始转换状态所需的任何序列。 **类型 char**的每个生成的元素`fp``fputc(byte, fp)``byte`都写入文件指针指定的关联流，就像窗体 的连续调用一样。 如果对的`fac.unshift`调用或任何写入失败，则函数不会成功。

### <a name="example"></a>示例

以下示例假定当前目录中有两个文件 *：basic_filebuf_close.txt（* 内容为"测试"）和*iotest.txt（* 内容为"ssss"）。

```cpp
// basic_filebuf_close.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main() {
   using namespace std;
   ifstream file;
   basic_ifstream <wchar_t> wfile;
   char c;
   // Open and close with a basic_filebuf
   file.rdbuf()->open( "basic_filebuf_close.txt", ios::in );
   file >> c;
   cout << c << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "iotest.txt" );
   file >> c;
   cout << c << endl;
   file.close( );

   // open a file with a wide character name
   wfile.open( L"iotest.txt" );

   // Open and close a nonexistent with a basic_filebuf
   file.rdbuf()->open( "ziotest.txt", ios::in );
   cout << file.fail() << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "ziotest.txt" );
   cout << file.fail() << endl;
   file.close( );
}
```

```Output
t
s
0
1
```

## <a name="basic_filebufint_type"></a><a name="int_type"></a>basic_filebuf：：int_type

使此类型在`basic_filebuf`作用域中等效于`Tr`作用域中的相同名称的类型。

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_filebufis_open"></a><a name="is_open"></a>basic_filebuf：is_open

指示文件是否打开。

```cpp
bool is_open() const;
```

### <a name="return-value"></a>返回值

如果文件指针不为空，**则为 true。**

### <a name="example"></a>示例

```cpp
// basic_filebuf_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   cout << boolalpha << file.rdbuf( )->is_open( ) << endl;

   file.open( "basic_filebuf_is_open.cpp" );
   cout << file.rdbuf( )->is_open( ) << endl;
}
```

```Output
false
true
```

## <a name="basic_filebufoff_type"></a><a name="off_type"></a>basic_filebuf：off_type

使此类型在`basic_filebuf`作用域中等效于`Tr`作用域中的相同名称的类型。

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_filebufopen"></a><a name="open"></a>basic_filebuf：：打开

打开文件。

```cpp
basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode);
```

### <a name="parameters"></a>参数

*文件名*\
要打开的文件的名称。

*模式*\
中的[`ios_base::openmode`](../standard-library/ios-base-class.md#openmode)枚举之一。

*保护*\
默认文件打开保护，等效于 _fsopen 中的*shflag*参数[，_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)。

### <a name="return-value"></a>返回值

如果缓冲区已打开，或者如果文件指针是空指针，则函数返回一个空指针。 否则，返回 **this**。

### <a name="remarks"></a>备注

成员函数通过调用[`fopen`](../c-runtime-library/reference/fopen-wfopen.md)`(filename, strmode)`打开具有名称*文件名*的文件。 `strmode`由 确定`mode & ~(`[`ate`](../standard-library/ios-base-class.md#openmode)`|`[`binary`](../standard-library/ios-base-class.md#openmode)`)`：

- `ios_base::in`变为`"r"`（打开现有文件进行读取）。

- [ios_base：：退出](../standard-library/ios-base-class.md#fmtflags)或`ios_base::out | ios_base::trunc`变为`"w"`（截截现有文件或创建以进行写入）。

- `ios_base::out | app`变为`"a"`（打开用于追加所有写入的现有文件）。

- `ios_base::in | ios_base::out`成为`"r+"`（打开用于读取和写入的现有文件）。

- `ios_base::in | ios_base::out | ios_base::trunc`成为`"w+"`（截截现有文件或创建用于读取和写入）。

- `ios_base::in | ios_base::out | ios_base::app`成为`"a+"`（打开用于读取和追加所有写入的现有文件）。

如果`mode & ios_base::binary`为非零，则函数将追加`b`以`strmode`打开二进制流而不是文本流。 然后，它将返回的值存储在文件`fopen`指针`fp`中。 如果`mode & ios_base::ate`为非零，并且文件指针不是空指针，则函数将调用`fseek(fp, 0, SEEK_END)`以将流定位到文件末尾。 如果定位操作失败，函数将调用[`close`](#close)`(fp)`并在文件指针中存储空指针。

如果文件指针不是空指针，则函数确定文件`use_facet<codecvt<Char_T, char, traits_type::`[`state_type`](../standard-library/char-traits-struct.md#state_type)`> >(`[`getloc`](../standard-library/basic-streambuf-class.md#getloc)`)`转换面： ，供[下溢](#underflow)和[溢出](#overflow)使用。

如果文件指针为 null 指针，则该函数返回 null 指针。 否则，返回 **this**。

### <a name="example"></a>示例

有关[`basic_filebuf::close`](#close)使用`open`的示例，请参阅。

## <a name="basic_filebufoperator"></a><a name="op_eq"></a>basic_filebuf：：操作员*

分配此流缓冲区对象的内容。 这是一个移动分配，涉及不会留下副本的 rvalue。

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>参数

*对*\
对 [basic_filebuf](../standard-library/basic-filebuf-class.md) 对象的右值引用。

### <a name="return-value"></a>返回值

返回 ___this__。

### <a name="remarks"></a>备注

成员运算符使用*权利*的内容替换对象的内容，该内容被视为 rvalue 引用。 有关详细信息，请参阅[Rvalue 引用声明符： &&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="basic_filebufoverflow"></a><a name="overflow"></a>basic_filebuf：溢出

当新字符插入到已满缓冲区时调用。

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>参数

*_Meta*\
要插入到缓冲区或`traits_type::eof`的字符。

### <a name="return-value"></a>返回值

如果函数无法成功，它将返回`traits_type::eof`。 否则，它将返回`traits_type::`[`not_eof`](../standard-library/char-traits-struct.md#not_eof)`(_Meta)`。

### <a name="remarks"></a>备注

如果`_Meta != traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof)，受保护的虚拟成员函数将尝试将元素`ch = traits_type::`[`to_char_type`](../standard-library/char-traits-struct.md#to_char_type)`(_Meta)`插入到输出缓冲区中。 它可以用多种方法执行此操作：

- 如果写入位置可用，它可将元素存储到写入位置并递增输出缓冲区的下一个指针。

- 它可以通过为输出缓冲区分配新的或额外的存储空间，提供写入位置。

- 它可以转换输出缓冲区中的任何挂起的输出，然后转换`ch`，使用文件转换面`fac`根据需要调用。 `fac.out` *类型 char*的每个生成的元素`fp``fputc(ch, fp)``ch`都写入文件指针指定的关联流，就像窗体 的连续调用一样。 如果任何转换或写入失败，该函数不会成功。

## <a name="basic_filebufpbackfail"></a><a name="pbackfail"></a>basic_filebuf：:p回击失败

尝试将元素放回到输入流中，随后使它成为当前元素（由下一个指针指向）。

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>参数

*_Meta*\
要插入到缓冲区的字符或 `traits_type::eof`。

### <a name="return-value"></a>返回值

如果函数无法成功，它将返回`traits_type::eof`。 否则，它将返回`traits_type::`[`not_eof`](../standard-library/char-traits-struct.md#not_eof)`(_Meta)`。

### <a name="remarks"></a>备注

受保护虚拟成员函数将元素放回到输入缓冲区中，随后使它成为当前元素（由下一个指针指向）。 如果`_Meta == traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof)，要回滚的元素实际上是当前元素之前流中的元素。 否则，该元素将替换为`ch = traits_type::`[`to_char_type`](../standard-library/char-traits-struct.md#to_char_type)`(_Meta)`。 该函数可以用多种方法放回元素：

- 如果位置`putback`可用，并且存储在那里的元素比较等于`ch`，它可以递减输入缓冲区的下一个指针。

- 如果函数可以使位置`putback`可用，则可以这样做，将下一个指针设置为指向该位置，并存储在`ch`该位置。

- 如果函数可以将元素推回输入流，则可以这样做，例如调用`ungetc`**类型 char**的元素。

## <a name="basic_filebufpos_type"></a><a name="pos_type"></a>basic_filebuf：:pos_类型

使此类型在`basic_filebuf`作用域中等效于`Tr`作用域中的相同名称的类型。

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_filebufseekoff"></a><a name="seekoff"></a>basic_filebuf：寻求

尝试更改受控制流的当前位置。

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>参数

*_Off*\
相对于 *_Way*寻求的位置。

*_Way*\
偏移操作的起点。 请参阅 [seekdir](../standard-library/ios-base-class.md#seekdir)，查看可能的值。

*_Which*\
指定指针位置的模式。 默认值允许修改读取和写入位置。

### <a name="return-value"></a>返回值

返回新位置或无效的流位置。

### <a name="remarks"></a>备注

受保护的虚拟成员函数尝试更改受控流的当前位置。 对于类[`basic_filebuf`](../standard-library/basic-filebuf-class.md)`<Char_T, Tr>`的对象，流位置可以由类型`fpos_t`对象表示，该对象存储偏移量以及解析宽流所需的任何状态信息。 偏移零是指流的第一个元素。 （类型[`pos_type`](../standard-library/basic-streambuf-class.md#pos_type)的对象至少存储一个`fpos_t`对象。

对于打开供读取和写入的文件，输入流和输出流串联放置。 若要在插入和提取之间切换，必须调用 或[`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff)[`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)。 `pubseekoff`对（因此）的`seekoff`调用对[文本流](../c-runtime-library/text-and-binary-streams.md)、[二进制流](../c-runtime-library/text-and-binary-streams.md)和[宽流](../c-runtime-library/byte-and-wide-streams.md)有各种限制。

如果文件指针`fp`为空指针，则函数将失败。 否则，它尝试通过调用`fseek(fp, _Off, _Way)`来更改流位置。 如果该函数成功，并且生成的位置`fposn`可以通过调用`fgetpos(fp, &fposn)`确定，则函数将成功。 如果函数成功，它将返回包含`pos_type``fposn`的类型值。 否则，返回一个无效的流位置。

## <a name="basic_filebufseekpos"></a><a name="seekpos"></a>basic_filebuf：seekpos

尝试更改受控制流的当前位置。

```cpp
virtual pos_type seekpos(
    pos_type _Sp,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>参数

*_Sp*\
要搜寻的位置。

*_Which*\
指定指针位置的模式。 默认值允许修改读取和写入位置。

### <a name="return-value"></a>返回值

如果文件指针`fp`为空指针，则函数将失败。 否则，它`fsetpos(fp, &fposn)`尝试通过调用 来更改流位置，`fposn``fpos_t`对象存储在`pos`中的位置。 如果该函数成功，则该函数将返回 `pos`。 否则，返回一个无效的流位置。 若要确定流位置是否无效，请比较返回值与 `pos_type(off_type(-1))`。

### <a name="remarks"></a>备注

受保护的虚拟成员函数尝试更改受控流的当前位置。 对于类[`basic_filebuf`](../standard-library/basic-filebuf-class.md)`<Char_T, Tr>`的对象，流位置可以由类型`fpos_t`对象表示，该对象存储偏移量以及解析宽流所需的任何状态信息。 偏移零是指流的第一个元素。 （类型为 `pos_type` 的对象存储至少一个 `fpos_t` 对象。）

对于打开供读取和写入的文件，输入流和输出流串联放置。 若要在插入和提取之间切换，必须调用 或[`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff)[`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)。 对`pubseekoff`（和`seekoff`） 的调用对文本流、二进制流和宽流具有各种限制。

对于宽流，如果自打开流后，或者自上次调用 `streampos` 后发生任何插入，该函数都将调用 [overflow](#overflow)。 它还通过根据需要使用文件转换面`fac`来调用`fac.unshift`，插入还原初始转换状态所需的任何序列。 **类型 char**的每个生成的元素`fp``fputc(byte, fp)``byte`都写入文件指针指定的关联流，就像窗体 的连续调用一样。 如果对的`fac.unshift`调用或任何写入失败，则函数不会成功。

## <a name="basic_filebufsetbuf"></a><a name="setbuf"></a>basic_filebuf：塞特布夫

执行特定于每个派生流缓冲区的操作。

```cpp
virtual basic_streambuf<Char_T, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>参数

*_Buffer*\
指向缓冲区的指针。

*计数*\
缓冲区的大小。

### <a name="return-value"></a>返回值

如果文件指针 `fp` 为 null 指针，则受保护成员函数将返回零。

### <a name="remarks"></a>备注

`setbuf`提供`setvbuf( fp, (char*) _Buffer, _IOFBF, count * sizeof( Char_T))`从`count`*_Buffer*开始的元素数组作为流的缓冲区。 如果该函数返回一个非零值，则该函数返回 null 指针。 否则，它将返回 **this** 表示成功。

## <a name="basic_filebufswap"></a><a name="swap"></a>basic_filebuf：：交换

将此 `basic_filebuf` 的内容与提供的 `basic_filebuf` 的内容进行交换。

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>参数

*对*\
对另一个`basic_filebuf`的 lvalue 引用。

## <a name="basic_filebufsync"></a><a name="sync"></a>basic_filebuf：同步

尝试将受控制流与任何关联的外部流同步。

```cpp
virtual int sync();
```

### <a name="return-value"></a>返回值

如果文件指针`fp`为空指针，则返回零。 否则，仅当[对溢出的](#overflow)调用并`fflush(fp)`成功刷新到流的任何挂起的输出时，它才会返回零。

## <a name="basic_filebuftraits_type"></a><a name="traits_type"></a>basic_filebuf：：traits_type

将类型名与 `Tr` 模板参数关联。

```cpp
typedef Tr traits_type;
```

## <a name="basic_filebufunderflow"></a><a name="underflow"></a>basic _ filebuf ：

从输入流中提取当前元素。

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>返回值

如果函数无法成功，它将返回`traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof)。 否则，它将返回`ch`，转换，如注释部分所述。

### <a name="remarks"></a>备注

受保护的虚拟成员函数尝试从输入流中提取当前元素`ch`，并将该元素返回为`traits_type::`[`to_int_type`](../standard-library/char-traits-struct.md#to_int_type)`(ch)`。 它可以用多种方法执行此操作：

- 如果读取位置可用，则它用作`ch`存储在读取位置的元素，并推进输入缓冲区的下一个指针。

- 它可以读取**字符**类型的一个或多个元素，就像通过`fgetc(fp)`窗体的连续调用一样，并通过使用文件转换面`ch``Char_T``fac`根据需要调用`fac.in`它们转换为类型元素。 如果任何读取或转换失败，该函数不会成功。

## <a name="see-also"></a>另请参阅

[\<>](../standard-library/fstream.md)\
[C++标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[电流编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
