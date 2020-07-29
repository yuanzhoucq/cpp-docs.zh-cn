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
ms.openlocfilehash: e6b4df60f4d28839419d02fd3ed6d7cbf73d327f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87202189"
---
# <a name="strstreambuf-class"></a>strstreambuf 类

描述一个流缓冲区，该缓冲区控制元素与数组对象中存储的元素序列之间的来回传输 **`char`** 。

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

|成员函数|说明|
|-|-|
|[&](#freeze)|导致无法通过流缓冲区操作使用流缓冲区。|
|[超出](#overflow)|将新字符插入到已满缓冲区时可以调用的受保护虚函数。|
|[pbackfail](#pbackfail)|一个受保护的虚拟成员函数，该函数尝试将元素放回到输入流，然后使它成为当前元素（由下一个指针指向）。|
|[pcount](#pcount)|返回写入到受控序列的元素计数。|
|[seekoff](#seekoff)|一个受保护的虚拟成员函数，它尝试更改受控流的当前位置。|
|[seekpos](#seekpos)|一个受保护的虚拟成员函数，它尝试更改受控流的当前位置。|
|[字符串](#str)|调用 [freeze](#freeze)，然后将返回指向受控序列开头的指针。|
|[下](#underflow)|一个受保护的虚拟函数，用于从输入流中提取当前元素。|

## <a name="requirements"></a>要求

**标头：**\<strstream>

**命名空间:** std

## <a name="strstreambuffreeze"></a><a name="freeze"></a>strstreambuf：：冻结

导致无法通过流缓冲区操作使用流缓冲区。

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>参数

*_Freezeit*\
一个 **`bool`** ，该值指示是否要冻结流。

### <a name="remarks"></a>备注

如果 *_Freezeit*为 true，则函数将更改存储 `strstreambuf` 模式，以使受控序列冻结。 否则，不能冻结受控序列。

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

## <a name="strstreambufoverflow"></a><a name="overflow"></a>strstreambuf：：溢出

将新字符插入到已满缓冲区时可以调用的受保护虚函数。

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>参数

*_Meta*\
要插入到缓冲区的字符或 `EOF`。

### <a name="return-value"></a>返回值

如果该函数不成功，它将返回 `EOF`。 否则，如果为* \_ 元*  ==  `EOF` ，则返回除之外的其他值 `EOF` 。 否则，它将返回* \_ 元*。

### <a name="remarks"></a>备注

如果为* \_ Meta* ！ = `EOF` ，受保护的虚拟成员函数尝试将元素插入 `(char)_Meta` 到输出缓冲区。 它可以用多种方法执行此操作：

- 如果写入位置可用，它可将元素存储到写入位置并递增输出缓冲区的下一个指针。

- 如果存储的 strstreambuf 模式指出受控的序列可修改、可扩展且未被冻结，则该函数通过向输出缓冲区分配新的序列，生成写入位置。 以这种方式扩展输出缓冲区还会扩展任何关联的输入缓冲区。

## <a name="strstreambufpbackfail"></a><a name="pbackfail"></a>strstreambuf：:p backfail

一个受保护的虚拟成员函数，该函数尝试将元素放回到输入流，然后使它成为当前元素（由下一个指针指向）。

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>参数

*_Meta*\
要插入到缓冲区的字符或 `EOF`。

### <a name="return-value"></a>返回值

如果该函数不成功，它将返回 `EOF`。 否则，如果为* \_ 元*  ==  `EOF` ，则返回除之外的其他值 `EOF` 。 否则，它将返回* \_ 元*。

### <a name="remarks"></a>备注

受保护虚拟成员函数尝试将元素放回输入缓冲区，随后使它成为当前元素（由下一个指针指向）。

如果是* \_ Meta*  ==  `EOF` ，要推送回的元素在当前元素之前实际上已是流中的一个元素。 否则，该元素将替换为 `ch = (char)_Meta` 。 该函数可以用多种方法放回元素：

- 如果放回位置可用，且存储在该位置的元素与相等 `ch` ，则它可以递减输入缓冲区的下一个指针。

- 如果放回位置可用，且 strstreambuf 模式显示受控序列是可修改的，则该函数可以存储在 `ch` 放回位置并减小输入缓冲区的下一个指针。

## <a name="strstreambufpcount"></a><a name="pcount"></a>strstreambuf：:p 计数

返回写入到受控序列的元素计数。

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>返回值

写入到受控序列的元素计数。

### <a name="remarks"></a>备注

具体而言，如果 [pptr](../standard-library/basic-streambuf-class.md#pptr) 是空指针，该函数将返回零。 否则，它将返回 `pptr`  -  [pbase](../standard-library/basic-streambuf-class.md#pbase)。

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

## <a name="strstreambufseekoff"></a><a name="seekoff"></a>strstreambuf：： seekoff

一个受保护的虚拟成员函数，它尝试更改受控流的当前位置。

```cpp
virtual streampos seekoff(streamoff _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>参数

*_Off*\
要查找的相对于 *_Way*的位置。

*_Way*\
偏移操作的起点。 请参阅 [seekdir](../standard-library/ios-base-class.md#seekdir)，查看可能的值。

*_Which*\
指定指针位置的模式。 默认值允许修改读取和写入位置。

### <a name="return-value"></a>返回值

如果此函数成功更改任何一个流位置或两个流位置，则返回结果流位置。 否则，如果失败将返回一个无效的流位置。

### <a name="remarks"></a>备注

受保护虚拟成员函数尝试更改受控流的当前位置。 对于 strstreambuf 类的对象，流位置仅包含流偏移量。 如果偏移量为零，将指定受控序列的第一个元素。

确定新的位置，如下所示：

- 如果 `_Way == ios_base::beg` 为，则新位置是流的开头加 *_Off*。

- 如果 `_Way == ios_base::cur` 为，则新位置是当前流位置加 *_Off*。

- 如果 `_Way == ios_base::end` 为，则新位置是流的末尾加 *_Off*。

如果 `_Which & ios_base::in` 为非零值且存在输入缓冲区，则函数将更改下一个位置以在输入缓冲区中读取。 如果 `_Which & ios_base::out` 也为非零值， `_Way != ios_base::cur` 并且存在输出缓冲区，则该函数还会将下一个要写入的位置设置为匹配要读取的下一个位置。

否则，如果 `_Which & ios_base::out` 为非零值且存在输出缓冲区，则该函数将更改输出缓冲区中的下一个写入位置。 否则，定位操作将失败。 若要成功执行定位操作，则结果流的位置必须位于受控序列内。

## <a name="strstreambufseekpos"></a><a name="seekpos"></a>strstreambuf：： seekpos

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

受保护虚拟成员函数尝试更改受控流的当前位置。 对于 strstreambuf 类的对象，流位置仅包含流偏移量。 如果偏移量为零，将指定受控序列的第一个元素。 新位置由 *_Sp*确定。

如果 `_Which` & **ios_base::in** 为非零值且存在输入缓冲区，则该函数将更改输入缓冲区中的下一个读取位置。 如果 `_Which` & `ios_base::out` 为非零值且存在输出缓冲区，则该函数还将设置下一个写入位置以便匹配下一个读取位置。 否则，如果 `_Which` & `ios_base::out` 为非零值且存在输出缓冲区，则该函数将更改输出缓冲区中的下一个写入位置。 否则，定位操作将失败。 若要成功执行定位操作，则结果流的位置必须位于受控序列内。

## <a name="strstreambufstr"></a><a name="str"></a>strstreambuf：： str

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

## <a name="strstreambufstrstreambuf"></a><a name="strstreambuf"></a>strstreambuf：： strstreambuf

构造 `strstreambuf` 类型的对象。

```cpp
explicit strstreambuf(streamsize count = 0);

strstreambuf(void (* alloc_func)(size_t),
    void (* free_func)(void*));

strstreambuf(char* getptr,
    streamsize count,
    char* putptr = 0);

strstreambuf(signed char* getptr,
    streamsize count,
    signed char* putptr = 0);

strstreambuf(unsigned char* getptr,
    streamsize count,
    unsigned char* putptr = 0);

strstreambuf(const char* getptr,
    streamsize count);

strstreambuf(const signed char* getptr,
    streamsize count);

strstreambuf(const unsigned char* getptr,
    streamsize count);
```

### <a name="parameters"></a>参数

*alloc_func*\
用以分配缓冲区内存的函数。

*计*\
确定*getptr*所指向的缓冲区的长度。 如果*getptr*不是参数（第一个构造函数格式），则为缓冲区提供建议的分配大小。

*_Freefunc*\
用来释放缓冲区内存的函数。

*getptr*\
用于输入的缓冲区。

*putptr*\
用于输出的缓冲区。

### <a name="remarks"></a>备注

第一个构造函数将空指针存储在所有控制输入缓冲区、输出缓冲区和 strstreambuf 分配的指针中。 该函数可设置存储的 strstreambuf 模式，使受控序列可修改和可扩展。 它还接受*count*作为建议的初始分配大小。

第二个构造函数的行为与第一个相同，不同之处在于它将*alloc_func*存储为指向函数的指针，调用该函数以调用来分配存储，并将其*free_func*为用于释放该存储的函数的指针。

这三个构造函数为：

```cpp
strstreambuf(char *getptr,
    streamsize count,
    char *putptr = 0);

strstreambuf(signed char *getptr,
    streamsize count,
    signed char *putptr = 0);

strstreambuf(unsigned char *getptr,
    streamsize count,
    unsigned char *putptr = 0);
```

的行为与第一个类似，不同之处在于*getptr*指定用于保存受控序列的数组对象。 （因此，它不能为 null 指针。）确定数组中的元素*N*的数目，如下所示：

- 如果（*计数*> 0），则*N*为*count*。

- 如果（*计数*= = 0），则*N*为 `strlen((const char *) getptr )` 。

- 如果（*计数*< 0），则*N*为**INT_MAX**。

如果*putptr*为 null 指针，则该函数将通过执行以下操作来仅建立输入缓冲区：

```cpp
setg(getptr,
    getptr,
    getptr + N);
```

否则，它将通过执行以下指令建立输入和输出缓冲区：

```cpp
setg(getptr,
    getptr,
    putptr);

setp(putptr,
    getptr + N);
```

在这种情况下， *putptr*必须处于 [ *getptr*， *getptr*  +  *N*] 的间隔内。

最后，这三个构造函数为：

```cpp
strstreambuf(const char *getptr,
    streamsize count);

strstreambuf(const signed char *getptr,
    streamsize count);

strstreambuf(const unsigned char *getptr,
    streamsize count);
```

所有构造函数的行为都与以下项相同：

```cpp
streambuf((char *)getptr, count);
```

只不过存储模式使受控序列既不可修改也不可扩展。

## <a name="strstreambufunderflow"></a><a name="underflow"></a>strstreambuf：：下溢

一个受保护的虚拟函数，用于从输入流中提取当前元素。

```cpp
virtual int underflow();
```

### <a name="return-value"></a>返回值

如果该函数不成功，它将返回 `EOF`。 否则，它返回输入流中的当前元素，并根据上文所述进行转换。

### <a name="remarks"></a>备注

受保护的虚拟成员函数致力于 `ch` 从输入缓冲区提取当前元素，然后提升当前流位置，并将该元素作为返回 `(int)(unsigned char)ch` 。 它只能通过一种方式执行此操作：如果读取位置可用，则它将 `ch` 作为存储在读取位置中的元素，并提升输入缓冲区的下一个指针。

## <a name="see-also"></a>另请参阅

[streambuf](../standard-library/streambuf-typedefs.md#streambuf)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
