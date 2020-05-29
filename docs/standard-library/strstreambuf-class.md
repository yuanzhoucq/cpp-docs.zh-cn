---
title: strstreambuf 类
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstreambuf::freeze
- strstream/std::strstreambuf::overflow
- strstream/std::strstreambuf::pbackfail
- strstream/std::strstreambuf::pcount
- strstream/std::strstreambuf::seekoff
- strstream/std::strstreambuf::seekpos
- strstream/std::strstreambuf::str
- strstream/std::strstreambuf::underflow
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
ms.openlocfilehash: 28399a1cd55407aadbc5d59e1e835892218ad0c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376613"
---
# <a name="strstreambuf-class"></a>strstreambuf 类

描述控制元素在**字符**数组对象中存储的序列中的元素的传输的流缓冲区。

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

|构造函数|说明|
|-|-|
|[strstreambuf](#strstreambuf)|构造 `strstreambuf` 类型的对象。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[冻结](#freeze)|导致无法通过流缓冲区操作使用流缓冲区。|
|[overflow](#overflow)|将新字符插入到已满缓冲区时可以调用的受保护虚函数。|
|[pbackfail](#pbackfail)|一个受保护的虚拟成员函数，该函数尝试将元素放回到输入流，然后使它成为当前元素（由下一个指针指向）。|
|[pcount](#pcount)|返回写入到受控序列的元素计数。|
|[seekoff](#seekoff)|一个受保护的虚拟成员函数，它尝试更改受控流的当前位置。|
|[seekpos](#seekpos)|一个受保护的虚拟成员函数，它尝试更改受控流的当前位置。|
|[Str](#str)|调用 [freeze](#freeze)，然后将返回指向受控序列开头的指针。|
|[underflow](#underflow)|一个受保护的虚拟函数，用于从输入流中提取当前元素。|

## <a name="requirements"></a>要求

**标头：** \<strstream>

**命名空间:** std

## <a name="strstreambuffreeze"></a><a name="freeze"></a>斯特兰布夫：冻结

导致无法通过流缓冲区操作使用流缓冲区。

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>参数

*_Freezeit*\
指示是否要冻结流的**布尔**。

### <a name="remarks"></a>备注

如果 *_Freezeit*为 true，则函数将更改存储`strstreambuf`模式，使受控序列冻结。 否则，不能冻结受控序列。

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

## <a name="strstreambufoverflow"></a><a name="overflow"></a>斯特兰布夫：溢出

将新字符插入到已满缓冲区时可以调用的受保护虚函数。

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>参数

*_Meta*\
要插入到缓冲区的字符或 `EOF`。

### <a name="return-value"></a>返回值

如果该函数不成功，它将返回 `EOF`。 否则，如果*\_Meta* == `EOF`返回 某些值，`EOF`则 返回 以外的一些值。 否则，它将返回*\_Meta*。

### <a name="remarks"></a>备注

如果*\_Meta* `EOF`！* ，受保护的虚拟成员函数将尝试将`(char)_Meta`元素插入到输出缓冲区中。 它可以用多种方法执行此操作：

- 如果写入位置可用，它可将元素存储到写入位置并递增输出缓冲区的下一个指针。

- 如果存储的 strstreambuf 模式指出受控的序列可修改、可扩展且未被冻结，则该函数通过向输出缓冲区分配新的序列，生成写入位置。 以这种方式扩展输出缓冲区还会扩展任何关联的输入缓冲区。

## <a name="strstreambufpbackfail"></a><a name="pbackfail"></a>斯特兰布夫：:p回击失败

一个受保护的虚拟成员函数，该函数尝试将元素放回到输入流，然后使它成为当前元素（由下一个指针指向）。

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>参数

*_Meta*\
要插入到缓冲区的字符或 `EOF`。

### <a name="return-value"></a>返回值

如果该函数不成功，它将返回 `EOF`。 否则，如果*\_Meta* == `EOF`返回 某些值，`EOF`则 返回 以外的一些值。 否则，它将返回*\_Meta*。

### <a name="remarks"></a>备注

受保护虚拟成员函数尝试将元素放回输入缓冲区，随后使它成为当前元素（由下一个指针指向）。

如果*\_Meta，* == `EOF`则要回滚的元素实际上是当前元素之前流中已有的元素。 否则，该元素将替换为`ch = (char)_Meta`。 该函数可以用多种方法放回元素：

- 如果回放位置可用，并且存储在那里的元素比较等于`ch`，则可以递减输入缓冲区的下一个指针。

- 如果回退位置可用，并且 strstreambuf 模式表示受控序列是可修改的，则函数可以存储`ch`到回退位置并递减输入缓冲区的下一个指针。

## <a name="strstreambufpcount"></a><a name="pcount"></a>斯特里布夫：:p计数

返回写入到受控序列的元素计数。

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>返回值

写入到受控序列的元素计数。

### <a name="remarks"></a>备注

具体而言，如果 [pptr](../standard-library/basic-streambuf-class.md#pptr) 是空指针，该函数将返回零。 否则，它将返回`pptr` -  [pbase](../standard-library/basic-streambuf-class.md#pbase)。

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

## <a name="strstreambufseekoff"></a><a name="seekoff"></a>斯特里布夫：寻人

一个受保护的虚拟成员函数，它尝试更改受控流的当前位置。

```cpp
virtual streampos seekoff(streamoff _Off,
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

如果此函数成功更改任何一个流位置或两个流位置，则返回结果流位置。 否则，如果失败将返回一个无效的流位置。

### <a name="remarks"></a>备注

受保护虚拟成员函数尝试更改受控流的当前位置。 对于 strstreambuf 类的对象，流位置仅包含流偏移量。 如果偏移量为零，将指定受控序列的第一个元素。

确定新的位置，如下所示：

- 如果`_Way == ios_base::beg`，新位置是流的开头加 *_Off*。

- 如果`_Way == ios_base::cur`，新位置是当前流位置加上 *_Off*。

- 如果`_Way == ios_base::end`，新位置是流的末尾加上 *_Off*。

如果`_Which & ios_base::in`为非零且存在输入缓冲区，则函数将更改输入缓冲区中要读取的下一个位置。 如果`_Which & ios_base::out`也是非零，`_Way != ios_base::cur`则 和输出缓冲区存在，则函数还会设置下一个位置以写入以匹配要读取的下一个位置。

否则，如果 `_Which & ios_base::out` 为非零值且存在输出缓冲区，则该函数将更改输出缓冲区中的下一个写入位置。 否则，定位操作将失败。 若要成功执行定位操作，则结果流的位置必须位于受控序列内。

## <a name="strstreambufseekpos"></a><a name="seekpos"></a>斯特里布夫：：寻求者

一个受保护的虚拟成员函数，它尝试更改受控流的当前位置。

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>参数

*_Sp*\
要搜寻的位置。

*_Which*\
指定指针位置的模式。 默认值允许修改读取和写入位置。

### <a name="return-value"></a>返回值

如果此函数成功更改任何一个流位置或两个流位置，则返回结果流位置。 否则，如果失败将返回一个无效的流位置。 若要确定流位置是否无效，请比较返回值与 `pos_type(off_type(-1))`。

### <a name="remarks"></a>备注

受保护虚拟成员函数尝试更改受控流的当前位置。 对于 strstreambuf 类的对象，流位置仅包含流偏移量。 如果偏移量为零，将指定受控序列的第一个元素。 新职位由 *_Sp*决定。

如果 `_Which` & **ios_base::in** 为非零值且存在输入缓冲区，则该函数将更改输入缓冲区中的下一个读取位置。 如果 `_Which` & `ios_base::out` 为非零值且存在输出缓冲区，则该函数还将设置下一个写入位置以便匹配下一个读取位置。 否则，如果 `_Which` & `ios_base::out` 为非零值且存在输出缓冲区，则该函数将更改输出缓冲区中的下一个写入位置。 否则，定位操作将失败。 若要成功执行定位操作，则结果流的位置必须位于受控序列内。

## <a name="strstreambufstr"></a><a name="str"></a>斯特兰布夫：斯特

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

## <a name="strstreambufstrstreambuf"></a><a name="strstreambuf"></a>斯特兰布夫：斯特特兰布夫

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

*_Allocfunc*\
用以分配缓冲区内存的函数。

*计数*\
确定 *_Getptr*指向的缓冲区的长度。 如果 *_Getptr*不是参数（第一个构造函数形式），则为缓冲区建议的分配大小。

*_Freefunc*\
用来释放缓冲区内存的函数。

*_Getptr*\
用于输入的缓冲区。

*_Putptr*\
用于输出的缓冲区。

### <a name="remarks"></a>备注

第一个构造函数将空指针存储在所有控制输入缓冲区、输出缓冲区和 strstreambuf 分配的指针中。 该函数可设置存储的 strstreambuf 模式，使受控序列可修改和可扩展。 它还接受*计数*作为建议的初始分配大小。

第二个构造函数的构造函数与第一个构造函数类似，只不过它存储*\_Allocfunc*作为调用以分配存储的函数的指针，而*\_Freefunc*则作为指向函数的指针来调用释放该存储。

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

同样与第一个构造函数类似，只不过 `_Getptr` 指定用来存储受控序列的数组对象。 （因此，它不得为空指针。数组中的元素*N*数确定如下：

- 如果`count`（> 0），则`count` *N*是 。

- 如果`count`（ = 0），`strlen`则*N*是`_Getptr`（ （ **_** `char` _ ） 。

- 如果`count`（< 0），则*N* **INT_MAX**。

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

## <a name="strstreambufunderflow"></a><a name="underflow"></a>斯特兰布夫：

一个受保护的虚拟函数，用于从输入流中提取当前元素。

```cpp
virtual int underflow();
```

### <a name="return-value"></a>返回值

如果该函数不成功，它将返回 `EOF`。 否则，它返回输入流中的当前元素，并根据上文所述进行转换。

### <a name="remarks"></a>备注

受保护的虚拟成员函数努力从输入缓冲区`ch`中提取当前元素，然后推进当前流位置，并将该元素返回为 （）（）ch`int``unsigned char`。 **ch** 它只能以一种方式做到这一点：如果读取位置可用，它将作为`ch`存储在读取位置的元素，并推进输入缓冲区的下一个指针。

## <a name="see-also"></a>另请参阅

[溪流布夫](../standard-library/streambuf-typedefs.md#streambuf)\
[C++标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[电流编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
