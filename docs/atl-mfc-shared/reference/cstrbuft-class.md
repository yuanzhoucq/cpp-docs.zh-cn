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
ms.openlocfilehash: 4d9d0b403e572d6fdea65355702467c89587cc3a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219074"
---
# <a name="cstrbuft-class"></a>CStrBufT 类

此类提供对现有对象的自动资源清理 `GetBuffer` ，并对该 `ReleaseBuffer` 对象进行调用 `CStringT` 。

## <a name="syntax"></a>语法

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>参数

*TCharType*<br/>
类的字符类型 `CStrBufT` 。 可以是以下值之一：

- **`char`**（对于 ANSI 字符串）

- **`wchar_t`**（对于 Unicode 字符串）

- TCHAR （用于 ANSI 和 Unicode 字符串）

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|PCXSTR|指向常量字符串的指针。|
|PXSTR|指向字符串的指针。|
|`StringType`|其缓冲区将由此类模板的专用化操作的字符串类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CStrBufT::CStrBufT](#cstrbuft)|字符串缓冲区对象的构造函数。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CStrBufT：： SetLength](#setlength)|设置关联的字符串对象的字符缓冲区长度。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CStrBufT：： operator PCXSTR](#operator_pcxstr)|检索 **`const`** 指向关联的字符串对象的字符缓冲区的指针。|
|[CStrBufT：： operator PXSTR](#operator_pxstr)|检索指向关联的字符串对象的字符缓冲区的指针。|

### <a name="public-constants"></a>公共常量

|名称|描述|
|----------|-----------------|
|[CStrBufT：： AUTO_LENGTH](#auto_length)|在发布时自动确定字符串的新长度。|
|[CStrBufT：： SET_LENGTH](#set_length)|在 GetBuffer 时设置字符串对象的长度|

## <a name="remarks"></a>备注

此类用作用于替换对[GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)或[GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)和的调用的包装类 `ReleaseBuffer` 。

主要是设计为帮助器类， `CStrBufT` 它为开发人员提供了一种方便的方法，使开发人员无需担心如何或何时调用即可处理字符串对象的字符缓冲区 `ReleaseBuffer` 。 这是可能的，因为在发生异常或多个退出代码路径时，包装对象自然会超出范围。导致其析构函数释放字符串资源。

## <a name="requirements"></a>要求

**标头：** atlsimpstr

## <a name="cstrbuftauto_length"></a><a name="auto_length"></a>CStrBufT：： AUTO_LENGTH

在发布时自动确定字符串的新长度。

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>备注

在发布时自动确定字符串的新长度。 字符串必须以 null 结尾。

## <a name="cstrbuftcstrbuft"></a><a name="cstrbuft"></a>CStrBufT::CStrBufT

构造缓冲区对象。

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>参数

*字符串*<br/>
与缓冲区关联的字符串对象。 通常，开发人员将使用预定义的 typedef `CStrBuf` （TCHAR 变体）、 `CStrBufA` （ **`char`** variant）和 `CStrBufW` （ **`wchar_t`** variant）。

*nMinLength*<br/>
字符缓冲区的最小长度。

dwFlags**<br/>
确定是否自动确定字符串长度。 可以是以下值之一：

- 调用[CSimpleStringT：： Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)时，自动确定 AUTO_LENGTH 字符串长度。 字符串必须以 null 结尾。 默认值。

- 调用[CSimpleStringT：： GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)时设置 SET_LENGTH 字符串长度。

### <a name="remarks"></a>备注

为关联的字符串对象创建一个字符串缓冲区。 在构造过程中，将调用[CSimpleStringT：： GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)或[CSimpleStringT：： GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) 。

请注意，复制构造函数为 **`private`** 。

## <a name="cstrbuftoperator-pcxstr"></a><a name="operator_pcxstr"></a>CStrBufT：： operator PCXSTR

直接访问存储在关联字符串对象中的字符作为 C 样式字符串。

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>返回值

指向字符串数据的字符指针。

### <a name="remarks"></a>备注

调用此函数可返回指向字符串对象的字符缓冲区的指针。 不能通过此指针更改字符串对象的内容。

## <a name="cstrbuftoperator-pxstr"></a><a name="operator_pxstr"></a>CStrBufT：： operator PXSTR

直接访问存储在关联字符串对象中的字符作为 C 样式字符串。

```
operator PXSTR() throw();
```

### <a name="return-value"></a>返回值

指向字符串数据的字符指针。

### <a name="remarks"></a>备注

调用此函数可返回指向字符串对象的字符缓冲区的指针。 开发人员可以通过此指针更改字符串对象的内容。

## <a name="cstrbuftpcxstr"></a><a name="pcxstr"></a>CStrBufT：:P CXSTR

指向常量字符串的指针。

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

## <a name="cstrbuftpxstr"></a><a name="pxstr"></a>CStrBufT：:P XSTR

指向字符串的指针。

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

## <a name="cstrbuftset_length"></a><a name="set_length"></a>CStrBufT：： SET_LENGTH

设置字符串对象的 `GetBuffer` 时间长度。

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>备注

在 GetBuffer 时设置字符串对象的长度。

确定在构造字符串缓冲区对象时是否调用[CSimpleStringT：： GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[CSimpleStringT：： GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) 。

## <a name="cstrbuftsetlength"></a><a name="setlength"></a>CStrBufT：： SetLength

设置字符缓冲区的长度。

```cpp
void SetLength(int nLength);
```

### <a name="parameters"></a>参数

*nLength*<br/>
字符串对象的字符缓冲区的新长度。

> [!NOTE]
> 必须小于或等于在的构造函数中指定的最小缓冲区长度 `CStrBufT` 。

### <a name="remarks"></a>备注

调用此函数可设置缓冲区对象表示的字符串的长度。

## <a name="cstrbuftstringtype"></a><a name="stringtype"></a>CStrBufT::StringType

其缓冲区将由此类模板的专用化操作的字符串类型。

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>备注

`TCharType`用于使类模板专用化的字符类型。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
