---
title: strstream 类
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
helpviewer_keywords:
- std::strstream [C++], freeze
- std::strstream [C++], pcount
- std::strstream [C++], rdbuf
- std::strstream [C++], str
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
ms.openlocfilehash: 047b7e9d7fdece75137980b013d43abf1d5e3ec3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376621"
---
# <a name="strstream-class"></a>strstream 类

描述了一个对象，该对象使用 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区控制元素和编码对象的插入和提取。

## <a name="syntax"></a>语法

```cpp
class strstream : public iostream
```

## <a name="remarks"></a>备注

该对象存储 `strstreambuf` 类的对象。

> [!NOTE]
> 此类已弃用。 请考虑改用 [stringstream](../standard-library/sstream-typedefs.md#stringstream) 或 [wstringstream](../standard-library/sstream-typedefs.md#wstringstream)。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[斯特流](#strstream)|构造 `strstream` 类型的对象。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[冻结](#freeze)|导致无法通过流缓冲区操作使用流缓冲区。|
|[pcount](#pcount)|返回写入到受控序列的元素计数。|
|[rdbuf](#rdbuf)|返回指向流的关联 `strstreambuf` 对象的指针。|
|[Str](#str)|调用 [freeze](../standard-library/strstreambuf-class.md#freeze)，然后将返回指向受控序列开头的指针。|

## <a name="requirements"></a>要求

**标头：** \<strstream>

**命名空间:** std

## <a name="strstreamfreeze"></a><a name="freeze"></a>流：：冻结

导致无法通过流缓冲区操作使用流缓冲区。

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>参数

*_Freezeit*\
指示是否要冻结流的**布尔**。

### <a name="remarks"></a>备注

成员函数调用[rdbuf](#rdbuf) -> [冻结](../standard-library/strstreambuf-class.md#freeze)（=*冻结*）。

### <a name="example"></a>示例

有关使用`freeze`的示例，请参阅[strstreambuf：：冻结](../standard-library/strstreambuf-class.md#freeze)。

## <a name="strstreampcount"></a><a name="pcount"></a>斯特流：:p计数

返回写入到受控序列的元素计数。

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>返回值

写入到受控序列的元素数。

### <a name="remarks"></a>备注

成员函数返回[rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount)。

### <a name="example"></a>示例

有关使用 pcount 的示例，请参阅 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)。

## <a name="strstreamrdbuf"></a><a name="rdbuf"></a>斯特兰：：rdbuf

返回指向流关联的 strstreambuf 对象的指针。

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>返回值

指向流关联的 strstreambuf 对象的指针。

### <a name="remarks"></a>备注

成员函数将类型的`pointer`存储流缓冲区的地址返回为[strstreambuf](../standard-library/strstreambuf-class.md)。

### <a name="example"></a>示例

有关使用 `rdbuf` 的示例，请参阅 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)。

## <a name="strstreamstr"></a><a name="str"></a>斯特兰：斯特

调用 [freeze](../standard-library/strstreambuf-class.md#freeze)，然后将返回指向受控序列开头的指针。

```cpp
char *str();
```

### <a name="return-value"></a>返回值

指向受控序列的开头的指针。

### <a name="remarks"></a>备注

成员函数返回[rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str)。

### <a name="example"></a>示例

有关 使用`str`的示例，请参阅[strstreambuf：str。](../standard-library/strstreambuf-class.md#str)

## <a name="strstreamstrstream"></a><a name="strstream"></a>串流：：斯特流

构造 `strstream` 类型的对象。

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>参数

*计数*\
缓冲区的大小。

*_Mode*\
缓冲区的输入和输出模式。 有关详细信息，请参阅 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。

*Ptr*\
缓冲区。

### <a name="remarks"></a>备注

两个构造函数都通过调用[streambuf](../standard-library/streambuf-typedefs.md#streambuf) **（sb**） 初始`sb`化基类，其中是类[strstreambuf](../standard-library/strstreambuf-class.md)的存储对象。 第一个构造函数也`sb`通过调用[strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf)进行初始化。 第二个构造函数以下列两种方式之一初始化基类：

- 如果`_Mode` & **ios_base：：app**= 0，则*ptr*必须`count`指定元素数组的第一个元素，构造函数调用`strstreambuf`（，，） `ptr` `count` `ptr`

- 否则 *，ptr*必须指定计数元素数组的第一个元素，该元素包含第一个元素由*ptr*指定的 C 字符串，构造函数`strstreambuf`调用`ptr` `count`（ `ptr`  +  `strlen` `ptr`， （ ） 。

## <a name="see-also"></a>另请参阅

[iostream](../standard-library/istream-typedefs.md#iostream)\
[C++标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[电流编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
