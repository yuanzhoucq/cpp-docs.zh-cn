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
ms.openlocfilehash: 76d418c4f063d5787209ea72e7c681013eb37801
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747031"
---
# <a name="csimplestringt-class"></a>CSimpleStringT 类

此类表示对象`CSimpleStringT`。

## <a name="syntax"></a>语法

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>参数

*BaseType*<br/>
字符串类的字符类型。 可以是以下值之一：

- **字符**（用于 ANSI 字符串）。

- **wchar_t（** 对于 Unicode 字符串）。

- TCHAR（适用于 ANSI 和 Unicode 字符串）。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[CSimpleStringT：:PCXSTR](#pcxstr)|指向常量字符串的指针。|
|[简单StringT：:PXSTR](#pxstr)|指向字符串的指针。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[简单StringT：：简单StringT](#ctor)|以各种方式构造`CSimpleStringT`对象。|
|[简单StringT：_CSimpleStringT](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSimpleStringT：：附加](#append)|将`CSimpleStringT`对象追加到现有`CSimpleStringT`对象。|
|[CSimpleStringT：：附录查尔](#appendchar)|将字符追加到现有`CSimpleStringT`对象。|
|[CSimpleStringT：：复制字符](#copychars)|将字符或字符复制到另一个字符串。|
|[CSimpleStringT：：复制字符重叠](#copycharsoverlapped)|将字符或字符复制到缓冲区重叠的另一个字符串。|
|[简单StringT：空](#empty)|强制字符串的长度为零。|
|[CSimpleStringT：：免费额外](#freeextra)|释放以前由字符串对象分配的任何额外内存。|
|[简单StringT：获取 Alloc 长度](#getalloclength)|检索`CSimpleStringT`对象的分配长度。|
|[简单Stringt：getat](#getat)|返回给定位置的字符。|
|[简单StringT：获取缓冲区](#getbuffer)|返回指向 中的字符的`CSimpleStringT`指针。|
|[CSimpleStringT：获取缓冲区集长度](#getbuffersetlength)|返回指向`CSimpleStringT`的指针，该指针将截断到指定长度。|
|[简单StringT：获取长度](#getlength)|返回`CSimpleStringT`对象中的字符数。|
|[CSimpleStringT：获取管理器](#getmanager)|检索`CSimpleStringT`对象的内存管理器。|
|[简单StringT：获取String](#getstring)|检索字符串|
|[简单StringT：：是空的](#isempty)|测试`CSimpleStringT`对象是否不包含字符。|
|[简单StringT：锁缓冲区](#lockbuffer)|禁用引用计数并保护缓冲区中的字符串。|
|[CSimpleStringT：:P重新分配](#preallocate)|为字符缓冲区分配特定数量的内存。|
|[CSimpleStringT：：释放缓冲区](#releasebuffer)|释放对 返回的`GetBuffer`缓冲区的控制。|
|[CSimpleStringT：：释放缓冲区集长度](#releasebuffersetlength)|释放对 返回的`GetBuffer`缓冲区的控制。|
|[简单Stringt：：Setat](#setat)|在给定位置设置字符。|
|[简单StringT：setManager](#setmanager)|设置`CSimpleStringT`对象的内存管理器。|
|[简单StringT：：设置String](#setstring)|设置`CSimpleStringT`对象的字符串。|
|[简单StringT：字符串长度](#stringlength)|返回指定字符串中的字符数。|
|[CSimpleStringT：：截流](#truncate)|将字符串截排到指定长度。|
|[CSimpleStringT：：解锁缓冲区](#unlockbuffer)|启用引用计数并释放缓冲区中的字符串。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[简单StringT：：操作员 PCXSTR](#operator_pcxstr)|直接访问作为 C 样式`CSimpleStringT`字符串存储在对象中的字符。|
|[CSimpleStringT::operator\[\]](#operator_at)|返回给定位置的字符 = 运算符替换`GetAt`。|
|[CSimpleStringT：：运算符 |](#operator_add_eq)|将新字符串串联到现有字符串的末尾。|
|[CSimpleStringT：：运算符 |](#operator_eq)|为`CSimpleStringT`对象分配新值。|

### <a name="remarks"></a>备注

`CSimpleStringT`是 Visual C++ 支持的各种字符串类的基类。 它为字符串对象的内存管理和基本缓冲区操作提供了最少的支持。 有关更高级的字符串对象，请参阅[CStringt 类](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="requirements"></a>要求

**标题：** atlsimpstr.h

## <a name="csimplestringtappend"></a><a name="append"></a>CSimpleStringT：：附加

将`CSimpleStringT`对象追加到现有`CSimpleStringT`对象。

### <a name="syntax"></a>语法

```cpp
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>参数

*斯特斯尔克*<br/>
要`CSimpleStringT`追加的对象。

*皮茨斯尔克*<br/>
指向包含要追加的字符的字符串的指针。

*n 长度*<br/>
要追加的字符数。

### <a name="remarks"></a>备注

调用此方法将现有`CSimpleStringT`对象追加到另一个`CSimpleStringT`对象。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::Append` 的用法。

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

## <a name="csimplestringtappendchar"></a><a name="appendchar"></a>CSimpleStringT：：附录查尔

将字符追加到现有`CSimpleStringT`对象。

### <a name="syntax"></a>语法

```cpp
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>参数

*ch*<br/>
要追加的字符

### <a name="remarks"></a>备注

调用此函数以将指定的字符追加到现有`CSimpleStringT`对象的末尾。

## <a name="csimplestringtcopychars"></a><a name="copychars"></a>CSimpleStringT：：复制字符

将字符或字符复制到`CSimpleStringT`对象。

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

*普施斯克*<br/>
指向包含要复制的字符的字符串的指针。

*n查尔斯*<br/>
要复制的*pchSrc*字符数。

### <a name="remarks"></a>备注

调用此方法以将字符从*pchSrc*复制到*pchDest*字符串。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::CopyChars` 的用法。

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

## <a name="csimplestringtcopycharsoverlapped"></a><a name="copycharsoverlapped"></a>CSimpleStringT：：复制字符重叠

将字符或字符复制到`CSimpleStringT`对象。

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

*普施斯克*<br/>
指向包含要复制的字符的字符串的指针。

*n查尔斯*<br/>
要复制的*pchSrc*字符数。

### <a name="remarks"></a>备注

调用此方法以将字符从*pchSrc*复制到*pchDest*字符串。 与`CopyChars``CopyCharsOverlapped`不同，提供了一种安全的方法，用于从可能重叠的字符缓冲区复制。

### <a name="example"></a>示例

请参阅[CSimpleStringT：：复制字符](#copychars)的示例，或 （`CSimpleStringT::SetString`位于 atlsimpstr.h） 的源代码。

## <a name="csimplestringtcsimplestringt"></a><a name="ctor"></a>简单StringT：：简单StringT

构造 `CSimpleStringT` 对象。

### <a name="syntax"></a>语法

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>参数

*斯特斯尔克*<br/>
要复制到`CSimpleStringT`此`CSimpleStringT`对象的现有对象。

*普施斯克*<br/>
指向长度*nLength*的字符数组的指针，而不是 null 终止。

*皮茨斯尔克*<br/>
要复制到此`CSimpleStringT`对象的 null 终止字符串。

*n 长度*<br/>
中字符数的计数`pch`。

*普斯特林姆格*<br/>
指向对象的内存管理器的`CSimpleStringT`指针。 有关 的详细信息`IAtlStringMgr`和内存管理`CSimpleStringT`，请参阅[内存管理和 CStringT](../memory-management-with-cstringt.md)。

### <a name="remarks"></a>备注

构造新`CSimpleStringT`对象。 由于构造函数将输入数据复制到新的分配存储中，因此可能会导致内存异常。

### <a name="example"></a>示例

下面的示例演示了使用 ATL`CSimpleStringT::CSimpleStringT`**类型def**`CSimpleString`的 。 `CSimpleString`是类模板`CSimpleStringT`的常用专门化。

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

## <a name="csimplestringtempty"></a><a name="empty"></a>简单StringT：空

使此`CSimpleStringT`对象成为空字符串，并根据需要释放内存。

### <a name="syntax"></a>语法

```cpp
void Empty() throw();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[字符串：CString 异常清理](../cstring-exception-cleanup.md)。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::Empty` 的用法。

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtfreeextra"></a><a name="freeextra"></a>CSimpleStringT：：免费额外

释放以前由字符串分配但不再需要的任何额外内存。

### <a name="syntax"></a>语法

```cpp
void FreeExtra();
```

### <a name="remarks"></a>备注

这将减少字符串对象消耗的内存开销。 该方法将缓冲区重新分配到[GetLength](#getlength)返回的确切长度。

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

## <a name="csimplestringtgetalloclength"></a><a name="getalloclength"></a>简单StringT：获取 Alloc 长度

检索`CSimpleStringT`对象的分配长度。

### <a name="syntax"></a>语法

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>返回值

为此对象分配的字符数。

### <a name="remarks"></a>备注

调用此方法以确定为此`CSimpleStringT`对象分配的字符数。 有关调用此函数的示例，请参阅[FreeExtra。](#freeextra)

## <a name="csimplestringtgetat"></a><a name="getat"></a>简单Stringt：getat

从对象返回一个字符`CSimpleStringT`。

### <a name="syntax"></a>语法

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>参数

*i查尔*<br/>
`CSimpleStringT`对象中字符的零基索引。 *iChar*参数必须大于或等于 0，小于[GetLength](#getlength)返回的值。 否则，`GetAt`将生成异常。

### <a name="return-value"></a>返回值

包含`XCHAR`字符串中指定位置的字符的 。

### <a name="remarks"></a>备注

调用此方法返回*iChar*指定的一个字符。 重载子标 （*****） 运算符是 的`GetAt`方便别名。 空终止符是可寻址的，无需使用`GetAt`生成异常。 但是，它不按`GetLength`计数，返回的值为 0。

### <a name="example"></a>示例

下面的示例演示如何使用`CSimpleStringT::GetAt`。

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

## <a name="csimplestringtgetbuffer"></a><a name="getbuffer"></a>简单StringT：获取缓冲区

返回指向对象的内部字符缓冲区的`CSimpleStringT`指针。

### <a name="syntax"></a>语法

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>参数

*n 最小缓冲区长度*<br/>
字符缓冲区可以容纳的最小字符数。 此值不包括空终止符的空间。

如果*nMinBufferLength 大于*当前缓冲区的长度，则`GetBuffer`销毁当前缓冲区，将其替换为请求大小的缓冲区，并将对象引用计数重置为零。 如果以前在此缓冲区上调用[LockBuffer，](#lockbuffer)则丢失缓冲区锁。

### <a name="return-value"></a>返回值

指向`PXSTR`对象的（空终止）字符缓冲区的指针。

### <a name="remarks"></a>备注

调用此方法以返回`CSimpleStringT`对象的缓冲区内容。 返回`PXSTR`的不是常量，因此允许直接修改`CSimpleStringT`内容。

如果使用返回`GetBuffer`的指针更改字符串内容，则必须在使用任何其他`CSimpleStringT`成员方法之前调用[ReleaseBuffer。](#releasebuffer)

返回`GetBuffer`的地址在调用后可能无效，`ReleaseBuffer`因为其他`CSimpleStringT`操作可能导致`CSimpleStringT`缓冲区被重新分配。 如果不更改 的长度`CSimpleStringT`，则不会重新分配缓冲区。

销毁对象时，`CSimpleStringT`将自动释放缓冲区内存。

如果自己跟踪字符串长度，则不应追加终止空字符。 但是，在释放使用`ReleaseBuffer`的缓冲区时，必须指定最终字符串长度。 如果确实追加了终止空字符，则应为长度传递 -1（默认值）。 `ReleaseBuffer`然后确定缓冲区长度。

如果内存不足以满足`GetBuffer`请求，此方法将引发 CMemoryException*。

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

## <a name="csimplestringtgetbuffersetlength"></a><a name="getbuffersetlength"></a>CSimpleStringT：获取缓冲区集长度

返回指向对象内部字符缓冲区的`CSimpleStringT`指针，如果需要，将截断或增加其长度以完全匹配*nLength*中指定的长度。

### <a name="syntax"></a>语法

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>参数

*n 长度*<br/>
字符缓冲区的确切`CSimpleStringT`大小（以字符表示）。

### <a name="return-value"></a>返回值

指向`PXSTR`对象的（空终止）字符缓冲区的指针。

### <a name="remarks"></a>备注

调用此方法以检索`CSimpleStringT`对象内部缓冲区的指定长度。 返回`PXSTR`的指针不**协调**，因此允许直接修改`CSimpleStringT`内容。

如果使用[GetBufferSetLength 返回](#getbuffersetlength)的指针更改字符串内容，请调用`ReleaseBuffer`以在使用任何其他`CsimpleStringT``CSimpleStringT`方法之前更新 的内部状态。

返回`GetBufferSetLength`的地址在调用后可能无效，`ReleaseBuffer`因为其他`CSimpleStringT`操作可能导致`CSimpleStringT`缓冲区被重新分配。 如果不更改 的长度`CSimpleStringT`，则不重新分配缓冲区。

销毁对象时，`CSimpleStringT`将自动释放缓冲区内存。

如果自己跟踪字符串长度，请不要追加终止空字符。 使用 释放缓冲区时，必须指定最终字符串长度`ReleaseBuffer`。 如果在调用`ReleaseBuffer`时追加了终止空字符 ，则将长度传递给`ReleaseBuffer`-1（默认值），并将`ReleaseBuffer`对 缓冲区执行 以确定`strlen`其长度。

有关引用计数的详细信息，请参阅以下文章：

- 通过 Windows SDK 中的[引用计数管理对象生存期](/windows/win32/com/managing-object-lifetimes-through-reference-counting)。

- 在 Windows SDK 中[实现引用计数](/windows/win32/com/implementing-reference-counting)。

- 用于在 Windows SDK 中[管理引用计数的规则](/windows/win32/com/rules-for-managing-reference-counts)。

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

## <a name="csimplestringtgetlength"></a><a name="getlength"></a>简单StringT：获取长度

返回对象中的`CSimpleStringT`字符数。

### <a name="syntax"></a>语法

```
int GetLength() const throw();
```

### <a name="return-value"></a>返回值

字符串中字符的计数。

### <a name="remarks"></a>备注

调用此方法以返回对象中的字符数。 计数不包括空终止符。

对于多字节字符集 （MBCS），`GetLength`计算每个 8 位字符;也就是说，一个多字节字符中的引线和跟踪字节计为两个字节。 有关调用此函数的示例，请参阅[FreeExtra。](#freeextra)

## <a name="csimplestringtgetmanager"></a><a name="getmanager"></a>CSimpleStringT：获取管理器

检索`CSimpleStringT`对象的内存管理器。

### <a name="syntax"></a>语法

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>返回值

指向对象的内存管理器的`CSimpleStringT`指针。

### <a name="remarks"></a>备注

调用此方法以检索`CSimpleStringT`对象使用的内存管理器。 有关内存管理器和字符串对象的详细信息，请参阅[内存管理和 CStringT](../memory-management-with-cstringt.md)。

## <a name="csimplestringtgetstring"></a><a name="getstring"></a>简单StringT：获取String

检索字符串。

### <a name="syntax"></a>语法

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>返回值

指向 null 终止字符串的指针。

### <a name="remarks"></a>备注

调用此方法以检索与`CSimpleStringT`对象关联的字符串。

> [!NOTE]
> 返回`PCXSTR`的指针**是 const，** 不允许直接修改`CSimpleStringT`内容。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::GetString` 的用法。

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

## <a name="csimplestringtisempty"></a><a name="isempty"></a>简单StringT：：是空的

测试`CSimpleStringT`空条件的对象。

### <a name="syntax"></a>语法

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>返回值

如果对象长度为`CSimpleStringT`0，则返回 TRUE;如果对象长度为 0，则返回 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

调用此方法以确定对象是否包含空字符串。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::IsEmpty` 的用法。

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtlockbuffer"></a><a name="lockbuffer"></a>简单StringT：锁缓冲区

禁用引用计数并保护缓冲区中的字符串。

### <a name="syntax"></a>语法

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>返回值

指向`CSimpleStringT`对象的指针或 null 终止的字符串。

### <a name="remarks"></a>备注

调用此方法以锁定`CSimpleStringT`对象的缓冲区。 通过调用`LockBuffer`，可以创建字符串的副本，该副本为 -1 表示引用计数。 当引用计数值为 -1 时，缓冲区中的字符串被视为处于"锁定"状态。 处于锁定状态时，字符串通过两种方式受到保护：

- 任何其他字符串都无法获取对锁定字符串中数据的引用，即使该字符串已分配给锁定的字符串也是如此。

- 锁定的字符串永远不会引用另一个字符串，即使该其他字符串复制到锁定的字符串。

通过在缓冲区中锁定字符串，可确保字符串对缓冲区的独占保留将保持不变。

完成`LockBuffer`后，调用[UnlockBuffer](#unlockbuffer)将引用计数重置为 1。

> [!NOTE]
> 如果在锁定的缓冲区上调用[GetBuffer，](#getbuffer)`GetBuffer`并将参数`nMinBufferLength`设置为大于当前缓冲区的长度，则将丢失缓冲区锁。 这种调用会破坏`GetBuffer`当前缓冲区，将其替换为请求大小的缓冲区，并将引用计数重置为零。

有关引用计数的详细信息，请参阅以下文章：

- 通过 Windows SDK 中的[引用计数管理对象生存期](/windows/win32/com/managing-object-lifetimes-through-reference-counting)

- 在 Windows SDK 中[实现引用计数](/windows/win32/com/implementing-reference-counting)

- 用于在 Windows SDK 中[管理参考计数的规则](/windows/win32/com/rules-for-managing-reference-counts)

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

## <a name="csimplestringtoperator"></a><a name="operator_at"></a>CSimpleStringT：：运算符\[\]

调用此函数以访问字符数组的单个字符。

### <a name="syntax"></a>语法

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>参数

*i查尔*<br/>
字符串中字符的零基索引。

### <a name="remarks"></a>备注

重载子标 （*****） 运算符返回*iChar*中的零基索引指定的单个字符。 此运算符是[GetAt](#getat)成员函数的便捷替代。

> [!NOTE]
> 可以使用下标 （*****） 运算符获取 中的字符的值`CSimpleStringT`，但不能使用它来更改 中`CSimpleStringT`字符的值。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::operator []` 的用法。

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="csimplestringtoperator-"></a><a name="operator_at"></a>CSimpleStringT：：运算符\[\]

调用此函数以访问字符数组的单个字符。

### <a name="syntax"></a>语法

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>参数

*i查尔*<br/>
字符串中字符的零基索引。

### <a name="remarks"></a>备注

重载子标 （*****） 运算符返回*iChar*中的零基索引指定的单个字符。 此运算符是[GetAt](#getat)成员函数的便捷替代。

> [!NOTE]
> 可以使用下标 （*****） 运算符获取 中的字符的值`CSimpleStringT`，但不能使用它来更改 中`CSimpleStringT`字符的值。

## <a name="csimplestringtoperator-"></a><a name="operator_add_eq"></a>CSimpleStringT：：运算符 |

将新字符串或字符联接到现有字符串的末尾。

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

*皮茨斯尔克*<br/>
指向 null 终止字符串的指针。

*斯特斯尔克*<br/>
指向现有`CSimpleStringT`对象的指针。

*ch*<br/>
要追加的字符。

### <a name="remarks"></a>备注

运算符接受另一`CSimpleStringT`个对象或字符。 请注意，每当使用此串联运算符时，都可能发生内存异常，因为可能会为添加到此`CSimpleStringT`对象的字符分配新存储。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::operator +=` 的用法。

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

## <a name="csimplestringtoperator-"></a><a name="operator_eq"></a>CSimpleStringT：：运算符 |

为`CSimpleStringT`对象分配新值。

### <a name="syntax"></a>语法

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>参数

*皮茨斯尔克*<br/>
指向 null 终止字符串的指针。

*斯特斯尔克*<br/>
指向现有`CSimpleStringT`对象的指针。

### <a name="remarks"></a>备注

如果目标字符串（左侧）已足够大以存储新数据，则不执行新的内存分配。 请注意，每当使用赋值运算符时，都可能发生内存异常，因为通常分配新存储来保存生成的`CSimpleStringT`对象。

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

## <a name="csimplestringtoperator-pcxstr"></a><a name="operator_pcxstr"></a>简单StringT：：操作员 PCXSTR

直接访问作为 C 样式`CSimpleStringT`字符串存储在对象中的字符。

### <a name="syntax"></a>语法

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>返回值

指向字符串数据的字符指针。

### <a name="remarks"></a>备注

不复制任何字符;仅返回指针。 小心此运算符。 如果在获取字符指针`CString`后更改对象，则可能导致重新分配内存，使指针无效。

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

## <a name="csimplestringtpcxstr"></a><a name="pcxstr"></a>CSimpleStringT：:PCXSTR

指向常量字符串的指针。

### <a name="syntax"></a>语法

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

## <a name="csimplestringtpreallocate"></a><a name="preallocate"></a>CSimpleStringT：:P重新分配

为`CSimpleStringT`对象分配特定数量的字节。

### <a name="syntax"></a>语法

```cpp
void Preallocate( int nLength);
```

#### <a name="parameters"></a>参数

*n 长度*<br/>
字符缓冲区的确切`CSimpleStringT`大小（以字符表示）。

### <a name="remarks"></a>备注

调用此方法为`CSimpleStringT`对象分配特定的缓冲区大小。

`CSimpleStringT`如果无法为字符缓冲区分配空间，则生成STATUS_NO_MEMORY异常。 默认情况下，内存分配由 WIN32 API 函数`HeapAlloc`或`HeapReAlloc`执行。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::Preallocate` 的用法。

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

## <a name="csimplestringtpxstr"></a><a name="pxstr"></a>简单StringT：:PXSTR

指向字符串的指针。

### <a name="syntax"></a>语法

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

## <a name="csimplestringtreleasebuffer"></a><a name="releasebuffer"></a>CSimpleStringT：：释放缓冲区

释放[GetBuffer](#getbuffer)分配的缓冲区的控制权。

### <a name="syntax"></a>语法

```cpp
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>参数

*n 新长度*<br/>
字符串的新长度以字符表示，不包括空终止符。 如果字符串为 null 终止，则 -1 默认值`CSimpleStringT`将大小设置为字符串的当前长度。

### <a name="remarks"></a>备注

调用此方法以重新分配或释放字符串对象的缓冲区。 如果您知道缓冲区中的字符串为 null 终止，则可以省略*nNewLength 参数*。 如果字符串未为 null 终止，请使用*nNewLength*指定其长度。 [GetBuffer](#getbuffer)返回的地址在`ReleaseBuffer`调用后或任何其他`CSimpleStringT`操作无效。

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

## <a name="csimplestringtreleasebuffersetlength"></a><a name="releasebuffersetlength"></a>CSimpleStringT：：释放缓冲区集长度

释放[GetBuffer](#getbuffer)分配的缓冲区的控制权。

### <a name="syntax"></a>语法

```cpp
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>参数

*n 新长度*<br/>
要释放的字符串的长度

### <a name="remarks"></a>备注

此函数在功能上与[ReleaseBuffer](#releasebuffer)类似，只不过必须传递字符串对象的有效长度。

## <a name="csimplestringtsetat"></a><a name="setat"></a>简单Stringt：：Setat

从`CSimpleStringT`对象设置单个字符。

### <a name="syntax"></a>语法

```cpp
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>参数

*i查尔*<br/>
`CSimpleStringT`对象中字符的零基索引。 *iChar*参数必须大于或等于 0，小于[GetLength](#getlength)返回的值。

*ch*<br/>
新字符。

### <a name="remarks"></a>备注

调用此方法来覆盖位于*iChar*的字符。 如果*iChar*超过现有字符串的边界，此方法将不会放大字符串。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::SetAt` 的用法。

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

## <a name="csimplestringtsetmanager"></a><a name="setmanager"></a>简单StringT：setManager

指定`CSimpleStringT`对象的内存管理器。

### <a name="syntax"></a>语法

```cpp
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>参数

*普斯特林姆格*<br/>
指向新内存管理器的指针。

### <a name="remarks"></a>备注

调用此方法以指定`CSimpleStringT`对象使用的新内存管理器。 有关内存管理器和字符串对象的详细信息，请参阅[内存管理和 CStringT](../memory-management-with-cstringt.md)。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::SetManager` 的用法。

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

## <a name="csimplestringtsetstring"></a><a name="setstring"></a>简单StringT：：设置String

设置`CSimpleStringT`对象的字符串。

### <a name="syntax"></a>语法

```cpp
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>参数

*皮茨斯尔克*<br/>
指向 null 终止字符串的指针。

*n 长度*<br/>
*pszSrc*中字符数的计数。

### <a name="remarks"></a>备注

将字符串复制到对象中`CSimpleStringT`。 `SetString`覆盖缓冲区中较旧的字符串数据。

两个版本`SetString`的检查*pszSrc*是否为空指针，如果是，则引发E_INVALIDARG错误。

*szSrc*的单`SetString`参数版本将指向 null 终止字符串。

的`SetString`两参数版本也期望*pszSrc*是一个 null 终止的字符串。 它使用*nLength*作为字符串长度，除非它首先遇到空终止符。

的`SetString`两参数版本还检查*pszSrc*是否指向 中`CSimpleStringT`当前缓冲区中的位置。 在此特殊情况中，`SetString`使用内存复制函数在将字符串数据复制回其缓冲区时不覆盖字符串数据。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::SetString` 的用法。

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

## <a name="csimplestringtstringlength"></a><a name="stringlength"></a>简单StringT：字符串长度

返回指定字符串中的字符数。

### <a name="syntax"></a>语法

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>参数

*psz*<br/>
指向 null 终止字符串的指针。

### <a name="return-value"></a>返回值

*psz*中的字符数 ;不包括空终止符。

### <a name="remarks"></a>备注

调用此方法以检索*psz*指向的字符串中的字符数。

### <a name="example"></a>示例

以下示例演示了 `CSimpleStringT::StringLength` 的用法。

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

## <a name="csimplestringttruncate"></a><a name="truncate"></a>CSimpleStringT：：截流

将字符串截排到新长度。

### <a name="syntax"></a>语法

```cpp
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>参数

*n 新长度*<br/>
字符串的新长度。

### <a name="remarks"></a>备注

调用此方法以将字符串的内容截接到新长度。

> [!NOTE]
> 这不会影响缓冲区的分配长度。 要减小或增加当前缓冲区，请参阅[FreeExtra](#freeextra)和[预分配](#preallocate)。

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

## <a name="csimplestringtunlockbuffer"></a><a name="unlockbuffer"></a>CSimpleStringT：：解锁缓冲区

解锁`CSimpleStringT`对象的缓冲区。

### <a name="syntax"></a>语法

```cpp
void UnlockBuffer() throw();
```

### <a name="remarks"></a>备注

调用此方法将字符串的引用计数重置为 1。

析`CSimpleStringT`构函数会自动调用`UnlockBuffer`以确保在调用析构函数时缓冲区未锁定。 有关此方法的示例，请参阅[LockBuffer](#lockbuffer)。

## <a name="csimplestringtcsimplestringt"></a><a name="dtor"></a>简单StringT：_CSimpleStringT

销毁 `CSimpleStringT` 对象。

### <a name="syntax"></a>语法

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>备注

调用此方法以销毁对象`CSimpleStringT`。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
