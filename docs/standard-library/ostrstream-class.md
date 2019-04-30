---
title: ostrstream 类
ms.date: 11/04/2016
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
ms.openlocfilehash: 2d4a7a780f1a7db27bcb600c13430deaa0dc35cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370861"
---
# <a name="ostrstream-class"></a>ostrstream 类

描述控制元素插入的对象，并将对象编码到 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区中。

## <a name="syntax"></a>语法

```cpp
class ostrstream : public ostream
```

## <a name="remarks"></a>备注

该对象存储 `strstreambuf` 类的对象。

> [!NOTE]
> 此类已弃用。 请考虑使用 [ostringstream](../standard-library/sstream-typedefs.md#ostringstream) 或 [wostringstream](../standard-library/sstream-typedefs.md#wostringstream) 作为替代。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[ostrstream](#ostrstream)|构造 `ostrstream` 类型的对象。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[freeze](#freeze)|导致无法通过流缓冲区操作使用流缓冲区。|
|[pcount](#pcount)|返回写入到受控序列的元素计数。|
|[rdbuf](#rdbuf)|返回指向流的关联 `strstreambuf` 对象的指针。|
|[str](#str)|调用 [freeze](../standard-library/strstreambuf-class.md#freeze)，然后将返回指向受控序列开头的指针。|

## <a name="requirements"></a>要求

**标头：**\<strstream>

**命名空间：** std

## <a name="freeze"></a>  ostrstream::freeze

导致无法通过流缓冲区操作使用流缓冲区。

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>参数

*_Freezeit*<br/>
一个**bool** ，该值指示是否要冻结的流。

### <a name="remarks"></a>备注

此成员函数调用 [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*)。

### <a name="example"></a>示例

请参阅[strstream:: freeze](../standard-library/strstreambuf-class.md#freeze)有关的示例，使用`freeze`。

## <a name="ostrstream"></a>  ostrstream::ostrstream

构造 `ostrstream` 类型的对象。

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>参数

*ptr*<br/>
缓冲区。

*count*<br/>
缓冲区的大小（以字节为单位）。

*_Mode*<br/>
缓冲区的输入和输出模式。 有关详细信息，请参阅 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。

### <a name="remarks"></a>备注

这两个构造函数通过调用初始化基类[ostream](../standard-library/ostream-typedefs.md#ostream)(**sb**)，其中`sb`是类的存储的对象[strstreambuf](../standard-library/strstreambuf-class.md)。 第一个构造函数还可以初始化`sb`通过调用`strstreambuf`。 第二个构造函数以下列两种方式之一初始化基类：

- 如果`_Mode`  &  **ios_base:: app**= = 0，然后`ptr`必须将指定的数组的第一个元素`count`元素以及构造函数调用`strstreambuf`(`ptr`， `count`, `ptr`).

- 否则为`ptr`必须将指定的计数元素包含的数组的 C 字符串由指定的第一个元素的第一个元素`ptr`，并构造函数调用`strstreambuf`(`ptr`， `count`， `ptr` + `strlen`( `ptr`) ).

## <a name="pcount"></a>  ostrstream::pcount

返回写入到受控序列的元素计数。

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>返回值

写入到受控序列的元素数。

### <a name="remarks"></a>备注

此成员函数返回 [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount)。

### <a name="example"></a>示例

有关使用 `pcount` 的示例，请参阅 [strstream::pcount](../standard-library/strstreambuf-class.md#pcount)。

## <a name="rdbuf"></a>  ostrstream::rdbuf

返回指向流关联的 strstreambuf 对象的指针。

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>返回值

指向流关联的 strstreambuf 对象的指针。

### <a name="remarks"></a>备注

此成员函数返回类型的存储的流缓冲区的地址`pointer`到[strstreambuf](../standard-library/strstreambuf-class.md)。

### <a name="example"></a>示例

有关使用 `rdbuf` 的示例，请参阅 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)。

## <a name="str"></a>  ostrstream::str

调用 [freeze](../standard-library/strstreambuf-class.md#freeze)，然后将返回指向受控序列开头的指针。

```cpp
char *str();
```

### <a name="return-value"></a>返回值

指向受控序列的开头的指针。

### <a name="remarks"></a>备注

此成员函数返回 [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str)。

### <a name="example"></a>示例

请参阅[strstream:: str](../standard-library/strstreambuf-class.md#str)有关的示例，使用`str`。

## <a name="see-also"></a>请参阅

[ostream](../standard-library/ostream-typedefs.md#ostream)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>
