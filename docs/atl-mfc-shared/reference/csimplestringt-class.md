---
title: "CSimpleStringT 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 1a00023e4d3e31ddb6381e90a50231449b1de18d
ms.openlocfilehash: e273aff69b9c8dbea4fb829798b2e9d58351b9dd
ms.lasthandoff: 02/28/2017

---
# <a name="csimplestringt-class"></a>CSimpleStringT 类
此类表示`CSimpleStringT`对象。  
  
## <a name="syntax"></a>语法  
  
```
template <typename BaseType>
class CSimpleStringT
```  
  
### <a name="parameters"></a>参数  
 `BaseType`  
 此字符串类字符类型。 可以是以下各项之一：  
  
- `char`（针对 ANSI 字符串）。  
  
- `wchar_t`（对于 Unicode 字符串）。  
  
- **TCHAR** （针对 ANSI 和 Unicode 字符串）。  

## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|[CSimpleStringT::PCXSTR](#pcxstr)|指向常量字符串的指针。|  
|[CSimpleStringT::PXSTR](#pxstr)|指向字符串的指针。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSimpleStringT::CSimpleStringT](#ctor)|构造`CSimpleStringT`对象以各种方式。|  
|[CSimpleStringT:: ~ CSimpleStringT](#dtor)|析构函数。|  

  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSimpleStringT::Append](#append)|追加`CSimpleStringT`对象传递给现有`CSimpleStringT`对象。|  
|[CSimpleStringT::AppendChar](#appendchar)|将字符追加到现有`CSimpleStringT`对象。|  
|[CSimpleStringT::CopyChars](#copychars)|将一个字符复制到另一个字符串。|  
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|将一个字符复制到另一个缓冲区与重叠的字符串。|  
|[CSimpleStringT::Empty](#empty)|强制的长度为零的字符串。|  
|[CSimpleStringT::FreeExtra](#freeextra)|释放以前分配的字符串对象的任何额外内存。|  
|[CSimpleStringT::GetAllocLength](#getalloclength)|检索的已分配的长度`CSimpleStringT`对象。|  
|[CSimpleStringT::GetAt](#getat)|返回位于给定位置处的字符。|  
|[CSimpleStringT::GetBuffer](#getbuffer)|将指针返回到的字符`CSimpleStringT`。|  
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|将指针返回到的字符`CSimpleStringT`、 截断到指定的长度。|  
|[CSimpleStringT::GetLength](#getlength)|返回中的字符数`CSimpleStringT`对象。|  
|[CSimpleStringT::GetManager](#getmanager)|检索的内存管理器`CSimpleStringT`对象。|  
|[CSimpleStringT::GetString](#getstring)|检索字符串|  
|[CSimpleStringT::IsEmpty](#isempty)|测试是否`CSimpleStringT`对象不包含任何字符。|  
|[CSimpleStringT::LockBuffer](#lockbuffer)|禁用引用计数，并保护缓冲区中的字符串。|  
|[CSimpleStringT::Preallocate](#preallocate)|为字符缓冲区中分配了特定的内存量。|  
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|释放控件返回的缓冲区`GetBuffer`。|  
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|释放控件返回的缓冲区`GetBuffer`。|  
|[CSimpleStringT::SetAt](#setat)|设置给定位置的字符。|  
|[CSimpleStringT::SetManager](#setmanager)|设置内存管理器的`CSimpleStringT`对象。|  
|[CSimpleStringT::SetString](#setstring)|设置的字符串`CSimpleStringT`对象。|  
|[CSimpleStringT::StringLength](#stringlength)|返回指定字符串中的字符数。|  
|[CSimpleStringT::Truncate](#truncate)|将截断到指定长度的字符串。|  
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|使引用计数，并释放缓冲区中的字符串。|  

### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CSimpleStringT::operator PCXSTR](#operator_pcxstr)|直接访问存储在字符`CSimpleStringT`对象用作 C 样式字符串。|  
|[CSimpleStringT::operator\[\]](#operator_at)|返回位于给定位置处的字符 — 的运算符替换`GetAt`。|  
|[CSimpleStringT::operator + =](#operator_add_eq)|连接到现有字符串的末尾的新字符串。|  
|[CSimpleStringT::operator =](#operator_eq)|将一个新值赋给`CSimpleStringT`对象。|  
  
### <a name="remarks"></a>备注  
 `CSimpleStringT`是由 Visual c + + 支持的各种字符串类的基类。 它提供对基本缓冲区操作的字符串对象的内存管理的最小支持。 有关更高级的字符串对象，请参阅[CStringT 类](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="requirements"></a>要求  
 **标头︰** atlsimpstr.h  


## <a name="append"></a>CSimpleStringT::Append
追加`CSimpleStringT`对象传递给现有`CSimpleStringT`对象。  
  
### <a name="syntax"></a>语法  
  
```  
void Append(const CSimpleStringT& strSrc); 
void Append(PCXSTR pszSrc, int nLength); 
void Append(PCXSTR pszSrc);
```  
#### <a name="parameters"></a>参数  
 `strSrc`  
 `CSimpleStringT`要追加的对象。  
  
 `pszSrc`  
 指向包含要追加的字符的字符串的指针。  
  
 `nLength`  
 要追加的字符数。  
  
### <a name="remarks"></a>备注  
 调用此方法可将附加的现有`CSimpleStringT`对象传递给另一个`CSimpleStringT`对象。  
  
### <a name="example"></a>示例  
 以下示例演示了 `CSimpleStringT::Append` 的用法。  
  
```cpp  
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```
  
##  <a name="appendchar"></a>CSimpleStringT::AppendChar
将字符追加到现有`CSimpleStringT`对象。  
  
### <a name="syntax"></a>语法  
  
```  
void AppendChar(XCHAR ch);
```  
#### <a name="parameters"></a>参数  
 *ch*  
 要追加的字符  
  
### <a name="remarks"></a>备注  
 调用此函数可将指定的字符追加到现有的末尾`CSimpleStringT`对象。  
  
##  <a name="copychars"></a>CSimpleStringT::CopyChars  
 将复制的字符或字符`CSimpleStringT`对象。  
  
### <a name="syntax"></a>语法  
  
```  
static void CopyChars(
  XCHAR* pchDest,
  const XCHAR* pchSrc, 
  int nChars) throw();
```  
#### <a name="parameters"></a>参数  
 `pchDest`  
 指向字符字符串的指针。  
  
 `pchSrc`  
 指向包含要复制的字符的字符串的指针。  
  
 `nChars`  
 数`pchSrc`要复制的字符。  
  
### <a name="remarks"></a>备注  
 调用此方法以将字符从复制`pchSrc`到`pchDest`字符串。  
  
### <a name="example"></a>示例  
 以下示例演示了 `CSimpleStringT::CopyChars` 的用法。  
  
```cpp  
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```
  
##  <a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsOverlapped
将复制的字符或字符`CSimpleStringT`对象。  
  
### <a name="syntax"></a>语法  
  
```  
static void CopyCharsOverlapped(
  XCHAR* pchDest,
  const XCHAR* pchSrc,
  int nChars) throw(); 
```  
#### <a name="parameters"></a>参数  
 `pchDest`  
 指向字符字符串的指针。  
  
 `pchSrc`  
 指向包含要复制的字符的字符串的指针。  
  
 `nChars`  
 数`pchSrc`要复制的字符。  
  
### <a name="remarks"></a>备注  
 调用此方法以将字符从复制`pchSrc`到`pchDest`字符串。 与不同`CopyChars`，`CopyCharsOverlapped`提供复制可能重叠的字符缓冲区中的安全方法。  
  
### <a name="example"></a>示例  
 请参阅示例[CSimpleStringT::CopyChars](#copychars)，或为源代码`CSimpleStringT::SetString`（位于 atlsimpstr.h）。  
  
##  <a name="ctor"></a>CSimpleStringT::CSimpleStringT  
 构造 `CSimpleStringT` 对象。  
  
### <a name="syntax"></a>语法  
  
```  
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr); 
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr); 
CSimpleStringT(const CSimpleStringT& strSrc); 
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw(); 
```  
#### <a name="parameters"></a>参数  
 `strSrc`  
 现有`CSimpleStringT`要复制到此对象`CSimpleStringT`对象。  
  
 `pchSrc`  
 指向字符数组的长度的指针`nLength`，不以 null 结尾。  
  
 `pszSrc`  
 以 null 结尾的字符串复制到此`CSimpleStringT`对象。  
  
 `nLength`  
 中的字符数的计数`pch`。  
  
 `pStringMgr`  
 指向的内存管理器的指针`CSimpleStringT`对象。 有关详细信息`IAtlStringMgr`和内存管理`CSimpleStringT`，请参阅[内存管理和 CStringT](../memory-management-with-cstringt.md)。  
  
### <a name="remarks"></a>备注  
 构造一个新`CSimpleStringT`对象。 因为构造函数将输入的数据复制到新的已分配存储，可能会导致内存异常。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`CSimpleStringT::CSimpleStringT`使用 ATL `typedef` `CSimpleString`。 `CSimpleString`是常用的类模板专用化`CSimpleStringT`。  
  
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

  
##  <a name="empty"></a>CSimpleStringT::Empty
这样，您`CSimpleStringT`对象为空字符串，并释放相应的内存。  
  
### <a name="syntax"></a>语法  
  
```  
void Empty() throw();  
```  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[字符串︰ CString 异常清理](../cstring-exception-cleanup.md)。  
  
### <a name="example"></a>示例  
 以下示例演示了 `CSimpleStringT::Empty` 的用法。  
  
```cpp  
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());  
```  
  
##  <a name="freeextra"></a>CSimpleStringT::FreeExtra
释放以前分配的字符串，但不再需要任何额外内存。  
  
### <a name="syntax"></a>语法  
  
```  
void FreeExtra(); 
```  
### <a name="remarks"></a>备注  
 这应减少字符串对象占用的内存开销。 该方法将重新分配到返回的确切长度的缓冲区[GetLength](#getlength)。  
  
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
 此示例的输出是，如下所示︰  
  
 `Alloc length is 1031, String length is 1024`  
  
 `Alloc length is 1031, String length is 15`  
  
 `Alloc length is 15, String length is 15`  
  
##  <a name="getalloclength"></a>CSimpleStringT::GetAllocLength  
检索的已分配的长度`CSimpleStringT`对象。  
  
### <a name="syntax"></a>语法  
  
```  
int GetAllocLength() const throw();  
```  
### <a name="return-value"></a>返回值  
 为此对象分配的字符数。  
  
### <a name="remarks"></a>备注  
 调用此方法来确定此分配的字符数`CSimpleStringT`对象。 请参阅[FreeExtra](#freeextra)有关调用此函数的示例。  
  
##  <a name="getat"></a>CSimpleStringT::GetAt  
返回从一个字符`CSimpleStringT`对象。  
  
### <a name="syntax"></a>语法  
  
```  
XCHAR GetAt(int iChar) const;
```  
#### <a name="parameters"></a>参数  
 `iChar`  
 中字符的从零开始索引`CSimpleStringT`对象。 `iChar`参数必须是大于或等于 0 且小于返回的值[GetLength](#getlength)。 否则为`GetAt`将生成一个异常。  
  
### <a name="return-value"></a>返回值  
 `XCHAR` ，其中包含在字符串中指定的位置处的字符。  
  
### <a name="remarks"></a>备注  
 调用此方法以返回由指定的一个字符`iChar`。 重载的下标 (`[]`) 运算符是一个方便别名，为`GetAt`。 空终止符是可寻址的而不会生成异常，通过使用`GetAt`。 但是，不计入`GetLength`，并且返回的值为 0。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`CSimpleStringT::GetAt`。  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```
  
##  <a name="getbuffer"></a>CSimpleStringT::GetBuffer  
将指针返回到的内部字符缓冲区`CSimpleStringT`对象。  
  
### <a name="syntax"></a>语法  
  
```  
PXSTR GetBuffer(int nMinBufferLength); 
PXSTR GetBuffer();
```  
#### <a name="parameters"></a>参数  
 `nMinBufferLength`  
 最小字符缓冲区可以容纳的字符数。 此值不包括 null 终止符的空间。  
  
 如果`nMinBufferLength`大于当前缓冲区的长度`GetBuffer`销毁当前缓冲区、 替换请求的大小的缓冲区并将对象引用计数重置为零。 如果以前已调用[LockBuffer](#lockbuffer)上此缓冲区，则会丢失缓冲区锁。  
  
### <a name="return-value"></a>返回值  
 `PXSTR`指向的对象 （以 null 结尾） 的字符串缓冲区的指针。  
  
### <a name="remarks"></a>备注  
 调用此方法可返回的缓冲区内容`CSimpleStringT`对象。 返回`PXSTR`都不是常量，从而使得可以直接修改`CSimpleStringT`内容。  
  
 如果您使用返回的指针`GetBuffer`若要更改的字符串内容，必须调用[ReleaseBuffer](#releasebuffer)使用任何其他之前`CSimpleStringT`成员方法。  
  
 返回的地址`GetBuffer`后在调用可能不有效`ReleaseBuffer`因为其他`CSimpleStringT`操作可能会导致`CSimpleStringT`缓冲区被重新分配。 如果不更改的长度，不重新分配缓冲区`CSimpleStringT`。  
  
 缓冲内存将自动释放时`CSimpleStringT`对象被销毁。  
  
 如果您跟踪的字符串长度自己，您应该不追加终止 null 字符。 但是，必须指定最终字符串长度，当你释放缓冲区与`ReleaseBuffer`。 如果您执行追加终止 null 字符，应传递-1 （默认值） 的长度。 `ReleaseBuffer`然后，确定缓冲区的长度。  
  
 如果内存不足，无法满足`GetBuffer`请求时，此方法将引发 CMemoryException *。  
  
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
  
##  <a name="getbuffersetlength"></a>CSimpleStringT::GetBufferSetLength  
将指针返回到的内部字符缓冲区`CSimpleStringT`对象，截断或不断增加其长度，如有必要完全匹配工作中指定的长度`nLength`。  
  
### <a name="syntax"></a>语法  
  
```  
PXSTR GetBufferSetLength(int nLength);
```  
#### <a name="parameters"></a>参数  
 `nLength`  
 确切大小`CSimpleStringT`以字符为单位的字符缓冲区。  
  
### <a name="return-value"></a>返回值  
 一个`PXSTR`指向的对象 （以 null 结尾） 的字符串缓冲区的指针。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索在指定的内部缓冲区的长度`CSimpleStringT`对象。 返回`PXSTR`指针不是`const`从而可以直接修改`CSimpleStringT`内容。  
  
 如果您使用返回的指针[GetBufferSetLength](#getbuffersetlength)若要更改字符串内容，请调用`ReleaseBuffer`要更新的内部状态`CsimpleStringT`使用任何其他之前`CSimpleStringT`方法。  
  
 返回的地址`GetBufferSetLength`后在调用可能不有效`ReleaseBuffer`因为其他`CSimpleStringT`操作可能会导致`CSimpleStringT`缓冲区被重新分配。 如果不更改的长度，不重新分配缓冲区`CSimpleStringT`。  
  
 缓冲内存将自动释放时`CSimpleStringT`对象被销毁。  
  
 如果您跟踪的字符串长度自己，不对不追加终止 null 字符。 通过释放缓冲区时，必须指定最终字符串长度`ReleaseBuffer`。 如果在调用时，请执行追加终止 null 字符`ReleaseBuffer`，将为-1 （默认值） 传递到长度`ReleaseBuffer`，和`ReleaseBuffer`将执行`strlen`上要确定其长度的缓冲区。  
  
 引用计数的详细信息，请参阅以下文章︰  
  
- [管理对象生存期通过引用计数](http://msdn.microsoft.com/library/windows/desktop/ms687260)Windows SDK 中。 
  
- [实现引用计数](http://msdn.microsoft.com/library/windows/desktop/ms693431)Windows SDK 中。
  
- [管理的引用计数的规则](http://msdn.microsoft.com/library/windows/desktop/ms692481)Windows SDK 中。  
  
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
  
##  <a name="getlength"></a>CSimpleStringT::GetLength  
返回中的字符数`CSimpleStringT`对象。  
  
### <a name="syntax"></a>语法  
  
```  
int GetLength() const throw();  
```  
### <a name="return-value"></a>返回值  
 在字符串中字符数。  
  
### <a name="remarks"></a>备注  
 调用此方法以返回对象中的字符数。 该计数不包括 null 终止符。  
  
 对于多字节字符集 (MBCS)，`GetLength`一个多字节字符中的每个 8 位字符; 也就是说，主管和记录字节计为两个字节的计数。 请参阅[FreeExtra](#freeextra)有关调用此函数的示例。  
  
##  <a name="getmanager"></a>CSimpleStringT::GetManager  
检索的内存管理器`CSimpleStringT`对象。  
  
### <a name="syntax"></a>语法  
  
```  
IAtlStringMgr* GetManager() const throw();  
```  
### <a name="return-value"></a>返回值  
 指向内存管理器为`CSimpleStringT`对象。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索内存管理器使用`CSimpleStringT`对象。 有关内存管理器和字符串对象的详细信息，请参阅[内存管理和 CStringT](../memory-management-with-cstringt.md)。  
  
##  <a name="getstring"></a>CSimpleStringT::GetString
检索字符字符串。  
  
### <a name="syntax"></a>语法  
  
```  
PCXSTR GetString() const throw();
```  
### <a name="return-value"></a>返回值  
 指向以 null 结尾的字符串的指针。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索与关联的字符字符串`CSimpleStringT`对象。  
  
> [!NOTE]
>  返回`PCXSTR`指针`const`，并且不允许直接修改`CSimpleStringT`内容。  
  
### <a name="example"></a>示例  
 以下示例演示了 `CSimpleStringT::GetString` 的用法。  
  
```cpp  
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```
  
##  <a name="isempty"></a>CSimpleStringT::IsEmpty  
测试`CSimpleStringT`对象为空的条件。  
  
### <a name="syntax"></a>语法  
  
```  
bool IsEmpty() const throw();  
```  
### <a name="return-value"></a>返回值  
 返回**true**如果`CSimpleStringT`对象具有零长度; 否则为**false**。  
  
### <a name="remarks"></a>备注  
 调用此方法来确定对象是否包含空字符串。  
  
### <a name="example"></a>示例  
 以下示例演示了 `CSimpleStringT::IsEmpty` 的用法。  
  
```cpp  
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```
  
##  <a name="lockbuffer"></a>CSimpleStringT::LockBuffer  
禁用引用计数，并保护缓冲区中的字符串。  
  
### <a name="syntax"></a>语法  
  
```  
PXSTR LockBuffer();
```  
### <a name="return-value"></a>返回值  
 一个指向`CSimpleStringT`对象或以 null 结尾的字符串。  
  
### <a name="remarks"></a>备注  
 调用此方法可锁定的缓冲`CSimpleStringT`对象。 通过调用`LockBuffer`，使用引用计数为 –&1; 创建字符串的副本。 当引用计数值为-1 时，缓冲区中的字符串被视为处于"锁定"状态。 处于锁定状态时该字符串是受保护的两种方式︰  
  
-   没有任何其他字符串可以在锁定的字符串中，获取对数据的引用，即使该字符串分配给已锁定的字符串。  
  
-   锁定的字符串永远不会将引用另一个字符串，即使该另一个字符串复制到锁定的字符串。  
  
 通过在缓冲区中锁定该字符串，可确保该字符串的独占持有对缓冲区将保持不变。  
  
 您用完后`LockBuffer`，调用[UnlockBuffer](#unlockbuffer)的引用计数重置为 1。  
  
> [!NOTE]
>  如果调用[GetBuffer](#getbuffer)锁定的缓冲区上设置`GetBuffer`参数`nMinBufferLength`为大于当前缓冲区的长度，则将失去缓冲区锁。 此类调用到`GetBuffer`销毁当前缓冲区、 替换请求的大小的缓冲区并将引用计数重置为零。  
  
 引用计数的详细信息，请参阅以下文章︰  
  
- [管理对象生存期通过引用计数](http://msdn.microsoft.com/library/windows/desktop/ms687260)Windows SDK 中  
  
- [实现引用计数](http://msdn.microsoft.com/library/windows/desktop/ms693431)Windows SDK 中  
  
- [管理的引用计数的规则](http://msdn.microsoft.com/library/windows/desktop/ms692481)Windows SDK 中  
  
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
  
##  <a name="operator_at"></a>CSimpleStringT::operator\[\]  
调用此函数可访问单个字符的字符数组。  
  
### <a name="syntax"></a>语法  
  
```  
XCHAR operator[](int iChar) const;
```  
#### <a name="parameters"></a>参数  
 `iChar`  
 字符串中字符的从零开始索引。  
  
### <a name="remarks"></a>备注  
 重载的下标 (`[]`) 运算符将返回由中从零开始的索引指定单个字符`iChar`。 此运算符是一个便捷替代[GetAt](#getat)成员函数。  
  
> [!NOTE]
>  您可以使用下标 (`[]`) 运算符来获取的值中的字符`CSimpleStringT`，但不是能使用它来更改中的字符值`CSimpleStringT`。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用**CSimpleStringT::operator []**。  
  
```cpp  
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```
  
## <a name="operator_at"></a>CSimpleStringT::operator\[\]
调用此函数可访问单个字符的字符数组。  
  
### <a name="syntax"></a>语法  
  
```   
XCHAR operator[](int iChar) const;
```  
  
### <a name="parameters"></a>参数  
 `iChar`  
 字符串中字符的从零开始索引。  
  
### <a name="remarks"></a>备注  
 重载的下标 (`[]`) 运算符将返回由中从零开始的索引指定单个字符`iChar`。 此运算符是一个便捷替代[GetAt](#getat)成员函数。  
  
> [!NOTE]
>  您可以使用下标 (`[]`) 运算符来获取的值中的字符`CSimpleStringT`，但不是能使用它来更改中的字符值`CSimpleStringT`。  
  
  
##  <a name="operator_add_eq"></a>CSimpleStringT::operator + =  
将一个新字符串或字符联接到现有字符串的末尾。  
  
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
 `pszSrc`  
 指向以 null 结尾的字符串的指针。  
  
 `strSrc`  
 一个指向现有`CSimpleStringT`对象。  
  
 *ch*  
 要追加的字符。  
  
### <a name="remarks"></a>备注  
 运算符可接受另一个`CSimpleStringT`对象或一个字符。 请注意，内存可能会发生异常，只要您使用此连接运算符，因为可能会分配新存储的字符添加到此`CSimpleStringT`对象。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用**CSimpleStringT::operator + =**。  
  
```cpp  
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```
  
##  <a name="operator_eq"></a>CSimpleStringT::operator =  
将一个新值赋给`CSimpleStringT`对象。  
  
### <a name="syntax"></a>语法  
  
```  
CSimpleStringT& operator =(PCXSTR pszSrc); 
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```  
#### <a name="parameters"></a>参数  
 `pszSrc`  
 指向以 null 结尾的字符串的指针。  
  
 `strSrc`  
 一个指向现有`CSimpleStringT`对象。  
  
### <a name="remarks"></a>备注  
 如果目标字符串 （左侧） 已足够大，无法存储新数据，会不执行任何新的内存分配。 请注意，内存可能会发生异常，只要您使用赋值运算符，因为通常分配新存储来存放所生成`CSimpleStringT`对象。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用**CSimpleStringT::operator =**。  
  
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
  
##  <a name="operator_pcxstr"></a>CSimpleStringT::operator PCXSTR  

 直接访问存储在字符`CSimpleStringT`对象用作 C 样式字符串。  
  
### <a name="syntax"></a>语法  
  
```  
operator PCXSTR() const throw();
```  
### <a name="return-value"></a>返回值  
 指向字符串的数据的字符指针。  
  
### <a name="remarks"></a>备注  
 没有字符被复制;仅一个指针，则返回。 请慎用此运算符。 如果您更改`CString`对象获得的字符指针后，您可能会导致重新分配的内存使无效指针。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用**CSimpleStringT::operator PCXSTR**。  
  
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
  
##  <a name="pcxstr"></a>CSimpleStringT::PCXSTR
指向常量字符串的指针。  
  
### <a name="syntax"></a>语法  
  
```  
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;    
```  
##  <a name="preallocate"></a>CSimpleStringT::Preallocate  
分配特定量的字节数的`CSimpleStringT`对象。  
  
### <a name="syntax"></a>语法  
  
```  
void Preallocate( int nLength);
```  
#### <a name="parameters"></a>参数  
 `nLength`  
 确切大小`CSimpleStringT`以字符为单位的字符缓冲区。  
  
### <a name="remarks"></a>备注  
 调用此方法来分配的特定的缓冲区大小`CSimpleStringT`对象。  
  
 `CSimpleStringT`生成`STATUS_NO_MEMORY`异常，如果无法为字符缓冲区的分配空间。 默认情况下，通过 WIN32 API 函数来执行内存分配`HeapAlloc`或`HeapReAlloc`。  
  
### <a name="example"></a>示例  
 以下示例演示了 `CSimpleStringT::Preallocate` 的用法。  
  
```cpp  
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```
  
##  <a name="pxstr"></a>CSimpleStringT::PXSTR  
指向字符串的指针。  
  
### <a name="syntax"></a>语法  
  
```  
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;  
```  
##  <a name="releasebuffer"></a>CSimpleStringT::ReleaseBuffer  
释放分配的缓冲区的控制[GetBuffer](#getbuffer)。  
  
### <a name="syntax"></a>语法  
  
```  
void ReleaseBuffer(int nNewLength = -1);
```  
#### <a name="parameters"></a>参数  
 `nNewLength`  
 中不包括 null 终止符的字符的字符串的新长度。 如果字符串为 null 终止，则为-1 默认值将设置`CSimpleStringT`大小达到该字符串的当前长度。  
  
### <a name="remarks"></a>备注  
 调用此方法以重新分配或释放的缓冲区的字符串对象。 如果您知道，在缓冲区中的字符串是以 null 结尾，则可以省略`nNewLength`参数。 如果您的字符串不是 null 终止，则使用`nNewLength`来指定它的长度。 返回的地址[GetBuffer](#getbuffer)是无效的调用之后`ReleaseBuffer`或任何其他`CSimpleStringT`操作。  
  
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
  
##  <a name="releasebuffersetlength"></a>CSimpleStringT::ReleaseBufferSetLength

释放分配的缓冲区的控制[GetBuffer](#getbuffer)。  
  
### <a name="syntax"></a>语法  
  
```  
void ReleaseBufferSetLength(int nNewLength);
```  
#### <a name="parameters"></a>参数  
 `nNewLength`  
 发布字符串的长度  
  
### <a name="remarks"></a>备注  
 此函数是功能上类似于[ReleaseBuffer](#releasebuffer)只不过必须传递的字符串对象的有效长度。  
  
##  <a name="setat"></a>CSimpleStringT::SetAt  
设置中的单个字符`CSimpleStringT`对象。  
  
### <a name="syntax"></a>语法  
  
```  
void SetAt(int iChar, XCHAR ch);
```  
#### <a name="parameters"></a>参数  
 `iChar`  
 中字符的从零开始索引`CSimpleStringT`对象。 `iChar`参数必须是大于或等于 0 且小于返回的值[GetLength](#getlength)。  
  
 *ch*  
 新的字符。  
  
### <a name="remarks"></a>备注  
 调用此方法来覆盖位于处的字符`iChar`。 此方法将不会增大该字符串，如果`iChar`超出了现有字符串的界限。  
  
### <a name="example"></a>示例  
 以下示例演示了 `CSimpleStringT::SetAt` 的用法。  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
``` 
  
##  <a name="setmanager"></a>CSimpleStringT::SetManager  
指定的内存管理器`CSimpleStringT`对象。  
  
### <a name="syntax"></a>语法  
  
```  
void SetManager(IAtlStringMgr* pStringMgr);
```  
#### <a name="parameters"></a>参数  
 `pStringMgr`  
 指向新的内存管理器的指针。  
  
### <a name="remarks"></a>备注  
 调用此方法以指定新的内存管理器使用`CSimpleStringT`对象。 有关内存管理器和字符串对象的详细信息，请参阅[内存管理和 CStringT](../memory-management-with-cstringt.md)。  
  
### <a name="example"></a>示例  
 以下示例演示了 `CSimpleStringT::SetManager` 的用法。  
  
```cpp  
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```
  
##  <a name="setstring"></a>CSimpleStringT::SetString  
设置的字符串`CSimpleStringT`对象。  
  
### <a name="syntax"></a>语法  
  
```  
void SetString(PCXSTR pszSrc, int nLength); 
void SetString(PCXSTR pszSrc);
```  
#### <a name="parameters"></a>参数  
 `pszSrc`  
 指向以 null 结尾的字符串的指针。  
  
 `nLength`  
 中的字符数的计数`pszSrc`。  
  
### <a name="remarks"></a>备注  
 复制字符串转换`CSimpleStringT`对象。 `SetString`将覆盖较旧的字符串数据缓冲区中。  
  
 这两个版本`SetString`检查是否`pszSrc`是 null 指针，以及如果是，引发**E_INVALIDARG**错误。  
  
 单参数版本`SetString`期望`pszSrc`为指向以 null 结尾的字符串。  
  
 两个参数版本的`SetString`还预期`pszSrc`是以 null 结尾的字符串。 它使用`nLength`作为字符串长度除非首先遇到 null 终止符。  
  
 两个参数版本的`SetString`还会检查是否`pszSrc`指向当前缓冲区中的某个位置`CSimpleStringT`。 在此特殊情况下，`SetString`使用不会覆盖的字符串数据，因为它会将字符串数据复制回其缓冲区内存复制功能。  
  
### <a name="example"></a>示例  
 以下示例演示了 `CSimpleStringT::SetString` 的用法。  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```
  
##  <a name="stringlength"></a>CSimpleStringT::StringLength  
返回指定字符串中的字符数。  
  
### <a name="syntax"></a>语法  
  
```  
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```  
#### <a name="parameters"></a>参数  
 `psz`  
 指向以 null 结尾的字符串的指针。  
  
### <a name="return-value"></a>返回值  
 中的字符数`psz`; 不包括 null 终止符。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索所指向的字符串中的字符数`psz`。  
  
### <a name="example"></a>示例  
 以下示例演示了 `CSimpleStringT::StringLength` 的用法。  
  
```cpp  
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
``` 
  
##  <a name="truncate"></a>CSimpleStringT::Truncate
将截断到新的长度的字符串。  
  
### <a name="syntax"></a>语法  
  
```  
void Truncate(int nNewLength);
```  
#### <a name="parameters"></a>参数  
 `nNewLength`  
 新的字符串的长度。  
  
### <a name="remarks"></a>备注  
 调用此方法来截断到新的长度的字符串的内容。  
  
> [!NOTE]
>  此值不影响已分配缓冲区的长度。 若要减小或增大当前缓冲区，请参阅[FreeExtra](#freeextra)和[Preallocate](#preallocate)。  
  
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
  
##  <a name="unlockbuffer"></a>CSimpleStringT::UnlockBuffer
 取消锁定的缓冲区`CSimpleStringT`对象。  
  
### <a name="syntax"></a>语法  
  
```  
void UnlockBuffer() throw();
```  
### <a name="remarks"></a>备注  
 调用此方法以将该字符串的引用计数重置为 1。  
  
 `CSimpleStringT`析构函数自动调用`UnlockBuffer`以确保在调用的析构函数时未锁定缓冲区。 此方法的示例，请参阅[LockBuffer](#lockbuffer)。  
  
##  <a name="dtor"></a>CSimpleStringT:: ~ CSimpleStringT
销毁 `CSimpleStringT` 对象。  
  
### <a name="syntax"></a>语法  
  
```  
~CSimpleStringT() throw();
```  
### <a name="remarks"></a>备注  
 调用此方法可销毁`CSimpleStringT`对象。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
