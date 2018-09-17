---
title: strstreambuf 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- strstream/std::strstreambuf::freeze
- strstream/std::strstreambuf::overflow
- strstream/std::strstreambuf::pbackfail
- strstream/std::strstreambuf::pcount
- strstream/std::strstreambuf::seekoff
- strstream/std::strstreambuf::seekpos
- strstream/std::strstreambuf::str
- strstream/std::strstreambuf::underflow
dev_langs:
- C++
helpviewer_keywords:
- std::strstreambuf [C++], freeze
- std::strstreambuf [C++], overflow
- std::strstreambuf [C++], pbackfail
- std::strstreambuf [C++], pcount
- std::strstreambuf [C++], seekoff
- std::strstreambuf [C++], seekpos
- std::strstreambuf [C++], str
- std::strstreambuf [C++], underflow
ms.assetid: b040b8ea-0669-4eba-8908-6a9cc159c54b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2424ce23c0a376156bbb78869a2e33e501958e73
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719129"
---
# <a name="strstreambuf-class"></a>strstreambuf 类

描述控制元素与序列中存储的元素的传输的流缓冲区**char**数组对象。

## <a name="syntax"></a>语法

```cpp
class strstreambuf : public streambuf
```

## <a name="remarks"></a>备注

可在必要时对它进行分配、扩展和释放以适应序列中的更改，具体取决于对象的构造方式。

类 `strstreambuf` 的对象将模式信息的几个位存储为其 `strstreambuf` 模式。 这些位指示受控序列是否：

- 已分配且最后需要释放。

- 是可修改的。

- 可通过重新分配存储进行扩展。

- 已被冻结并因此需要在对象被销毁前进行解冻，或者已由不是对象的某个代理释放（若已分配）。

无论这些单独模式位的状态如何，都不能修改或扩展已冻结的受控序列。

此对象还存储指向控制 `strstreambuf` 分配的两个函数的指针。 如果这些指针都是空指针，则对象会自行设计用于分配和释放受控序列存储的方法。

> [!NOTE]
> 此类已弃用。 请考虑改为使用 [stringbuf](../standard-library/sstream-typedefs.md#stringbuf) 或 [wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[strstreambuf](#strstreambuf)|构造 `strstreambuf` 类型的对象。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[freeze](#freeze)|导致无法通过流缓冲区操作使用流缓冲区。|
|[overflow](#overflow)|将新字符插入到已满缓冲区时可以调用的受保护虚函数。|
|[pbackfail](#pbackfail)|一个受保护的虚拟成员函数，该函数尝试将元素放回到输入流，然后使它成为当前元素（由下一个指针指向）。|
|[pcount](#pcount)|返回写入到受控序列的元素计数。|
|[seekoff](#seekoff)|一个受保护的虚拟成员函数，它尝试更改受控流的当前位置。|
|[seekpos](#seekpos)|一个受保护的虚拟成员函数，它尝试更改受控流的当前位置。|
|[str](#str)|调用 [freeze](#freeze)，然后将返回指向受控序列开头的指针。|
|[underflow](#underflow)|一个受保护的虚拟函数，用于从输入流中提取当前元素。|

## <a name="requirements"></a>要求

**标头：**\<strstream>

**命名空间：** std

## <a name="freeze"></a>  strstreambuf::freeze

导致无法通过流缓冲区操作使用流缓冲区。

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>参数

*_Freezeit*<br/>
一个**bool** ，该值指示是否要冻结的流。

### <a name="remarks"></a>备注

如果 *_Freezeit*为 true，该函数将更改存储`strstreambuf`模式以冻结受控的序列。 否则，不能冻结受控序列。

[str](#str) 意味着 `freeze`。

> [!NOTE]
> 在 `strstreambuf` 析构期间不会释放冻结的缓冲区。 释放缓冲区之前，必须解除对它的冻结，避免内存泄漏。

### <a name="example"></a>示例

```cpp
// strstreambuf_freeze.cpp
// compile with: /EHsc

#include <iostream>
#include <strstream>

using namespace std;

void report(strstream &x)
{
    if (!x.good())
        cout << "stream bad" << endl;
    else
        cout << "stream good" << endl;
}

int main()
{
    strstream x;

    x << "test1";
    cout << "before freeze: ";
    report(x);

    // Calling str freezes stream.
    cout.write(x.rdbuf()->str(), 5) << endl;
    cout << "after freeze: ";
    report(x);

    // Stream is bad now, wrote on frozen stream
    x << "test1.5";
    cout << "after write to frozen stream: ";
    report(x);

    // Unfreeze stream, but it is still bad
    x.rdbuf()->freeze(false);
    cout << "after unfreezing stream: ";
    report(x);

    // Clear stream
    x.clear();
    cout << "after clearing stream: ";
    report(x);

    x << "test3";
    cout.write(x.rdbuf()->str(), 10) << endl;

    // Clean up.  Failure to unfreeze stream will cause a
    // memory leak.
    x.rdbuf()->freeze(false);
}
```

```Output
before freeze: stream good
test1
after freeze: stream good
after write to frozen stream: stream bad
after unfreezing stream: stream bad
after clearing stream: stream good
test1test3
```

## <a name="overflow"></a>  strstreambuf::overflow

将新字符插入到已满缓冲区时可以调用的受保护虚函数。

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>参数

*_Meta*<br/>
要插入到缓冲区的字符或 `EOF`。

### <a name="return-value"></a>返回值

如果该函数不成功，它将返回 `EOF`。 否则，如果 _ *Meta* == `EOF`，它将返回不是 `EOF` 的其他值。 否则，返回 \_ *Meta*。

### <a name="remarks"></a>备注

如果 _ *Meta* != `EOF`，受保护的虚拟成员函数会尝试将元素 ( `char`)\_ *Meta* 插入到输出缓冲区。 可通过多种方式执行该操作：

- 如果写入位置可用，它可将元素存储到写入位置并增加输出缓冲区的下一个指针。

- 如果存储的 strstreambuf 模式指出受控的序列可修改、可扩展且未被冻结，则该函数通过向输出缓冲区分配新的序列，生成写入位置。 以这种方式扩展输出缓冲区还会扩展任何关联的输入缓冲区。

## <a name="pbackfail"></a>  strstreambuf::pbackfail

一个受保护的虚拟成员函数，该函数尝试将元素放回到输入流，然后使它成为当前元素（由下一个指针指向）。

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>参数

*_Meta*<br/>
要插入到缓冲区的字符或 `EOF`。

### <a name="return-value"></a>返回值

如果该函数不成功，它将返回 `EOF`。 否则，如果 _ *Meta* == `EOF`，它将返回不是 `EOF` 的其他值。 否则，返回 \_ *Meta*。

### <a name="remarks"></a>备注

受保护虚拟成员函数尝试将元素放回输入缓冲区，随后使它成为当前元素（由下一个指针指向）。

如果 _ *Meta* == `EOF`，要推送回的元素在当前元素之前实际上已是流中的一个元素了。 否则，该元素替换为 **ch** = ( `char`)\_ *Meta*。 该函数可以用多种方法放回元素：

- 如果放回位置可用，且存储在其中的元素进行比较等于`ch`，它可以递减输入缓冲区的下一个指针。

- 如果放回位置可用，且如果 strstreambuf 模式指出受控的序列是可修改，该函数可以存储`ch`到放回位置并递减输入缓冲区的下一个指针。

## <a name="pcount"></a>  strstreambuf::pcount

返回写入到受控序列的元素计数。

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>返回值

写入到受控序列的元素计数。

### <a name="remarks"></a>备注

具体而言，如果 [pptr](../standard-library/basic-streambuf-class.md#pptr) 是空指针，该函数将返回零。 否则，它将返回`pptr`  -  [pbase](../standard-library/basic-streambuf-class.md#pbase)。

### <a name="example"></a>示例

```cpp
// strstreambuf_pcount.cpp
// compile with: /EHsc
#include <iostream>
#include <strstream>
using namespace std;

int main( )
{
   strstream x;
   x << "test1";
   cout << x.rdbuf( )->pcount( ) << endl;
   x << "test2";
   cout << x.rdbuf( )->pcount( ) << endl;
}
```

## <a name="seekoff"></a>  strstreambuf::seekoff

一个受保护的虚拟成员函数，它尝试更改受控流的当前位置。

```cpp
virtual streampos seekoff(streamoff _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>参数

*_Off*<br/>
要搜寻的相对于的位置 *_Way*。

*_Way*<br/>
偏移操作的起点。 请参阅 [seekdir](../standard-library/ios-base-class.md#seekdir)，查看可能的值。

*_Which*<br/>
指定指针位置的模式。 默认允许修改读取和写入位置。

### <a name="return-value"></a>返回值

如果此函数成功更改任何一个流位置或两个流位置，则返回结果流位置。 否则，如果失败将返回一个无效的流位置。

### <a name="remarks"></a>备注

受保护虚拟成员函数更改受控流的当前位置。 对于 strstreambuf 类的对象，流位置仅包含流偏移量。 如果偏移量为零，将指定受控序列的第一个元素。

确定新位置，如下所示：

- 如果 `_Way` ==  `ios_base::beg`，新位置是流的开始位置加上 _ *Off*。

- 如果 `_Way` ==  `ios_base::cur`，新位置是当前流位置加上 _*Off*。

- 如果 `_Way` ==  `ios_base::end`，新位置是流末尾位置加上 _*Off*。

如果 `_Which` &  **ios_base::in** 为非零值且存在输入缓冲区，则该函数将更改输入缓冲区中的下一个读取位置。 如果 `_Which` &  **ios_base::out** 也为非零值 `_Way` != **ios_base::cur**，且存在输出缓冲区，则该函数还将设置下一个写入位置以便匹配下一个读取位置。

否则，如果 `_Which` &  `ios_base::out` 为非零值且存在输出缓冲区，则该函数将更改输出缓冲区中的下一个写入位置。 否则，定位操作将失败。 若要成功执行定位操作，则结果流的位置必须位于受控序列内。

## <a name="seekpos"></a>  strstreambuf::seekpos

一个受保护的虚拟成员函数，它尝试更改受控流的当前位置。

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>参数

*_Sp*<br/>
要搜寻的位置。

*_Which*<br/>
指定指针位置的模式。 默认允许修改读取和写入位置。

### <a name="return-value"></a>返回值

如果此函数成功更改任何一个流位置或两个流位置，则返回结果流位置。 否则，如果失败将返回一个无效的流位置。 若要确定流位置是否有效，请比较返回值和 `pos_type(off_type(-1))`。

### <a name="remarks"></a>备注

受保护虚拟成员函数更改受控流的当前位置。 对于 strstreambuf 类的对象，流位置仅包含流偏移量。 如果偏移量为零，将指定受控序列的第一个元素。 新的位置由 _ *Sp* 确定。

如果 `_Which` &  **ios_base::in** 为非零值且存在输入缓冲区，则该函数将更改输入缓冲区中的下一个读取位置。 如果 `_Which` &  `ios_base::out` 为非零值且存在输出缓冲区，则该函数还将设置下一个写入位置以便匹配下一个读取位置。 否则，如果 `_Which` &  `ios_base::out` 为非零值且存在输出缓冲区，则该函数将更改输出缓冲区中的下一个写入位置。 否则，定位操作将失败。 若要成功执行定位操作，则结果流的位置必须位于受控序列内。

## <a name="str"></a>  strstreambuf::str

调用 [freeze](#freeze)，然后将返回指向受控序列开头的指针。

```cpp
char *str();
```

### <a name="return-value"></a>返回值

指向受控序列的开头的指针。

### <a name="remarks"></a>备注

不存在终止的空元素，除非显式插入一个。

### <a name="example"></a>示例

有关使用 **str** 的示例，请参阅 [strstreambuf::freeze](#freeze)。

## <a name="strstreambuf"></a>  strstreambuf::strstreambuf

构造 `strstreambuf` 类型的对象。

```cpp
explicit strstreambuf(streamsize count = 0);

strstreambuf(void (* _Allocfunc)(size_t),
    void (* _Freefunc)(void*));

strstreambuf(char* _Getptr,
    streamsize count,
    char* _Putptr = 0);

strstreambuf(signed char* _Getptr,
    streamsize count,
    signed char* _Putptr = 0);

strstreambuf(unsigned char* _Getptr,
    streamsize count,
    unsigned char* _Putptr = 0);

strstreambuf(const char* _Getptr,
    streamsize count);

strstreambuf(const signed char* _Getptr,
    streamsize count);

strstreambuf(const unsigned char* _Getptr,
    streamsize count);
```

### <a name="parameters"></a>参数

*_Allocfunc*<br/>
用以分配缓冲区内存的函数。

*count*<br/>
确定指向缓冲区的长度 *_Getptr*。 如果 *_Getptr*不是参数 （第一个构造函数格式），建议的分配缓冲区的大小。

*_Freefunc*<br/>
用来释放缓冲区内存的函数。

*_Getptr*<br/>
用于输入的缓冲区。

*_Putptr*<br/>
用于输出的缓冲区。

### <a name="remarks"></a>备注

第一个构造函数将空指针存储在所有控制输入缓冲区、输出缓冲区和 strstreambuf 分配的指针中。 该函数可设置存储的 strstreambuf 模式，使受控序列可修改和可扩展。 它还会接受*计数*作为建议的初始分配大小。

第二个构造函数与第一个类似，只不过它将 _ *Allocfunc* 存储为用于调用来分配存储的函数的指针，将 \_ *Freefunc* 存储为用于调用来释放该存储的函数的指针。

这三个构造函数为：

```cpp
strstreambuf(char *_Getptr,
    streamsize count,
    char *putptr = 0);

strstreambuf(signed char *_Getptr,
    streamsize count,
    signed char *putptr = 0);

strstreambuf(unsigned char *_Getptr,
    streamsize count,
    unsigned char *putptr = 0);
```

同样与第一个构造函数类似，只不过 `_Getptr` 指定用来存储受控序列的数组对象。 （因此，它不能为空指针。）数组中 *N* 元素的数量按以下方式确定：

- 如果 (`count` > 0)，然后*N*是`count`。

- 如果 (`count` = = 0)，然后*N*是`strlen`(( **const** `char` *) `_Getptr` )。

- 如果 (`count` < 0)，然后*N*是**INT_MAX**。

如果 `_Putptr` 是空指针，该函数通过执行指令建立输入缓冲区：

```cpp
setg(_Getptr,
    _Getptr,
    _Getptr + N);
```

否则，它将通过执行以下指令建立输入和输出缓冲区：

```cpp
setg(_Getptr,
    _Getptr,
    _Putptr);

setp(_Putptr,
    _Getptr + N);
```

在这种情况下，`_Putptr` 必须在间隔 [ `_Getptr`、`_Getptr` + *N*] 中。

最后，这三个构造函数为：

```cpp
strstreambuf(const char *_Getptr,
    streamsize count);

strstreambuf(const signed char *_Getptr,
    streamsize count);

strstreambuf(const unsigned char *_Getptr,
    streamsize count);
```

所有构造函数的行为都与以下项相同：

```cpp
streambuf((char *)_Getptr, count);
```

只不过存储模式使受控序列既不可修改也不可扩展。

## <a name="underflow"></a>  strstreambuf::underflow

一个受保护的虚拟函数，用于从输入流中提取当前元素。

```cpp
virtual int underflow();
```

### <a name="return-value"></a>返回值

如果该函数不成功，它将返回 `EOF`。 否则，它返回输入流中的当前元素，并根据上文所述进行转换。

### <a name="remarks"></a>备注

受保护虚拟成员函数尝试提取当前元素`ch`从输入缓冲区，然后提出当前流位置，并返回元素作为 (`int`) (`unsigned char`) **ch**。 它可以在只有一种方法的操作： 如果读取的位置可用，它采用`ch`如元素存储在读取位置，并提升输入缓冲区的下一个指针。

## <a name="see-also"></a>请参阅

[streambuf](../standard-library/streambuf-typedefs.md#streambuf)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>
