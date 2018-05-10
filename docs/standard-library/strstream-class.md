---
title: strstream 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
dev_langs:
- C++
helpviewer_keywords:
- std::strstream [C++], freeze
- std::strstream [C++], pcount
- std::strstream [C++], rdbuf
- std::strstream [C++], str
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 245391a0625d94fee0a4457f87e7b633ba3d03ca
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
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

|构造函数|描述|
|-|-|
|[strstream](#strstream)|构造 `strstream` 类型的对象。|

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

## <a name="freeze"></a>  strstream::freeze

导致无法通过流缓冲区操作使用流缓冲区。

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>参数

`_Freezeit` A `bool` ，该值指示你是否想要被冻结的流。

### <a name="remarks"></a>备注

此成员函数调用 [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*)。

### <a name="example"></a>示例

有关使用 **freeze** 的示例，请参阅 [strstreambuf::freeze](../standard-library/strstreambuf-class.md#freeze)。

## <a name="pcount"></a>  strstream::pcount

返回写入到受控序列的元素计数。

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>返回值

写入到受控序列的元素数。

### <a name="remarks"></a>备注

此成员函数返回 [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount)。

### <a name="example"></a>示例

有关使用 pcount 的示例，请参阅 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)。

## <a name="rdbuf"></a>  strstream::rdbuf

返回指向流关联的 strstreambuf 对象的指针。

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>返回值

指向流关联的 strstreambuf 对象的指针。

### <a name="remarks"></a>备注

此成员函数将**指针**类型的已存储流缓冲区的地址返回到 [strstreambuf](../standard-library/strstreambuf-class.md)。

### <a name="example"></a>示例

有关使用 `rdbuf` 的示例，请参阅 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)。

## <a name="str"></a>  strstream::str

调用 [freeze](../standard-library/strstreambuf-class.md#freeze)，然后将返回指向受控序列开头的指针。

```cpp
char *str();
```

### <a name="return-value"></a>返回值

指向受控序列的开头的指针。

### <a name="remarks"></a>备注

此成员函数返回 [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str)。

### <a name="example"></a>示例

有关使用 **str** 的示例，请参阅 [strstreambuf::str](../standard-library/strstreambuf-class.md#str)。

## <a name="strstream"></a>  strstream::strstream

构造 `strstream` 类型的对象。

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>参数

`count` 缓冲区的大小。

`_Mode` 缓冲区输入和输出模式。 有关详细信息，请参阅 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。

`ptr` 缓冲区。

### <a name="remarks"></a>备注

这两个构造函数均可通过调用 [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **sb**)（其中 **sb** 是 [strstreambuf](../standard-library/strstreambuf-class.md) 类的存储对象）对基类进行初始化。 第一个构造函数还可通过调用 [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf) 初始化 **sb**。 第二个构造函数以下列两种方式之一初始化基类：

- 如果 `_Mode` & **ios_base::app**== 0，则 `ptr` 必须指定 `count` 元素数组的第一个元素，且构造函数调用 `strstreambuf`( `ptr`, `count`, `ptr`)。

- 否则，`ptr` 必须指定包含 C 字符串（其第一个元素由 `ptr` 指定）的计数元素数组的第一个元素，且构造函数调用 `strstreambuf`( `ptr`, `count`, `ptr` + `strlen`( `ptr`) )。

## <a name="see-also"></a>请参阅

[iostream](../standard-library/istream-typedefs.md#iostream)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>
