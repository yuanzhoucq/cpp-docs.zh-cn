---
title: CStrBufT 类
ms.date: 10/18/2018
f1_keywords:
- CStrBufT
- ATLSIMPSTR/ATL::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::SetLength
- ATLSIMPSTR/ATL::CStrBufT::AUTO_LENGTH
- ATLSIMPSTR/ATL::CStrBufT::SET_LENGTH
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
ms.openlocfilehash: 81c3b429089eab3ba95c178e3fc7cf2bf55783a2
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747445"
---
# <a name="cstrbuft-class"></a>CStrBufT 类

此类提供的自动资源清除`GetBuffer`并`ReleaseBuffer`上的现有调用`CStringT`对象。

## <a name="syntax"></a>语法

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>参数

*TCharType*<br/>
字符类型`CStrBufT`类。 可以是以下各项之一：

- **char** （适用于 ANSI 字符串）

- **wchar_t** （适用于 Unicode 字符串）

- TCHAR （针对 ANSI 和 Unicode 字符串）

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|PCXSTR|指向常量字符串的指针。|
|PXSTR|指向字符串的指针。|
|`StringType`|字符串类型的缓冲区是通过此类模板的专用化操作。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CStrBufT::CStrBufT](#cstrbuft)|字符串缓冲区对象的构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CStrBufT::SetLength](#setlength)|设置关联的字符串对象的字符缓冲区长度。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CStrBufT::operator PCXSTR](#operator_pcxstr)|检索**const**关联的字符串对象的字符缓冲区的指针。|
|[CStrBufT::operator PXSTR](#operator_pxstr)|检索指向关联的字符串对象的字符缓冲区的指针。|

### <a name="public-constants"></a>公共常量

|name|描述|
|----------|-----------------|
|[CStrBufT::AUTO_LENGTH](#auto_length)|自动确定在发行版字符串的新长度。|
|[CStrBufT::SET_LENGTH](#set_length)|在 GetBuffer 时设置的字符串对象的长度|

## <a name="remarks"></a>备注

此类用作替换对的调用包装器类[GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)并[ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)，或[GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)和`ReleaseBuffer`。

主要设计为帮助器类`CStrBufT`提供了方便开发人员使用的字符缓冲区的字符串对象而无需担心如何或何时调用`ReleaseBuffer`。 这可能是因为包装器对象超出作用域自然会发生异常或多个现有的代码路径;导致其析构函数释放字符串资源。

## <a name="requirements"></a>要求

**标头：** atlsimpstr.h

##  <a name="auto_length"></a>  CStrBufT::AUTO_LENGTH

自动确定在发行版字符串的新长度。

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>备注

自动确定在发行版字符串的新长度。 字符串必须是以 null 结尾。

##  <a name="cstrbuft"></a>  CStrBufT::CStrBufT

构造一个缓冲区对象。

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>参数

*str*<br/>
与缓冲区关联的字符串对象。 通常情况下，开发人员将使用的预定义的 typedef `CStrBuf` （TCHAR 变体）， `CStrBufA` (**char**变体) 和`CStrBufW`(**wchar_t**变体)。

*nMinLength*<br/>
字符缓冲区的最小长度。

*dwFlags*<br/>
确定是否自动确定字符串长度。 可以是以下各项之一：

- AUTO_LENGTH 字符串长度会自动确定何时[CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)调用。 字符串必须是以 null 结尾。 默认值。

- 当设置 SET_LENGTH 字符串长度[CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)调用。

### <a name="remarks"></a>备注

创建关联的字符串对象的字符串缓冲区。 在构造期间[CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)或[CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)调用。

请注意，复制构造函数是**专用**。

##  <a name="operator_pcxstr"></a>  CStrBufT::operator PCXSTR

直接访问存储在作为 C 样式字符串关联的字符串对象中的字符。

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>返回值

指向字符串的数据的字符指针。

### <a name="remarks"></a>备注

调用此函数可返回指向字符串对象的字符缓冲区的指针。 字符串对象的内容不能更改与此指针。

##  <a name="operator_pxstr"></a>  CStrBufT::operator PXSTR

直接访问存储在作为 C 样式字符串关联的字符串对象中的字符。

```
operator PXSTR() throw();
```

### <a name="return-value"></a>返回值

指向字符串的数据的字符指针。

### <a name="remarks"></a>备注

调用此函数可返回指向字符串对象的字符缓冲区的指针。 开发人员可能会更改与此指针的字符串对象的内容。

##  <a name="pcxstr"></a>  CStrBufT::PCXSTR

指向常量字符串的指针。

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

##  <a name="pxstr"></a>  CStrBufT::PXSTR

指向字符串的指针。

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

##  <a name="set_length"></a>  CStrBufT::SET_LENGTH

在字符串对象的长度设置`GetBuffer`时间。

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>备注

在 GetBuffer 时设置的字符串对象的长度。

确定是否[CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)并[CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)构造的字符串缓冲区对象时调用。

##  <a name="setlength"></a>  CStrBufT::SetLength

设置字符缓冲区的长度。

```
void SetLength(int nLength);
```

### <a name="parameters"></a>参数

*nLength*<br/>
新的字符串对象的字符缓冲区的长度。

> [!NOTE]
>  必须小于或等于指定的构造函数中的最小缓冲区长度`CStrBufT`。

### <a name="remarks"></a>备注

调用此函数来设置缓冲区对象表示字符串的长度。

##  <a name="stringtype"></a>  CStrBufT::StringType

字符串类型的缓冲区是通过此类模板的专用化操作。

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>备注

`TCharType` 用于使类模板专用化的字符类型。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
