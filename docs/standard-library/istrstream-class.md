---
title: istrstream 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
dev_langs:
- C++
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d6be9c5d9a305032a61677c820832a76c464db4c
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="istrstream-class"></a>istrstream 类

描述了一种对象，它对从 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区提取元素和编码对象的操作进行控制。

## <a name="syntax"></a>语法

```cpp
class istrstream : public istream
```

## <a name="remarks"></a>备注

该对象存储 `strstreambuf` 类的对象。

> [!NOTE]
> 此类已弃用。 请考虑改用 [istringstream](../standard-library/sstream-typedefs.md#istringstream) 或 [wistringstream](../standard-library/sstream-typedefs.md#wistringstream)。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[istrstream](#istrstream)|构造 `istrstream` 类型的对象。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[rdbuf](#rdbuf)|返回指向流的关联 `strstreambuf` 对象的指针。|
|[str](#str)|调用 [freeze](../standard-library/strstreambuf-class.md#freeze)，然后将返回指向受控序列开头的指针。|

## <a name="requirements"></a>要求

**标头：**\<strstream>

**命名空间：** std

## <a name="istrstream"></a>istrstream::istrstream

构造 `istrstream` 类型的对象。

```cpp
explicit istrstream(
    const char* ptr);

explicit istrstream(
    char* ptr);

istrstream(
    const char* ptr,
    streamsize count);

istrstream(
    char* ptr,
    int count);
```

### <a name="parameters"></a>参数

`count` 缓冲区的长度 ( `ptr`)。

`ptr` 与其初始化缓冲区的内容。

### <a name="remarks"></a>备注

所有构造函数均可通过调用 [istream](../standard-library/istream-typedefs.md#istream)( **sb**)（其中 **sb** 是 [strstreambuf](../standard-library/strstreambuf-class.md) 类的存储的对象）对基类进行初始化。 前两个构造函数还通过调用 `strstreambuf`( ( **const**`char` \*) `ptr`, 0 ) 来初始化 **sb** 。 剩余的两个构造函数则调用 `strstreambuf`( ( **const**`char` *) `ptr`, `count` )。

## <a name="rdbuf"></a>istrstream::rdbuf

返回指向流关联的 strstreambuf 对象的指针。

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>返回值

指向流关联的 strstreambuf 对象的指针。

### <a name="remarks"></a>备注

此成员函数将指针类型的存储流缓冲区的地址返回到 [strstreambuf](../standard-library/strstreambuf-class.md)。

### <a name="example"></a>示例

有关使用 `rdbuf` 的示例，请参阅 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)。

## <a name="str"></a>istrstream::str

调用 [freeze](../standard-library/strstreambuf-class.md#freeze)，然后将返回指向受控序列开头的指针。

```cpp
char *str();
```

### <a name="return-value"></a>返回值

指向受控序列的开头的指针。

### <a name="remarks"></a>备注

此成员函数返回 [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str)。

### <a name="example"></a>示例

有关使用 **str** 的示例，请参阅 [strstream::str](../standard-library/strstreambuf-class.md#str)。

## <a name="see-also"></a>请参阅

[istream](../standard-library/istream-typedefs.md#istream)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>
