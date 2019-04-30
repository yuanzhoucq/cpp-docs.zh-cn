---
title: basic_streambuf 类
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::basic_streambuf
- streambuf/std::basic_streambuf::char_type
- streambuf/std::basic_streambuf::int_type
- streambuf/std::basic_streambuf::off_type
- streambuf/std::basic_streambuf::pos_type
- streambuf/std::basic_streambuf::traits_type
- streambuf/std::basic_streambuf::eback
- streambuf/std::basic_streambuf::egptr
- streambuf/std::basic_streambuf::epptr
- streambuf/std::basic_streambuf::gbump
- streambuf/std::basic_streambuf::getloc
- streambuf/std::basic_streambuf::gptr
- streambuf/std::basic_streambuf::imbue
- streambuf/std::basic_streambuf::in_avail
- streambuf/std::basic_streambuf::overflow
- streambuf/std::basic_streambuf::pbackfail
- streambuf/std::basic_streambuf::pbase
- streambuf/std::basic_streambuf::pbump
- streambuf/std::basic_streambuf::pptr
- streambuf/std::basic_streambuf::pubimbue
- streambuf/std::basic_streambuf::pubseekoff
- streambuf/std::basic_streambuf::pubseekpos
- streambuf/std::basic_streambuf::pubsetbuf
- streambuf/std::basic_streambuf::pubsync
- streambuf/std::basic_streambuf::sbumpc
- streambuf/std::basic_streambuf::seekoff
- streambuf/std::basic_streambuf::seekpos
- streambuf/std::basic_streambuf::setbuf
- streambuf/std::basic_streambuf::setg
- streambuf/std::basic_streambuf::setp
- streambuf/std::basic_streambuf::sgetc
- streambuf/std::basic_streambuf::sgetn
- streambuf/std::basic_streambuf::showmanyc
- streambuf/std::basic_streambuf::snextc
- streambuf/std::basic_streambuf::sputbackc
- streambuf/std::basic_streambuf::sputc
- streambuf/std::basic_streambuf::sputn
- streambuf/std::basic_streambuf::stossc
- streambuf/std::basic_streambuf::sungetc
- streambuf/std::basic_streambuf::swap
- streambuf/std::basic_streambuf::sync
- streambuf/std::basic_streambuf::uflow
- streambuf/std::basic_streambuf::underflow
- streambuf/std::basic_streambuf::xsgetn
- streambuf/std::basic_streambuf::xsputn
helpviewer_keywords:
- std::basic_streambuf [C++]
- std::basic_streambuf [C++], char_type
- std::basic_streambuf [C++], int_type
- std::basic_streambuf [C++], off_type
- std::basic_streambuf [C++], pos_type
- std::basic_streambuf [C++], traits_type
- std::basic_streambuf [C++], eback
- std::basic_streambuf [C++], egptr
- std::basic_streambuf [C++], epptr
- std::basic_streambuf [C++], gbump
- std::basic_streambuf [C++], getloc
- std::basic_streambuf [C++], gptr
- std::basic_streambuf [C++], imbue
- std::basic_streambuf [C++], in_avail
- std::basic_streambuf [C++], overflow
- std::basic_streambuf [C++], pbackfail
- std::basic_streambuf [C++], pbase
- std::basic_streambuf [C++], pbump
- std::basic_streambuf [C++], pptr
- std::basic_streambuf [C++], pubimbue
- std::basic_streambuf [C++], pubseekoff
- std::basic_streambuf [C++], pubseekpos
- std::basic_streambuf [C++], pubsetbuf
- std::basic_streambuf [C++], pubsync
- std::basic_streambuf [C++], sbumpc
- std::basic_streambuf [C++], seekoff
- std::basic_streambuf [C++], seekpos
- std::basic_streambuf [C++], setbuf
- std::basic_streambuf [C++], setg
- std::basic_streambuf [C++], setp
- std::basic_streambuf [C++], sgetc
- std::basic_streambuf [C++], sgetn
- std::basic_streambuf [C++], showmanyc
- std::basic_streambuf [C++], snextc
- std::basic_streambuf [C++], sputbackc
- std::basic_streambuf [C++], sputc
- std::basic_streambuf [C++], sputn
- std::basic_streambuf [C++], stossc
- std::basic_streambuf [C++], sungetc
- std::basic_streambuf [C++], swap
- std::basic_streambuf [C++], sync
- std::basic_streambuf [C++], uflow
- std::basic_streambuf [C++], underflow
- std::basic_streambuf [C++], xsgetn
- std::basic_streambuf [C++], xsputn
ms.assetid: 136af6c3-13bf-4501-9288-b93da26efac7
ms.openlocfilehash: 581652ea39d0729079666dc675b7214b4b3a4da3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62414173"
---
# <a name="basicstreambuf-class"></a>basic_streambuf 类

描述一个用于派生流缓冲区的抽象基类，该缓冲区控制元素与特定的流表示形式的来回传输。

## <a name="syntax"></a>语法

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_streambuf;
```

### <a name="parameters"></a>参数

*Elem*<br/>
一个 [char_type](#char_type)。

*Tr*<br/>
字符 [traits_type](#traits_type)。

## <a name="remarks"></a>备注

此模板类描述一个用于派生流缓冲区的抽象基类，该缓冲区控制元素与特定的流表示形式的来回传输。 类的对象`basic_streambuf`可帮助控制具有类型的元素的流*Tr*，也称为[char_type](#char_type)，其字符特征由类[char_traits](../standard-library/char-traits-struct.md)，也称为[traits_type](#traits_type)。

从概念上来说，每个流缓冲区控制两个独立的流：一个用于提取（输入），另一个用于插入（输出）。 但是，特定的表示形式可能会导致这些流中的一个或两个不可访问。 通常，它在两个流之间保持有某种关系。 例如，向 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`> 对象的输出流插入的内容，就是之后从其输入流中提取的内容。 当定位 [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> 对象的一个流时，将同时定位其他流。

模板类 `basic_streambuf` 的公共接口提供对所有流缓冲区通用但又专用的操作。 受保护的接口提供特定流的表示形式完成其工作所需的操作。 受保护的虚拟成员函数允许你为特定的流表示形式定制派生流缓冲区的行为。 此库中的每个派生流缓冲区描述它如何专用化其受保护虚拟成员函数的行为。 本主题中描述了基类的默认行为，基类通常不执行任何操作。

剩余的受保护成员函数控制将内容复制到任何存储以及从此类存储中复制内容的操作，这类存储用于缓冲出入流的传输。 例如，输入缓冲区的特征是：

- [eback](#eback)，指向缓冲区开头的指针。

- [gptr](#gptr)，指向要读取的下一个元素的指针。

- [egptr](#egptr)，刚超出缓冲区末尾的指针。

同样，输出缓冲区的特征是：

- [pbase](#pbase)，指向缓冲区开头的指针。

- [pptr](#pptr)，指向要写入的下一个元素的指针。

- [epptr](#epptr)，刚超出缓冲区末尾的指针。

对于任何缓冲区，使用以下协议：

- 如果下一个指针为 null，则不存在缓冲区。 否则，所有三个指针都将指向相同的序列。 可以安全地比较它们的顺序。

- 对于输出缓冲区，如果下一个指针与结束指针相比较小，则可以在下一个指针指定的写入位置处存储元素。

- 对于输入缓冲区，如果下一个指针与结束指针相比较小，则可以在下一个指针指定的读取位置处读取元素。

- 对于输入缓冲区，如果开始指针与下一个指针相比较小，则可以在递减的下一个指针指定的放回位置处放回元素。

为派生自 `basic_streambuf`< `Elem`, `Tr`> 的类编写的任何受保护虚拟成员函数必须共同协作来维护此协议。

`basic_streambuf`< `Elem`, `Tr`> 类的对象将存储前面所述的六个指针。 该对象还会将区域设置对象存储于类型 [locale](../standard-library/locale-class.md) 的对象中，以供派生的流缓冲区使用。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[basic_streambuf](#basic_streambuf)|构造 `basic_streambuf` 类型的对象。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[char_type](#char_type)|将类型名与 `Elem` 模板参数关联。|
|[int_type](#int_type)|将 `basic_streambuf` 范围内的类型名称与 `Elem`模板参数 关联。|
|[off_type](#off_type)|将 `basic_streambuf` 范围内的类型名称与 `Elem`模板参数 关联。|
|[pos_type](#pos_type)|将 `basic_streambuf` 范围内的类型名称与 `Elem`模板参数 关联。|
|[traits_type](#traits_type)|将类型名与 `Tr` 模板参数关联。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[eback](#eback)|一个受保护的函数，该函数返回指向输入缓冲区开头的指针。|
|[egptr](#egptr)|一个受保护的函数，该函数返回刚超出输入缓冲区末尾的指针。|
|[epptr](#epptr)|一个受保护的函数，该函数返回刚超出输出缓冲区末尾的指针。|
|[gbump](#gbump)|一个受保护的函数，该函数将 `count` 添加到输入缓冲区的下一个指针。|
|[getloc](#getloc)|获取 `basic_streambuf` 对象的区域设置。|
|[gptr](#gptr)|一个受保护的函数，该函数返回指向输入缓冲区的下一个元素的指针。|
|[imbue](#imbue)|由 [pubimbue](#pubimbue) 调用的受保护虚拟函数。|
|[in_avail](#in_avail)|返回可随时从缓冲区读取的元素数目。|
|[overflow](#overflow)|将新字符插入到已满缓冲区时可以调用的受保护虚函数。|
|[pbackfail](#pbackfail)|一个受保护虚拟成员函数，该函数尝试将元素放回输入流中，随后使它成为当前元素（由下一个指针指向）。|
|[pbase](#pbase)|一个受保护的函数，该函数返回指向输出缓冲区开头的指针。|
|[pbump](#pbump)|一个受保护的函数，该函数将 `count` 添加到输出缓冲区的下一个指针。|
|[pptr](#pptr)|一个受保护的函数，该函数返回指向输出缓冲区的下一个元素的指针。|
|[pubimbue](#pubimbue)|设置 `basic_streambuf` 对象的区域设置。|
|[pubseekoff](#pubseekoff)|调用 [seekoff](#seekoff)，它是在派生类中进行了重写的受保护虚拟函数。|
|[pubseekpos](#pubseekpos)|调用 [seekpos](#seekpos)，它是在派生类中进行了重写并且重置了当前指针位置的受保护虚拟函数。|
|[pubsetbuf](#pubsetbuf)|调用 [setbuf](#setbuf)，它是在派生类中进行了重写的受保护虚拟函数。|
|[pubsync](#pubsync)|调用 [sync](#sync)，它是在派生类中进行了重写并且更新了与此缓冲区关联的外部流的受保护虚拟函数。|
|[sbumpc](#sbumpc)|读取并返回当前元素，从而移动流指针。|
|[seekoff](#seekoff)|受保护虚拟成员函数尝试更改受控制流的当前位置。|
|[seekpos](#seekpos)|受保护虚拟成员函数尝试更改受控制流的当前位置。|
|[setbuf](#setbuf)|受保护虚拟成员函数执行特定于每个派生流缓冲区的操作。|
|[setg](#setg)|一个受保护的函数，该函数将 `_Gbeg` 存储到开始指针，将 `_Gnext` 存储到下一个指针，并将 `_Gend` 存储到输入缓冲区的结束指针。|
|[setp](#setp)|一个受保护的函数，该函数将 `_Pbeg` 存储到开始指针，并将 `_Pend` 存储到输出缓冲区的结束指针。|
|[sgetc](#sgetc)|返回当前元素，但不更改流中的位置。|
|[sgetn](#sgetn)|返回读取的元素数目。|
|[showmanyc](#showmanyc)|一个受保护的虚拟成员函数，该函数返回可以从输入流中提取并确保该程序将不需要无限期等待的字符数计数。|
|[snextc](#snextc)|读取当前元素并返回以下元素。|
|[sputbackc](#sputbackc)|将 `char_type` 放入流中。|
|[sputc](#sputc)|将一个字符放入流中。|
|[sputn](#sputn)|将一个字符串放入流中。|
|[stossc](#stossc)|越过流中的当前元素。|
|[sungetc](#sungetc)|从流中获取字符。|
|[swap](#swap)|将此对象中的值与所提供 `basic_streambuf` 对象参数中的值进行交换。|
|[sync](#sync)|一个受保护的虚拟函数，它尝试将受控流与任何关联的外部流同步。|
|[uflow](#uflow)|一个受保护的虚拟函数，它从输入流中提取当前元素。|
|[underflow](#underflow)|一个受保护的虚拟函数，它从输入流中提取当前元素。|
|[xsgetn](#xsgetn)|一个受保护的虚拟函数，它从输入流中提取元素。|
|[xsputn](#xsputn)|一个受保护的虚拟函数，它将元素插入到输出流中。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator=](#op_eq)|从另一个 `basic_streambuf` 对象为此对象赋值。|

## <a name="requirements"></a>要求

**标头：**\<streambuf>

**命名空间：** std

## <a name="basic_streambuf"></a>  basic_streambuf::basic_streambuf

构造 `basic_streambuf` 类型的对象。

```cpp
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```

### <a name="parameters"></a>参数

*right*<br/>
对用于为此 `basic_streambuf` 对象设置值的 `basic_streambuf` 对象的左值引用。

### <a name="remarks"></a>备注

第一个受保护构造函数将 null 指针存储在控制输入缓冲区和输出缓冲区的所有指针中。 此外，它还将 `locale::classic` 存储在区域设置对象中。 有关详细信息，请参见 [locale::classic](../standard-library/locale-class.md#classic)。

第二个受保护的构造函数将指针和区域设置从复制*右*。

## <a name="char_type"></a>  basic_streambuf::char_type

将类型名与 **Elem** 模板参数关联。

```cpp
typedef Elem char_type;
```

## <a name="eback"></a>  basic_streambuf::eback

一个受保护的函数，该函数返回指向输入缓冲区开头的指针。

```cpp
char_type *eback() const;
```

### <a name="return-value"></a>返回值

指向输入缓冲区开头的指针。

## <a name="egptr"></a>  basic_streambuf::egptr

一个受保护的函数，该函数返回刚超出输入缓冲区末尾的指针。

```cpp
char_type *egptr() const;
```

### <a name="return-value"></a>返回值

刚超出输入缓冲区末尾的指针。

## <a name="epptr"></a>  basic_streambuf::epptr

一个受保护的函数，该函数返回刚超出输出缓冲区末尾的指针。

```cpp
char_type *epptr() const;
```

### <a name="return-value"></a>返回值

刚超出输出缓冲区末尾的指针。

## <a name="gbump"></a>  basic_streambuf::gbump

将添加一个受保护的函数*计数*到输入缓冲区的下一个指针。

```cpp
void gbump(int count);
```

### <a name="parameters"></a>参数

*count*<br/>
让指针前进的量。

## <a name="getloc"></a>  basic_streambuf::getloc

获取 basic_streambuf 对象的区域设置。

```cpp
locale getloc() const;
```

### <a name="return-value"></a>返回值

存储的区域设置对象。

### <a name="remarks"></a>备注

相关信息，请参阅 [ios_base::getloc](../standard-library/ios-base-class.md#getloc)。

### <a name="example"></a>示例

```cpp
// basic_streambuf_getloc.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << cout.rdbuf( )->getloc( ).name( ).c_str( ) << endl;
}
```

```Output
C
```

## <a name="gptr"></a>  basic_streambuf::gptr

一个受保护的函数，该函数返回指向输入缓冲区的下一个元素的指针。

```cpp
char_type *gptr() const;
```

### <a name="return-value"></a>返回值

指向输入缓冲区下一个元素的指针。

## <a name="imbue"></a>  basic_streambuf::imbue

由 [pubimbue](#pubimbue) 调用的受保护虚拟函数。

```cpp
virtual void imbue(const locale& _Loc);
```

### <a name="parameters"></a>参数

*_Loc*<br/>
对区域设置的引用。

### <a name="remarks"></a>备注

默认行为是不执行任何操作。

## <a name="in_avail"></a>  basic_streambuf::in_avail

返回可随时从缓冲区读取的元素数目。

```cpp
streamsize in_avail();
```

### <a name="return-value"></a>返回值

可随时从缓冲区读取的元素数目。

### <a name="remarks"></a>备注

如果[读取位置](../standard-library/basic-streambuf-class.md)不可用，此成员函数返回[egptr](#egptr) - [gptr](#gptr)。 否则，将返回 [showmanyc](#showmanyc)。

### <a name="example"></a>示例

```cpp
// basic_streambuf_in_avail.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   char c;
   // cin's buffer is empty, in_avail will return 0
   cout << cin.rdbuf( )->in_avail( ) << endl;
   cin >> c;
   cout << cin.rdbuf( )->in_avail( ) << endl;
}
```

## <a name="int_type"></a>  basic_streambuf::int_type

将 basic_streambuf 作用域内的类型名称与模板参数中的其中一个类型相关联。

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_streambuf::off_type

将 basic_streambuf 作用域内的类型名称与模板参数中的其中一个类型相关联。

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="op_eq"></a>  basic_streambuf::operator=

从另一个 `basic_streambuf` 对象为此对象赋值。

```cpp
basic_streambuf& operator=(const basic_streambuf& right);
```

### <a name="parameters"></a>参数

*right*<br/>
对用于为此对象赋值的 `basic_streambuf` 对象的左值引用。

### <a name="remarks"></a>备注

受保护的成员运算符将从复制*右*控制输入的缓冲区和输出缓冲区的指针。 它还将 `right.`[getloc()](#getloc) 存储在 `locale object` 中。 它将返回 `*this`。

## <a name="overflow"></a>  basic_streambuf::overflow

将新字符插入到已满缓冲区时可以调用的受保护虚函数。

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>参数

*_Meta*<br/>
要插入到缓冲区中的字符或 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)。

### <a name="return-value"></a>返回值

如果该函数不能成功，它将返回 **traits_type::eof** 或引发异常。 否则，它将返回 **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*)。 默认行为是返回 **traits_type::eof**。

### <a name="remarks"></a>备注

如果 *\_Meta*不会比较等于**traits_type:: eof**，受保护虚拟成员函数尝试将元素插入**traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_元*) 到输出流中。 它可以用多种方法执行此操作：

- 如果 `write position` 可用，它可将元素存储到写入位置并增加输出缓冲区的下一个指针。

- 它可以通过为输出缓冲区分配新的或额外的存储空间，提供写入位置。

- 可以通过写出到某些外部目标、输出缓冲区的开头和下一个指针之间的某些或所有元素使写入位置可用。

虚拟溢出函数，以及 [sync](#sync) 和 [underflow](#underflow) 函数，共同定义了 streambuf 派生的类的特征。 每个派生的类实现下溢的方式可能不同，但是调用流类的接口是相同的。

在 put 区域为满时，`overflow` 函数最常由公共 `streambuf` 函数（如 `sputc` 和 `sputn`）调用，但其他类（包括流类）可以在任何时候调用 `overflow`。

该函数使用 `pbase` 和 `pptr` 指针之间 put 区域中的字符，然后重新初始化 put 区域。 `overflow` 函数必须也使用 `nCh`（如果 `nCh` 不为 `EOF`），或者，它可能选择将该字符放入新的 put 区域，以便在下一次调用时使用它。

使用的定义根据派生的类而有所不同。 例如，`filebuf` 类将其字符写入到文件，而 `strstreambuf` 类则将字符保留在它的缓冲区中，并且（缓冲区被指定为动态）扩展缓冲区，以响应溢出的调用。 此扩展通过释放旧的缓冲区并将其替换为新的、较大的缓冲区来实现。 根据需要调整指针。

## <a name="pbackfail"></a>  basic_streambuf::pbackfail

一个受保护虚拟成员函数，该函数尝试将元素放回输入流中，随后使它成为当前元素（由下一个指针指向）。

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>参数

*_Meta*<br/>
要插入到缓冲区中的字符或 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)。

### <a name="return-value"></a>返回值

如果该函数不能成功，它将返回 **traits_type::eof** 或引发异常。 否则，将返回其他值。 默认行为是返回 **traits_type::eof**。

### <a name="remarks"></a>备注

如果 *\_Meta*经比较等于**traits_type:: eof**，要推送回的元素实际上是已在当前元素之前的流中的一个。 否则，该元素将替换为**traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_元*)。 该函数可以用多种方法放回元素：

- 如果放回位置可用，它可将元素存储到放回位置并递减输入缓冲区的下一个指针。

- 通过分配输入缓冲区的新的或其他存储使放回位置可用。

- 对于具有常见的输入和输出流的流缓冲区，可以通过写出到某些外部目标、输出缓冲区的开头和下一个指针之间的某些或所有元素使放回位置可用。

## <a name="pbase"></a>  basic_streambuf::pbase

一个受保护的函数，该函数返回指向输出缓冲区开头的指针。

```cpp
char_type *pbase() const;
```

### <a name="return-value"></a>返回值

指向输出缓冲区开头的指针。

## <a name="pbump"></a>  basic_streambuf::pbump

将添加一个受保护的函数*计数*到输出缓冲区的下一个指针。

```cpp
void pbump(int count);
```

### <a name="parameters"></a>参数

*count*<br/>
向前移动写入位置的字符数。

## <a name="pos_type"></a>  basic_streambuf::pos_type

将 basic_streambuf 作用域内的类型名称与模板参数中的其中一个类型相关联。

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="pptr"></a>  basic_streambuf::pptr

一个受保护的函数，该函数返回指向输出缓冲区的下一个元素的指针。

```cpp
char_type *pptr() const;
```

### <a name="return-value"></a>返回值

指向输出缓冲区下一个元素的指针。

## <a name="pubimbue"></a>  basic_streambuf::pubimbue

设置 basic_streambuf 对象的区域设置。

```cpp
locale pubimbue(const locale& _Loc);
```

### <a name="parameters"></a>参数

*_Loc*<br/>
对区域设置的引用。

### <a name="return-value"></a>返回值

存储在区域设置对象中的以前的值。

### <a name="remarks"></a>备注

成员函数将 _ *Loc* 存储在区域设置对象中，并调用 [imbue](#imbue)。

### <a name="example"></a>示例

有关使用 `pubimbue` 的示例，请参阅 [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue)。

## <a name="pubseekoff"></a>  basic_streambuf::pubseekoff

调用 [seekoff](#seekoff)，它是在派生类中进行了重写的受保护虚拟函数。

```cpp
pos_type pubseekoff(off_type _Off,
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

返回新位置或无效的流位置 ( [seekoff](#seekoff)(_ *Off*, `_Way`, `_Which`) )。

### <a name="remarks"></a>备注

将相对于指针移 *_Way*。

## <a name="pubseekpos"></a>  basic_streambuf::pubseekpos

调用 [seekpos](#seekpos)，它是在派生类中进行了重写并且重置了当前指针位置的受保护虚拟函数。

```cpp
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>参数

*_Sp*<br/>
要搜寻的位置。

*_Which*<br/>
指定指针位置的模式。 默认允许修改读取和写入位置。

### <a name="return-value"></a>返回值

新位置或无效的流位置。 若要确定流位置是否有效，请比较返回值和 `pos_type(off_type(-1))`。

### <a name="remarks"></a>备注

此成员函数返回 [seekpos](#seekpos)(_ *Sp*, `_Which`)。

## <a name="pubsetbuf"></a>  basic_streambuf::pubsetbuf

调用 [setbuf](#setbuf)，它是在派生类中进行了重写的受保护虚拟函数。

```cpp
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>参数

*_Buffer*<br/>
指向此实例化的 `char_type` 的指针。

*count*<br/>
缓冲区的大小。

### <a name="return-value"></a>返回值

返回 [setbuf](#setbuf)( `_Buffer`, `count`)。

## <a name="pubsync"></a>  basic_streambuf::pubsync

调用 [sync](#sync)，它是在派生类中重写并更新了与此缓冲区相关联的外部流的受保护虚拟函数。

```cpp
int pubsync();
```

### <a name="return-value"></a>返回值

返回[同步](#sync)或者为-1 失败。

## <a name="sbumpc"></a>  basic_streambuf::sbumpc

读取并返回当前元素，从而移动流指针。

```cpp
int_type sbumpc();
```

### <a name="return-value"></a>返回值

当前元素。

### <a name="remarks"></a>备注

如果读取位置可用，则成员函数返回 **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( <strong>\*</strong>[gptr](#gptr)) 并递增输入缓冲区的下一个指针。 否则，返回 [uflow](#uflow)。

### <a name="example"></a>示例

```cpp
// basic_streambuf_sbumpc.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 0;
   i = cin.rdbuf( )->sbumpc( );
   cout << i << endl;
}
```

```Input
3
```

```Output
33
51
```

## <a name="seekoff"></a>  basic_streambuf::seekoff

一个受保护的虚拟成员函数，它尝试更改受控流的当前位置。

```cpp
virtual pos_type seekoff(
    off_type _Off,
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

返回新位置或无效的流位置 ( `seekoff` (_ *Off*, `_Way`, `_Which`) )。

### <a name="remarks"></a>备注

确定新的位置，如下所示：

- 如果 `_Way` ==  `ios_base::beg`，新位置是流的开始位置加上 _ *Off*。

- 如果 `_Way` ==  `ios_base::cur`，新位置是当前流位置加上 _*Off*。

- 如果 `_Way` ==  `ios_base::end`，新的位置是当前流末尾加上 _*Off*。

通常情况下，如果 **which & ios_base::in** 为非零值，则输入流受影响；如果 **which & ios_base::out** 为非零值，则输出流受影响。 但是，此参数的实际用法因派生的流缓冲区而有所不同。

如果该函数成功改变了一个或多个流位置，它将返回结果流位置或其中一个结果流位置。 否则，返回一个无效的流位置。 默认行为是返回无效的流位置。

## <a name="seekpos"></a>  basic_streambuf::seekpos

一个受保护的虚拟成员函数，它尝试更改受控流的当前位置。

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>参数

*_Sp*<br/>
要搜寻的位置。

*_Which*<br/>
指定指针位置的模式。 默认允许修改读取和写入位置。

### <a name="return-value"></a>返回值

新位置，或无效的流位置。 若要确定流位置是否无效，请比较返回值与 `pos_type(off_type(-1))`。

### <a name="remarks"></a>备注

新的位置是 _ *Sp*。

通常情况下，如果 **which & ios_base::in** 为非零值，则输入流受影响；如果 **which & ios_base::out** 为非零值，则输出流受影响。 但是，此参数的实际用法因派生的流缓冲区而有所不同。

如果该函数成功改变了一个或多个流位置，它将返回结果流位置或其中一个结果流位置。 否则，返回一个无效的流位置 (-1)。 默认行为是返回无效的流位置。

## <a name="setbuf"></a>  basic_streambuf::setbuf

受保护虚拟成员函数，执行特定于每个派生流缓冲区的操作。

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>参数

*_Buffer*<br/>
指向缓冲区的指针。

*count*<br/>
缓冲区的大小。

### <a name="return-value"></a>返回值

默认行为是返回 **this**。

### <a name="remarks"></a>备注

请参阅 [basic_filebuf](../standard-library/basic-filebuf-class.md)。 `setbuf` 提供一个内存区域，以供 `streambuf` 对象使用。 在派生类中定义的缓冲区的使用方式。

## <a name="setg"></a>  basic_streambuf::setg

一个受保护函数，用于将 _*Gbeg* 存储到开始指针，将 `_Gnext` 存储到下一个指针，并将 `_Gend` 存储到输入缓冲区的结束指针。

```cpp
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```

### <a name="parameters"></a>参数

*_Gbeg*<br/>
指向缓冲区开头的指针。

*_Gnext*<br/>
指向缓冲区中间某处的指针。

*_Gend*<br/>
指向缓冲区末尾的指针。

## <a name="setp"></a>  basic_streambuf::setp

将存储的受保护的函数 *_Pbeg*到开始指针和 *_Pend*输出缓冲区的结束指针。

```cpp
void setp(char_type* _Pbeg, char_type* _Pend);
```

### <a name="parameters"></a>参数

*_Pbeg*<br/>
指向缓冲区开头的指针。

*_Pend*<br/>
指向缓冲区末尾的指针。

## <a name="sgetc"></a>  basic_streambuf::sgetc

返回当前元素，但不更改流中的位置。

```cpp
int_type sgetc();
```

### <a name="return-value"></a>返回值

当前元素。

### <a name="remarks"></a>备注

如果读取位置可用，则成员函数返回 **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*`[gptr](#gptr))。 否则，返回 [underflow](#underflow)。

### <a name="example"></a>示例

```cpp
// basic_streambuf_sgetc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   ifstream myfile( "basic_streambuf_sgetc.txt", ios::in );

   char i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
   i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
}
```

## <a name="sgetn"></a>  basic_streambuf::sgetn

提取最多*计数*字符从输入缓冲区并将它们存储在提供的缓冲区*ptr*。

此方法可能并不安全，因为它依赖于调用方检查所传递的值是否正确。

```cpp
streamsize sgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>参数

*ptr*<br/>
要包含提取字符的缓冲区。

*count*<br/>
要读取的元素数目。

### <a name="return-value"></a>返回值

要读取的元素数目。 有关详细信息，请参阅 [streamsize](../standard-library/ios-typedefs.md#streamsize)。

### <a name="remarks"></a>备注

此成员函数返回 [xsgetn](#xsgetn)( `ptr`, `count`)。

### <a name="example"></a>示例

```cpp
// basic_streambuf_sgetn.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;

    ifstream myfile("basic_streambuf_sgetn.txt", ios::in);
    char a[10];

    // Extract 3 characters from myfile and store them in a.
    streamsize i = myfile.rdbuf()->sgetn(&a[0], 3);  // C4996
    a[i] = myfile.widen('\0');

    // Display the size and contents of the buffer passed to sgetn.
    cout << i << " " << a << endl;

    // Display the contents of the original input buffer.
    cout << myfile.rdbuf() << endl;
}
```

## <a name="showmanyc"></a>  basic_streambuf::showmanyc

一个受保护虚拟成员函数，该函数返回可以从输入流中提取并确保该程序将不需要无限期等待的字符数计数。

```cpp
virtual streamsize showmanyc();
```

### <a name="return-value"></a>返回值

默认行为是返回零。

## <a name="snextc"></a>  basic_streambuf::snextc

读取当前元素并返回以下元素。

```cpp
int_type snextc();
```

### <a name="return-value"></a>返回值

流中的下一个元素。

### <a name="remarks"></a>备注

成员函数调用 [sbumpc](#sbumpc)，如果该函数返回 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)，则返回 **traits_type::eof**。 否则，返回 [sgetc](#sgetc)。

### <a name="example"></a>示例

```cpp
// basic_streambuf_snextc.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   int i = 0;
   i = cin.rdbuf( )->snextc( );
   // cout << ( int )char_traits<char>::eof << endl;
   cout << i << endl;
}
```

```Input
aa
```

```Output
aa97
```

## <a name="sputbackc"></a>  basic_streambuf::sputbackc

将 char_type 放入流中。

```cpp
int_type sputbackc(char_type _Ch);
```

### <a name="parameters"></a>参数

*_Ch*<br/>
字符。

### <a name="return-value"></a>返回值

返回字符或失败。

### <a name="remarks"></a>备注

如果放回位置可用并 *_Ch*经比较等于字符存储在该位置，则成员函数递减输入的缓冲区和返回的下一个指针**traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `_Ch`)。 否则，它将返回 [pbackfail](#pbackfail)( `_Ch`)。

### <a name="example"></a>示例

```cpp
// basic_streambuf_sputbackc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;

    ifstream myfile("basic_streambuf_sputbackc.txt",
        ios::in);

    int i = myfile.rdbuf()->sbumpc();
    cout << (char)i << endl;
    int j = myfile.rdbuf()->sputbackc('z');
    if (j == 'z')
    {
        cout << "it worked" << endl;
    }
    i = myfile.rdbuf()->sgetc();
    cout << (char)i << endl;
}
```

## <a name="sputc"></a>  basic_streambuf::sputc

将一个字符放入流中。

```cpp
int_type sputc(char_type _Ch);
```

### <a name="parameters"></a>参数

*_Ch*<br/>
字符。

### <a name="return-value"></a>返回值

如果成功，则返回字符。

### <a name="remarks"></a>备注

如果`write position`不可用，此成员函数存储 *_Ch*中的写入位置，递增输出缓冲区的下一个指针，并返回**traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `_Ch`). 否则，返回 [overflow](#overflow)( `_Ch`)。

### <a name="example"></a>示例

```cpp
// basic_streambuf_sputc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   int i = cout.rdbuf( )->sputc( 'a' );
   cout << endl << ( char )i << endl;
}
```

```Output
a
a
```

## <a name="sputn"></a>  basic_streambuf::sputn

将一个字符串放入流中。

```cpp
streamsize sputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>参数

*ptr*<br/>
字符串。

*count*<br/>
字符数。

### <a name="return-value"></a>返回值

实际插入流的字符数。

### <a name="remarks"></a>备注

此成员函数返回 [xsgetn](#xsputn)( `ptr`, `count`)。 有关详细信息，请参阅此成员的“备注”部分。

### <a name="example"></a>示例

```cpp
// basic_streambuf_sputn.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;

    streamsize i = cout.rdbuf()->sputn("test", 4);
    cout << endl << i << endl;
}
```

```Output
test
4
```

## <a name="stossc"></a>  basic_streambuf::stossc

越过流中的当前元素。

```cpp
void stossc();
```

### <a name="remarks"></a>备注

成员函数调用 [sbumpc](#sbumpc)。 请注意，提供该成员函数不需要实现。

### <a name="example"></a>示例

```cpp
// basic_streambuf_stossc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   ifstream myfile( "basic_streambuf_stossc.txt", ios::in );

   myfile.rdbuf( )->stossc( );
   char i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
}
```

## <a name="sungetc"></a>  basic_streambuf::sungetc

从流中获取字符。

```cpp
int_type sungetc();
```

### <a name="return-value"></a>返回值

返回字符或失败。

### <a name="remarks"></a>备注

如果放回位置可用，则成员函数递减输入缓冲区的下一个指针并返回 `traits_type::`[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*`[gptr](#gptr))。 但是，并不总是能够确定读取的最后一个字符，使得可以在当前缓冲区的状态中将其捕获。 如果这为 true，则函数返回 [pbackfail](#pbackfail)。 若要避免这种情况，请跟踪字符，以放回并调用 `sputbackc(ch)`；如果没有在流的开始位置对其调用或尝试放回多个字符，则此调用不会失败。

### <a name="example"></a>示例

```cpp
// basic_streambuf_sungetc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   ifstream myfile( "basic_streambuf_sungetc.txt", ios::in );

   // Read and increment
   int i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;

   // Read and increment
   i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;

   // Decrement, read, and do not increment
   i = myfile.rdbuf( )->sungetc( );
   cout << ( char )i << endl;

   i = myfile.rdbuf( )->sungetc( );
   cout << ( char )i << endl;

   i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;
}
```

## <a name="swap"></a>  basic_streambuf::swap

将此对象中的值与提供的 `basic_streambuf` 对象中的值进行交换。

```cpp
void swap(basic_streambuf& right);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*right*|对用于交换值的 `basic_streambuf` 对象的左值引用。|

### <a name="remarks"></a>备注

与受保护的成员函数交换*右*控制的所有指针`input buffer`和`output buffer`。 它还将 `right.`[getloc()](#getloc) 与 `locale` 对象进行交换。

## <a name="sync"></a>  basic_streambuf::sync

一个受保护的虚拟函数，它尝试将受控流与任何关联的外部流同步。

```cpp
virtual int sync();
```

### <a name="return-value"></a>返回值

如果该函数不成功，它将返回 -1。 默认行为是返回零。

### <a name="remarks"></a>备注

`sync` 涉及写出输出缓冲区的开头和下一个指针间的任意元素。 它不涉及放回输入缓冲区的下一个和结束指针之间的任何元素。

## <a name="traits_type"></a>  basic_streambuf::traits_type

将类型名与 **Tr** 模板参数关联。

```cpp
typedef Tr traits_type;
```

## <a name="uflow"></a>  basic_streambuf::uflow

一个受保护的虚拟函数，它从输入流中提取当前元素。

```cpp
virtual int_type uflow();
```

### <a name="return-value"></a>返回值

当前元素。

### <a name="remarks"></a>备注

受保护虚拟成员函数尝试从输入流提取当前元素 **ch**，提升当前流位置，并返回元素作为 **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**)。 它可以用多种方法执行此操作：

- 如果读取位置可用，它采用 **ch** 作为存储在读取位置中的元素，并提升输入缓冲区的下一个指针。

- 它可以从某些外部源直接读取元素，并将其传输为值 **ch**。

- 对于具有常见的输入和输出流的流缓冲区，可以通过写出到某些外部目标、输出缓冲区的开头和下一个指针之间的某些或所有元素使读取位置可用。 或者，可以为输入缓冲区分配新的或其他存储。 然后，该函数从某些外部源的一个或多个元素中进行读取。

如果该函数不成功，它将返回 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)，或者引发异常。 否则，它返回输入流中的当前元素 `ch`，按上文所述进行转换，并提升输入缓冲区的下一个指针。 默认行为是调用 [underflow](#underflow)，并且，如果该函数返回 **traits_type::eof**，则返回 **traits_type::eof**。 否则，它返回输入流中的当前元素 **ch**，按上文所述进行转换，并为输入缓冲区提升下一个指针。

## <a name="underflow"></a>  basic_streambuf::underflow

受保护虚函数从输入流中提取当前元素。

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>返回值

当前元素。

### <a name="remarks"></a>备注

受保护虚拟成员函数从输入流提取当前元素 **ch**，而不会提升当前流位置，并将其返回为 `traits_type::`[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**)。 它可以用多种方法执行此操作：

- 如果读取位置可用，则 **ch** 为存储在读取位置的元素。 有关详细信息，请参阅 [basic_streambuf 类](../standard-library/basic-streambuf-class.md)的“备注”部分。

- 通过为输入缓冲区分配新的或其他存储，然后从某些外部源中读取一个或多个元素使读取位置可用。 有关详细信息，请参阅 [basic_streambuf 类](../standard-library/basic-streambuf-class.md)的“备注”部分。

如果该函数不能成功，它将返回 `traits_type::`[eof](../standard-library/char-traits-struct.md#eof)`()` 或引发异常。 否则，它返回输入流中的当前元素，并根据前文所述进行转换。 默认行为是返回 `traits_type::eof()`。

虚拟 `underflow` 函数，以及 [sync](#sync) 和 [overflow](#overflow) 函数，共同定义 `streambuf` 派生的类的特征。 每个派生的类实现 `underflow` 的方式可能不同，但是调用流类的接口是相同的。

在 get 区域为空时，`underflow` 函数最常由公共 `streambuf` 函数调用，如 [sgetc](#sgetc) 和 [sgetn](#sgetn)，但其他类（包括流类）可以在任何时候调用 `underflow`。

`underflow` 函数为 get 区域提供来自输入源的字符。 如果 get 区域包含字符，则 `underflow` 返回第一个字符。 如果 get 区域为空，则填充 get 区域并返回下一个字符（即留在 get 区域中的字符）。 如果没有更多可用的字符，则 `underflow` 返回 `EOF` 并将 get 区域留空。

在 `strstreambuf` 类中，`underflow` 调整 [egptr](#egptr) 指针，以访问由调用 `overflow` 动态分配的存储。

## <a name="xsgetn"></a>  basic_streambuf::xsgetn

一个受保护虚拟函数，它从输入流中提取元素。

此方法可能并不安全，因为它依赖于调用方检查所传递的值是否正确。

```cpp
virtual streamsize xsgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>参数

*ptr*<br/>
要包含提取字符的缓冲区。

*count*<br/>
要提取的元素数。

### <a name="return-value"></a>返回值

已提取的元素数。

### <a name="remarks"></a>备注

受保护虚拟成员函数提取最多*计数*元素从输入流中，如果通过重复调用[sbumpc](#sbumpc)，并将它们存储在数组开始*ptr*. 它返回实际提取的元素数。

## <a name="xsputn"></a>  basic_streambuf::xsputn

受保护虚拟函数，它将元素插入到输出流中。

```cpp
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>参数

*ptr*<br/>
指向要插入的元素的指针。

*count*<br/>
要插入的元素数。

### <a name="return-value"></a>返回值

它返回实际插入到流的元素数。

### <a name="remarks"></a>备注

受保护虚拟成员函数插入最多*计数*元素插入输出流，通过重复调用像[sputc](#sputc)，从数组开头*ptr*。 插入到输出流中的字符一次停止所有*计数*已写入的字符，或如果调用`sputc( count)`将返回`traits::eof()`。 它返回实际插入的元素数。

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>
