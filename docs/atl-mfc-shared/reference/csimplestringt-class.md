---
title: CSimpleStringT 类
ms.date: 10/18/2018
f1_keywords:
- CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::PCXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::PXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::Append
- ATLSIMPSTR/ATL::CSimpleStringT::AppendChar
- ATLSIMPSTR/ATL::CSimpleStringT::CopyChars
- ATLSIMPSTR/ATL::CSimpleStringT::CopyCharsOverlapped
- ATLSIMPSTR/ATL::CSimpleStringT::Empty
- ATLSIMPSTR/ATL::CSimpleStringT::FreeExtra
- ATLSIMPSTR/ATL::CSimpleStringT::GetAllocLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetAt
- ATLSIMPSTR/ATL::CSimpleStringT::GetBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::GetBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetManager
- ATLSIMPSTR/ATL::CSimpleStringT::GetString
- ATLSIMPSTR/ATL::CSimpleStringT::IsEmpty
- ATLSIMPSTR/ATL::CSimpleStringT::LockBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::Preallocate
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::SetAt
- ATLSIMPSTR/ATL::CSimpleStringT::SetManager
- ATLSIMPSTR/ATL::CSimpleStringT::SetString
- ATLSIMPSTR/ATL::CSimpleStringT::StringLength
- ATLSIMPSTR/ATL::CSimpleStringT::Truncate
- ATLSIMPSTR/ATL::CSimpleStringT::UnlockBuffer
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
ms.openlocfilehash: c033346b7a687a1c6778ad23e30ee0e73c787ad8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491447"
---
# <a name="csimplestringt-class"></a>CSimpleStringT 类

此类表示一个`CSimpleStringT`对象。

## <a name="syntax"></a>语法

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>参数

*BaseType*<br/>
字符串类的字符类型。 可以是以下各项之一：

- **char**（对于 ANSI 字符串）。

- **wchar_t**（对于 Unicode 字符串）。

- TCHAR （用于 ANSI 和 Unicode 字符串）。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|name|描述|
|----------|-----------------|
|[CSimpleStringT::PCXSTR](#pcxstr)|指向常量字符串的指针。|
|[CSimpleStringT::PXSTR](#pxstr)|指向字符串的指针。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|以`CSimpleStringT`多种方式构造对象。|
|[CSimpleStringT::~CSimpleStringT](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSimpleStringT::Append](#append)|将对象追加到现有`CSimpleStringT`对象。 `CSimpleStringT`|
|[CSimpleStringT::AppendChar](#appendchar)|在现有`CSimpleStringT`对象后面追加一个字符。|
|[CSimpleStringT::CopyChars](#copychars)|将一个或多个字符复制到另一个字符串。|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|将一个或多个字符复制到缓冲区重叠的另一个字符串。|
|[CSimpleStringT::Empty](#empty)|强制字符串长度为零。|
|[CSimpleStringT::FreeExtra](#freeextra)|释放先前由字符串对象分配的任何额外内存。|
|[CSimpleStringT::GetAllocLength](#getalloclength)|检索`CSimpleStringT`对象的分配长度。|
|[CSimpleStringT::GetAt](#getat)|返回指定位置处的字符。|
|[CSimpleStringT::GetBuffer](#getbuffer)|返回一个指向中`CSimpleStringT`的字符的指针。|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|返回一个指向中`CSimpleStringT`的字符的指针，并将截断为指定长度。|
|[CSimpleStringT::GetLength](#getlength)|返回`CSimpleStringT`对象中的字符数。|
|[CSimpleStringT::GetManager](#getmanager)|检索`CSimpleStringT`对象的内存管理器。|
|[CSimpleStringT::GetString](#getstring)|检索字符串|
|[CSimpleStringT::IsEmpty](#isempty)|测试`CSimpleStringT`对象是否不包含任何字符。|
|[CSimpleStringT::LockBuffer](#lockbuffer)|禁用引用计数并保护缓冲区中的字符串。|
|[CSimpleStringT::Preallocate](#preallocate)|为字符缓冲区分配特定的内存量。|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|释放由`GetBuffer`返回的缓冲区的控制。|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|释放由`GetBuffer`返回的缓冲区的控制。|
|[CSimpleStringT::SetAt](#setat)|设置给定位置处的字符。|
|[CSimpleStringT::SetManager](#setmanager)|设置`CSimpleStringT`对象的内存管理器。|
|[CSimpleStringT::SetString](#setstring)|设置`CSimpleStringT`对象的字符串。|
|[CSimpleStringT::StringLength](#stringlength)|返回指定字符串中的字符数。|
|[CSimpleStringT::Truncate](#truncate)|将字符串截断为指定长度。|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|启用引用计数，并释放缓冲区中的字符串。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CSimpleStringT::operator PCXSTR](#operator_pcxstr)|直接访问存储在`CSimpleStringT`对象中的字符作为 C 样式字符串。|
|[CSimpleStringT::operator\[\]](#operator_at)|返回位于给定位置的字符-的运算符替换`GetAt`。|
|[CSimpleStringT::operator +=](#operator_add_eq)|将新字符串连接到现有字符串的末尾。|
|[CSimpleStringT::operator =](#operator_eq)|将新值分配给`CSimpleStringT`对象。|

### <a name="remarks"></a>备注

`CSimpleStringT`是视觉对象C++支持的各种字符串类的基类。 它为字符串对象的内存管理和基本缓冲区操作提供最低支持。 有关更高级的字符串对象，请参阅[CStringT 类](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="requirements"></a>要求

**标头：** atlsimpstr

## <a name="append"></a> CSimpleStringT::Append

将对象追加到现有`CSimpleStringT`对象。 `CSimpleStringT`

### <a name="syntax"></a>语法

```
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>参数

*strSrc*<br/>
要`CSimpleStringT`追加的对象。

*pszSrc*<br/>
一个指针，指向包含要追加的字符的字符串。

*nLength*<br/>
要追加的字符数。

### <a name="remarks"></a>备注

调用此方法可将现有`CSimpleStringT`对象追加到另一个`CSimpleStringT`对象。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::Append` 的用法。

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

##  <a name="appendchar"></a> CSimpleStringT::AppendChar

在现有`CSimpleStringT`对象后面追加一个字符。

### <a name="syntax"></a>语法

```
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>参数

*ch*<br/>
要追加的字符

### <a name="remarks"></a>备注

调用此函数可将指定的字符追加到现有`CSimpleStringT`对象的末尾。

##  <a name="copychars"></a> CSimpleStringT::CopyChars

将一个或多个字符复制`CSimpleStringT`到对象。

### <a name="syntax"></a>语法

```
static void CopyChars(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>参数

*pchDest*<br/>
指向字符串的指针。

*pchSrc*<br/>
指向字符串的指针，该字符串包含要复制的字符。

*nChars*<br/>
要复制的*pchSrc*字符数。

### <a name="remarks"></a>备注

调用此方法可将字符从*pchSrc*复制到*pchDest*字符串。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::CopyChars` 的用法。

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

##  <a name="copycharsoverlapped"></a>  CSimpleStringT::CopyCharsOverlapped

将一个或多个字符复制`CSimpleStringT`到对象。

### <a name="syntax"></a>语法

```
static void CopyCharsOverlapped(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>参数

*pchDest*<br/>
指向字符串的指针。

*pchSrc*<br/>
指向字符串的指针，该字符串包含要复制的字符。

*nChars*<br/>
要复制的*pchSrc*字符数。

### <a name="remarks"></a>备注

调用此方法可将字符从*pchSrc*复制到*pchDest*字符串。 与`CopyChars`不同`CopyCharsOverlapped` ，提供从可能重叠的字符缓冲区复制的安全方法。

### <a name="example"></a>示例

请参阅[CSimpleStringT：： CopyChars](#copychars)的示例或`CSimpleStringT::SetString` （位于 atlsimpstr 中）的源代码。

##  <a name="ctor"></a>  CSimpleStringT::CSimpleStringT

构造 `CSimpleStringT` 对象。

### <a name="syntax"></a>语法

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>参数

*strSrc*<br/>
要复制`CSimpleStringT`到此`CSimpleStringT`对象中的现有对象。

*pchSrc*<br/>
指向长度为*nLength*的字符数组的指针，不是以 null 结尾的。

*pszSrc*<br/>
要复制到此`CSimpleStringT`对象中的以 null 值结束的字符串。

*nLength*<br/>
中`pch`的字符数的计数。

*pStringMgr*<br/>
指向`CSimpleStringT`对象的内存管理器的指针。 有关的`IAtlStringMgr`和内存管理的`CSimpleStringT`详细信息，请参阅[内存管理和 CStringT](../memory-management-with-cstringt.md)。

### <a name="remarks"></a>备注

构造新`CSimpleStringT`的对象。 由于构造函数将输入数据复制到新分配的存储中，因此可能会导致内存异常。

### <a name="example"></a>示例

下面的示例演示如何`CSimpleStringT::CSimpleStringT`使用 ATL **typedef** `CSimpleString`。 `CSimpleString`是类模板`CSimpleStringT`的常用专用化。

```cpp
CSimpleString s1(pMgr);
// Empty string
CSimpleString s2(_T("cat"), pMgr);
// From a C string literal

CSimpleString s3(s2);
// Copy constructor
CSimpleString s4(s2 + _T(" ") + s3);

// From a string expression
CSimpleString s5(_T("xxxxxx"), 6, pMgr);
// s5 = "xxxxxx"
```

##  <a name="empty"></a>  CSimpleStringT::Empty

使此`CSimpleStringT`对象为空字符串，并根据需要释放内存。

### <a name="syntax"></a>语法

```
void Empty() throw();
```

### <a name="remarks"></a>备注

有关详细信息，请[参阅字符串：CString 异常清理](../cstring-exception-cleanup.md)。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::Empty` 的用法。

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="freeextra"></a>  CSimpleStringT::FreeExtra

释放先前由字符串分配但不再需要的任何额外内存。

### <a name="syntax"></a>语法

```
void FreeExtra();
```

### <a name="remarks"></a>备注

这应减少字符串对象占用的内存开销。 方法将缓冲区重新分配给[GetLength](#getlength)返回的准确长度。

### <a name="example"></a>示例

```cpp
CAtlString basestr;
IAtlStringMgr* pMgr;

pMgr= basestr.GetManager();
ASSERT(pMgr != NULL);

// Create a CSimpleString with 28 characters
CSimpleString str(_T("Many sports are fun to play."), 28, pMgr);
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// Assigning a smaller string won't cause CSimpleString to free its
// memory, because it assumes the string will grow again anyway.
str = _T("Soccer is best!");
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// This call forces CSimpleString to release the extra
// memory it doesn't need.
str.FreeExtra();
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());
```

### <a name="remarks"></a>备注

此示例的输出如下所示：

```Output
Alloc length is 1031, String length is 1024
Alloc length is 1031, String length is 15
Alloc length is 15, String length is 15
```

##  <a name="getalloclength"></a>  CSimpleStringT::GetAllocLength

检索`CSimpleStringT`对象的分配长度。

### <a name="syntax"></a>语法

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>返回值

为此对象分配的字符数。

### <a name="remarks"></a>备注

调用此方法以确定为此`CSimpleStringT`对象分配的字符数。 有关调用此函数的示例，请参阅[FreeExtra](#freeextra) 。

##  <a name="getat"></a>  CSimpleStringT::GetAt

从`CSimpleStringT`对象返回一个字符。

### <a name="syntax"></a>语法

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>参数

*iChar*<br/>
`CSimpleStringT`对象中字符的从零开始的索引。 *IChar*参数必须大于或等于0且小于[GetLength](#getlength)返回的值。 否则， `GetAt`将生成异常。

### <a name="return-value"></a>返回值

一个`XCHAR` ，它包含字符串中指定位置处的字符。

### <a name="remarks"></a>备注

调用此方法以返回由*iChar*指定的一个字符。 重载的下标（ **[]** ）运算符是的方便别名`GetAt`。 空终止符无需使用`GetAt`生成异常即可寻址。 但是，它不会计数`GetLength`，并且返回的值为0。

### <a name="example"></a>示例

下面的示例演示如何使用`CSimpleStringT::GetAt`。

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

##  <a name="getbuffer"></a>  CSimpleStringT::GetBuffer

返回指向`CSimpleStringT`对象的内部字符缓冲区的指针。

### <a name="syntax"></a>语法

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>参数

*nMinBufferLength*<br/>
字符缓冲区可以容纳的最小字符数。 此值不包括 null 终止符的空间。

如果*nMinBufferLength*大于当前缓冲区的长度， `GetBuffer`则会销毁当前缓冲区，并将其替换为所请求大小的缓冲区，并将对象引用计数重置为零。 如果以前在此缓冲区上调用了[LockBuffer](#lockbuffer) ，则会丢失缓冲区锁。

### <a name="return-value"></a>返回值

指向对象的（以 null 结尾的）字符缓冲区的指针。`PXSTR`

### <a name="remarks"></a>备注

调用此方法以返回`CSimpleStringT`对象的缓冲区内容。 返回`PXSTR`的不是常数，因此允许直接`CSimpleStringT`修改内容。

如果使用由`GetBuffer`返回的指针更改字符串内容，则必须先调用[ReleaseBuffer](#releasebuffer) ，然后才能使用任何其他`CSimpleStringT`成员方法。

调用后，返回`GetBuffer`的地址可能无效， `ReleaseBuffer`原因是`CSimpleStringT`其他`CSimpleStringT`操作可能会导致重新分配缓冲区。 如果不更改的长度`CSimpleStringT`，则不会重新分配缓冲区。

销毁`CSimpleStringT`对象时，会自动释放缓冲区内存。

如果自行跟踪字符串长度，则不应追加终止 null 字符。 但是，在用`ReleaseBuffer`释放缓冲区时，必须指定最终字符串长度。 如果追加了终止 null 字符，则应该为长度传递-1 （默认值）。 `ReleaseBuffer`然后确定缓冲区长度。

如果内存不足，无法满足`GetBuffer`请求，则此方法将引发 CMemoryException *。

### <a name="example"></a>示例

```cpp
CSimpleString s(_T("abcd"), pMgr);
LPTSTR pBuffer = s.GetBuffer(10);
int sizeOfBuffer = s.GetAllocLength();

// Directly access CSimpleString buffer
_tcscpy_s(pBuffer, sizeOfBuffer, _T("Hello"));
ASSERT(_tcscmp(s, _T("Hello")) == 0);
s.ReleaseBuffer();
```

##  <a name="getbuffersetlength"></a>  CSimpleStringT::GetBufferSetLength

返回一个指向`CSimpleStringT`对象的内部字符缓冲区的指针，如有必要准确匹配*nLength*中指定的长度，则截断或增大其长度。

### <a name="syntax"></a>语法

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>参数

*nLength*<br/>
字符缓冲区的准确大小`CSimpleStringT` （字符）。

### <a name="return-value"></a>返回值

指向`PXSTR`对象的（以 null 结尾的）字符缓冲区的指针。

### <a name="remarks"></a>备注

调用此方法以检索`CSimpleStringT`对象的内部缓冲区的指定长度。 返回`PXSTR`的指针不是**常量**，因此`CSimpleStringT`允许直接修改内容。

如果使用[GetBufferSetLength](#getbuffersetlength)返回的指针更改字符串内容，请`ReleaseBuffer` `CsimpleStringT`在使用任何其他`CSimpleStringT`方法之前调用来更新的内部状态。

调用后，返回`GetBufferSetLength`的地址可能无效， `ReleaseBuffer`原因是`CSimpleStringT`其他`CSimpleStringT`操作可能会导致重新分配缓冲区。 如果未更改的长度`CSimpleStringT`，则不会重新分配缓冲区。

销毁`CSimpleStringT`对象时，会自动释放缓冲区内存。

如果自行跟踪字符串长度，请不要追加终止 null 字符。 使用`ReleaseBuffer`释放缓冲区时，必须指定最终的字符串长度。 如果在调用`ReleaseBuffer`时追加了一个终止 null 字符，则将长度传递到`ReleaseBuffer`-1 （默认值） `strlen` ，并`ReleaseBuffer`将在缓冲区上执行以确定其长度。

有关引用计数的详细信息，请参阅以下文章：

- 通过 Windows SDK 中的[引用计数来管理对象生存期](/windows/win32/com/managing-object-lifetimes-through-reference-counting)。

- 在 Windows SDK 中[实现引用计数](/windows/win32/com/implementing-reference-counting)。

- [用于管理](/windows/win32/com/rules-for-managing-reference-counts)Windows SDK 中的引用计数的规则。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::GetBufferSetLength` 的用法。

```cpp
CSimpleString str(pMgr);
LPTSTR pstr = str.GetBufferSetLength(3);
pstr[0] = _T('C');
pstr[1] = _T('u');
pstr[2] = _T('p');

// No need for trailing zero or call to ReleaseBuffer()
// because GetBufferSetLength() set it for us.

str += _T(" soccer is best!");
ASSERT(_tcscmp(str, _T("Cup soccer is best!")) == 0);
```

##  <a name="getlength"></a>  CSimpleStringT::GetLength

返回`CSimpleStringT`对象中的字符数。

### <a name="syntax"></a>语法

```
int GetLength() const throw();
```

### <a name="return-value"></a>返回值

字符串中的字符数。

### <a name="remarks"></a>备注

调用此方法以返回对象中的字符数。 此计数不包括 null 终止符。

对于多字节字符集（MBCS）， `GetLength`会对每个8位字符进行计数，即一个多字节字符的前导字节和结尾字节计为两个字节。 有关调用此函数的示例，请参阅[FreeExtra](#freeextra) 。

##  <a name="getmanager"></a>  CSimpleStringT::GetManager

检索`CSimpleStringT`对象的内存管理器。

### <a name="syntax"></a>语法

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>返回值

指向`CSimpleStringT`对象的内存管理器的指针。

### <a name="remarks"></a>备注

调用此方法以检索`CSimpleStringT`对象使用的内存管理器。 有关内存管理器和字符串对象的详细信息，请参阅[内存管理和 CStringT](../memory-management-with-cstringt.md)。

##  <a name="getstring"></a>  CSimpleStringT::GetString

检索字符串。

### <a name="syntax"></a>语法

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>返回值

指向以 null 结尾的字符串的指针。

### <a name="remarks"></a>备注

调用此方法可检索与`CSimpleStringT`对象关联的字符串。

> [!NOTE]
>  返回`PCXSTR`的指针为**const** ，不`CSimpleStringT`允许直接修改内容。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::GetString` 的用法。

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

##  <a name="isempty"></a>  CSimpleStringT::IsEmpty

为空条件测试对象。`CSimpleStringT`

### <a name="syntax"></a>语法

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>返回值

如果对象的`CSimpleStringT`长度为零，则返回 TRUE; 否则返回 FALSE。

### <a name="remarks"></a>备注

调用此方法以确定对象是否包含空字符串。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::IsEmpty` 的用法。

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="lockbuffer"></a>  CSimpleStringT::LockBuffer

禁用引用计数并保护缓冲区中的字符串。

### <a name="syntax"></a>语法

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>返回值

指向`CSimpleStringT`对象或以 null 结尾的字符串的指针。

### <a name="remarks"></a>备注

调用此方法可锁定`CSimpleStringT`对象的缓冲区。 通过调用`LockBuffer`，可创建字符串的副本，引用计数为-1。 当引用计数值为-1 时，缓冲区中的字符串被视为处于 "锁定" 状态。 处于锁定状态时，将通过两种方式保护字符串：

- 任何其他字符串都不能获取对锁定的字符串中数据的引用，即使该字符串已被分配到锁定的字符串也是如此。

- 锁定的字符串将从不引用另一个字符串，即使将其他字符串复制到锁定的字符串也是如此。

通过锁定缓冲区中的字符串，可以确保字符串在缓冲区上的独占保留保持不变。

完成`LockBuffer`后，调用[UnlockBuffer](#unlockbuffer)将引用计数重置为1。

> [!NOTE]
>  如果对锁定的缓冲区调用[GetBuffer](#getbuffer) ，并将`GetBuffer`参数`nMinBufferLength`设置为大于当前缓冲区的长度，则会丢失缓冲区锁。 此类调用`GetBuffer`会销毁当前缓冲区，并将其替换为所请求大小的缓冲区，并将引用计数重置为零。

有关引用计数的详细信息，请参阅以下文章：

- 通过 Windows SDK 中的[引用计数来管理对象生存期](/windows/win32/com/managing-object-lifetimes-through-reference-counting)

- 在 Windows SDK 中[实现引用计数](/windows/win32/com/implementing-reference-counting)

- [用于管理](/windows/win32/com/rules-for-managing-reference-counts)Windows SDK 中的引用计数的规则

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::LockBuffer` 的用法。

```cpp
CSimpleString str(_T("Hello"), pMgr);
TCHAR ch;

str.LockBuffer();
ch = str.GetAt(2);
_tprintf_s(_T("%c"), ch);
str.UnlockBuffer();
```

##  <a name="operator_at"></a>  CSimpleStringT::operator\[\]

调用此函数可访问字符数组中的单个字符。

### <a name="syntax"></a>语法

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>参数

*iChar*<br/>
字符串中的字符从零开始的索引。

### <a name="remarks"></a>备注

重载的下标（ **[]** ）运算符返回*iChar*中从零开始的索引指定的单个字符。 此运算符是[GetAt](#getat)成员函数的便利替代品。

> [!NOTE]
>  可以使用下标（ **[]** ）运算符来获取中`CSimpleStringT`字符的值，但不能使用它来更改中`CSimpleStringT`字符的值。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::operator []` 的用法。

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="operator_at"></a>  CSimpleStringT::operator \[\]

调用此函数可访问字符数组中的单个字符。

### <a name="syntax"></a>语法

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>参数

*iChar*<br/>
字符串中的字符从零开始的索引。

### <a name="remarks"></a>备注

重载的下标（ **[]** ）运算符返回*iChar*中从零开始的索引指定的单个字符。 此运算符是[GetAt](#getat)成员函数的便利替代品。

> [!NOTE]
>  可以使用下标（ **[]** ）运算符来获取中`CSimpleStringT`字符的值，但不能使用它来更改中`CSimpleStringT`字符的值。

##  <a name="operator_add_eq"></a>CSimpleStringT：： operator + =

将新字符串或字符加入现有字符串的末尾。

### <a name="syntax"></a>语法

```
CSimpleStringT& operator +=(PCXSTR pszSrc);
CSimpleStringT& operator +=(const CSimpleStringT& strSrc);
template<int t_nSize>
CSimpleStringT& operator+=(const CStaticString< XCHAR, t_nSize >& strSrc);
CSimpleStringT& operator +=(char ch);
CSimpleStringT& operator +=(unsigned char ch);
CSimpleStringT& operator +=(wchar_t ch);
```

#### <a name="parameters"></a>参数

*pszSrc*<br/>
指向以 null 结尾的字符串的指针。

*strSrc*<br/>
指向现有`CSimpleStringT`对象的指针。

*ch*<br/>
要追加的字符。

### <a name="remarks"></a>备注

运算符接受另一个`CSimpleStringT`对象或一个字符。 请注意，只要使用此串联运算符，就可能会发生内存异常，因为可以为添加到此`CSimpleStringT`对象的字符分配新存储。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::operator +=` 的用法。

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

##  <a name="operator_eq"></a>  CSimpleStringT::operator =

将新值分配给`CSimpleStringT`对象。

### <a name="syntax"></a>语法

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>参数

*pszSrc*<br/>
指向以 null 结尾的字符串的指针。

*strSrc*<br/>
指向现有`CSimpleStringT`对象的指针。

### <a name="remarks"></a>备注

如果目标字符串（左侧）已经足够大，无法存储新数据，则不会执行任何新的内存分配。 请注意，只要你使用赋值运算符，就可能会发生内存异常，因为通常会分配新存储`CSimpleStringT`来保存生成的对象。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::operator =` 的用法。

```cpp
CSimpleString s1(pMgr), s2(pMgr);
// Empty CSimpleStringT objects

s1 = _T("cat");
// s1 = "cat"
ASSERT(_tcscmp(s1, _T("cat")) == 0);

s2 = s1;               // s1 and s2 each = "cat"
ASSERT(_tcscmp(s2, _T("cat")) == 0);

s1 = _T("the ") + s1;
// Or expressions
ASSERT(_tcscmp(s1, _T("the cat")) == 0);

s1 = _T("x");
// Or just individual characters
ASSERT(_tcscmp(s1, _T("x")) == 0);
```

##  <a name="operator_pcxstr"></a>  CSimpleStringT::operator PCXSTR

直接访问存储在`CSimpleStringT`对象中的字符作为 C 样式字符串。

### <a name="syntax"></a>语法

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>返回值

指向字符串数据的字符指针。

### <a name="remarks"></a>备注

不复制任何字符;仅返回指针。 请小心处理此运算符。 如果在获取字符`CString`指针之后更改对象，则可能会导致重新分配使指针失效的内存。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::operator PCXSTR` 的用法。

```cpp
// If the prototype of a function is known to the compiler,
// the PCXSTR cast operator may be invoked implicitly.

CSimpleString strSports(L"Soccer is Best!", pMgr);
WCHAR sz[1024];

wcscpy_s(sz, strSports);

// If the prototype isn't known or is a va_arg prototype,
// you must invoke the cast operator explicitly. For example,
// the va_arg part of a call to swprintf_s() needs the cast:

swprintf_s(sz, 1024, L"I think that %s!\n", (PCWSTR)strSports);

// While the format parameter is known to be an PCXSTR and
// therefore doesn't need the cast:

swprintf_s(sz, 1024, strSports);

// Note that some situations are ambiguous. This line will
// put the address of the strSports object to stdout:

wcout << strSports;

// while this line will put the content of the string out:

wcout << (PCWSTR)strSports;
```

##  <a name="pcxstr"></a>  CSimpleStringT::PCXSTR

指向常量字符串的指针。

### <a name="syntax"></a>语法

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

##  <a name="preallocate"></a>  CSimpleStringT::Preallocate

为`CSimpleStringT`对象分配特定字节量。

### <a name="syntax"></a>语法

```
void Preallocate( int nLength);
```

#### <a name="parameters"></a>参数

*nLength*<br/>
字符缓冲区的准确大小`CSimpleStringT` （字符）。

### <a name="remarks"></a>备注

调用此方法以分配`CSimpleStringT`对象的特定缓冲区大小。

`CSimpleStringT`如果无法为字符缓冲区分配空间，则生成 STATUS_NO_MEMORY 异常。 默认情况下，内存分配由 WIN32 API 函数`HeapAlloc`或`HeapReAlloc`执行。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::Preallocate` 的用法。

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

##  <a name="pxstr"></a>  CSimpleStringT::PXSTR

指向字符串的指针。

### <a name="syntax"></a>语法

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

##  <a name="releasebuffer"></a>  CSimpleStringT::ReleaseBuffer

释放由[GetBuffer](#getbuffer)分配的缓冲区的控制。

### <a name="syntax"></a>语法

```
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>参数

*nNewLength*<br/>
字符串的新长度（以字符计），不包括 null 终止符。 如果字符串为 null，则默认值为-1，则将`CSimpleStringT`大小设置为字符串的当前长度。

### <a name="remarks"></a>备注

调用此方法可重新分配或释放字符串对象的缓冲区。 如果知道缓冲区中的字符串已终止 null，则可以省略*nNewLength*参数。 如果字符串未以 null 终止，请使用*nNewLength*指定其长度。 调用`ReleaseBuffer`或任何其他`CSimpleStringT`操作后，[GetBuffer](#getbuffer) 返回的地址无效。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::ReleaseBuffer` 的用法。

```cpp
const int bufferSize = 1024;
CSimpleString s(_T("abc"), pMgr);
LPTSTR p = s.GetBuffer(bufferSize);
_tcscpy_s(p, bufferSize, _T("abc"));

// use the buffer directly
ASSERT(s.GetLength() == 3);

// String length = 3
s.ReleaseBuffer();

// Surplus memory released, p is now invalid.
ASSERT(s.GetLength() == 3);

// Length still 3
```

##  <a name="releasebuffersetlength"></a>  CSimpleStringT::ReleaseBufferSetLength

释放由[GetBuffer](#getbuffer)分配的缓冲区的控制。

### <a name="syntax"></a>语法

```
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>参数

*nNewLength*<br/>
要释放的字符串的长度

### <a name="remarks"></a>备注

此函数在功能上类似于[ReleaseBuffer](#releasebuffer) ，只不过必须传递字符串对象的有效长度。

##  <a name="setat"></a>  CSimpleStringT::SetAt

设置`CSimpleStringT`对象中的单个字符。

### <a name="syntax"></a>语法

```
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>参数

*iChar*<br/>
`CSimpleStringT`对象中字符的从零开始的索引。 *IChar*参数必须大于或等于0且小于[GetLength](#getlength)返回的值。

*ch*<br/>
新字符。

### <a name="remarks"></a>备注

调用此方法可覆盖位于*iChar*的字符。 如果*iChar*超出了现有字符串的界限，则此方法将不会扩大字符串。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::SetAt` 的用法。

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

##  <a name="setmanager"></a>  CSimpleStringT::SetManager

指定`CSimpleStringT`对象的内存管理器。

### <a name="syntax"></a>语法

```
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>参数

*pStringMgr*<br/>
指向新内存管理器的指针。

### <a name="remarks"></a>备注

调用此方法以指定`CSimpleStringT`对象使用的新内存管理器。 有关内存管理器和字符串对象的详细信息，请参阅[内存管理和 CStringT](../memory-management-with-cstringt.md)。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::SetManager` 的用法。

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

##  <a name="setstring"></a>  CSimpleStringT::SetString

设置`CSimpleStringT`对象的字符串。

### <a name="syntax"></a>语法

```
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>参数

*pszSrc*<br/>
指向以 null 结尾的字符串的指针。

*nLength*<br/>
*PszSrc*中的字符数计数。

### <a name="remarks"></a>备注

将字符串复制到`CSimpleStringT`对象中。 `SetString`覆盖缓冲区中较旧的字符串数据。

这两个`SetString`版本均检查*pszSrc*是否为 null 指针，如果为 null，则引发 E_INVALIDARG 错误。

`SetString`需要*pszSrc*的单参数版本，以指向以 null 结尾的字符串。

的`SetString`双参数版本也需要*pszSrc*为以 null 结尾的字符串。 它使用*nLength*作为字符串长度，除非首先遇到空终止符。

的`SetString`双参数版本还会检查*pszSrc*是否指向中`CSimpleStringT`的当前缓冲区中的位置。 在这种特殊情况`SetString`下，使用不会覆盖字符串数据的内存复制函数，因为它将字符串数据复制回其缓冲区。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::SetString` 的用法。

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

##  <a name="stringlength"></a>  CSimpleStringT::StringLength

返回指定字符串中的字符数。

### <a name="syntax"></a>语法

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>参数

*psz*<br/>
指向以 null 结尾的字符串的指针。

### <a name="return-value"></a>返回值

*Psz*中的字符数;不计算 null 终止符。

### <a name="remarks"></a>备注

调用此方法可检索*psz*所指向的字符串中的字符数。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::StringLength` 的用法。

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

##  <a name="truncate"></a>  CSimpleStringT::Truncate

将字符串截断为新长度。

### <a name="syntax"></a>语法

```
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>参数

*nNewLength*<br/>
字符串的新长度。

### <a name="remarks"></a>备注

调用此方法可将字符串的内容截断为新长度。

> [!NOTE]
>  这不会影响分配的缓冲区长度。 若要减小或增加当前缓冲区，请参阅 [FreeExtra](#freeextra)和[预分配](#preallocate)。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::Truncate` 的用法。

```cpp
CSimpleString str(_T("abcdefghi"), pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
str.Truncate(4);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
```

##  <a name="unlockbuffer"></a>  CSimpleStringT::UnlockBuffer

解除锁定`CSimpleStringT`对象的缓冲区。

### <a name="syntax"></a>语法

```
void UnlockBuffer() throw();
```

### <a name="remarks"></a>备注

调用此方法可将字符串的引用计数重置为1。

析构函数将自动`UnlockBuffer`调用以确保调用析构函数时缓冲区不会被锁定。 `CSimpleStringT` 有关此方法的示例，请参阅[LockBuffer](#lockbuffer)。

##  <a name="dtor"></a>CSimpleStringT：： ~ CSimpleStringT

销毁 `CSimpleStringT` 对象。

### <a name="syntax"></a>语法

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>备注

调用此方法以销毁`CSimpleStringT`对象。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
