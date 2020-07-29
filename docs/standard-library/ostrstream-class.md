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
ms.openlocfilehash: f17d8006aea6c5467f8de270318386bb12df264a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222220"
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

|成员函数|说明|
|-|-|
|[&](#freeze)|导致无法通过流缓冲区操作使用流缓冲区。|
|[pcount](#pcount)|返回写入到受控序列的元素计数。|
|[rdbuf](#rdbuf)|返回指向流的关联 `strstreambuf` 对象的指针。|
|[字符串](#str)|调用 [freeze](../standard-library/strstreambuf-class.md#freeze)，然后将返回指向受控序列开头的指针。|

## <a name="requirements"></a>要求

**标头：**\<strstream>

**命名空间:** std

## <a name="ostrstreamfreeze"></a><a name="freeze"></a>ostrstream：：冻结

导致无法通过流缓冲区操作使用流缓冲区。

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>参数

*_Freezeit*\
一个 **`bool`** ，该值指示是否要冻结流。

### <a name="remarks"></a>备注

此成员函数调用[rdbuf](#rdbuf)  ->  [冻结](../standard-library/strstreambuf-class.md#freeze)（_ *Freezeit*）。

### <a name="example"></a>示例

有关使用的示例，请参阅[strstream：：冻结](../standard-library/strstreambuf-class.md#freeze) `freeze` 。

## <a name="ostrstreamostrstream"></a><a name="ostrstream"></a>ostrstream：： ostrstream

构造 `ostrstream` 类型的对象。

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>参数

*ptr*\
缓冲区。

*计*\
缓冲区的大小（以字节为单位）。

*_Mode*\
缓冲区的输入和输出模式。 有关详细信息，请参阅 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。

### <a name="remarks"></a>备注

这两个构造函数通过调用[ostream](../standard-library/ostream-typedefs.md#ostream)（**sb**）来初始化基类，其中 `sb` 是[strstreambuf](../standard-library/strstreambuf-class.md)类的存储对象。 第一个构造函数还 `sb` 通过调用初始化 `strstreambuf` 。 第二个构造函数以下列两种方式之一初始化基类：

- 如果 `_Mode`  &  **ios_base：： app**= = 0，则 `ptr` 必须指定元素数组的第一个元素 `count` ，且构造函数调用 `strstreambuf` （ `ptr` ， `count` ， `ptr` ）。

- 否则， `ptr` 必须指定 count 元素数组的第一个元素，该元素包含一个 C 字符串，其中第一个元素由指定 `ptr` ，并且构造函数调用 `strstreambuf` （ `ptr` ， `count` ，， `ptr`  +  `strlen` `ptr` ））。

## <a name="ostrstreampcount"></a><a name="pcount"></a>ostrstream：:p 计数

返回写入到受控序列的元素计数。

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>返回值

写入到受控序列的元素数。

### <a name="remarks"></a>备注

此成员函数返回[rdbuf](#rdbuf)  ->  [pcount](../standard-library/strstreambuf-class.md#pcount)。

### <a name="example"></a>示例

有关使用 `pcount` 的示例，请参阅 [strstream::pcount](../standard-library/strstreambuf-class.md#pcount)。

## <a name="ostrstreamrdbuf"></a><a name="rdbuf"></a>ostrstream：： rdbuf

返回指向流关联的 strstreambuf 对象的指针。

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>返回值

指向流关联的 strstreambuf 对象的指针。

### <a name="remarks"></a>备注

成员函数将类型的已存储流缓冲区的地址返回 `pointer` 到[strstreambuf](../standard-library/strstreambuf-class.md)。

### <a name="example"></a>示例

有关使用 `rdbuf` 的示例，请参阅 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)。

## <a name="ostrstreamstr"></a><a name="str"></a>ostrstream：： str

调用 [freeze](../standard-library/strstreambuf-class.md#freeze)，然后将返回指向受控序列开头的指针。

```cpp
char *str();
```

### <a name="return-value"></a>返回值

指向受控序列的开头的指针。

### <a name="remarks"></a>备注

此成员函数返回[rdbuf](#rdbuf)  ->  [str](../standard-library/strstreambuf-class.md#str)。

### <a name="example"></a>示例

有关使用的示例，请参阅[strstream：： str](../standard-library/strstreambuf-class.md#str) `str` 。

## <a name="see-also"></a>另请参阅

[ostream](../standard-library/ostream-typedefs.md#ostream)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
