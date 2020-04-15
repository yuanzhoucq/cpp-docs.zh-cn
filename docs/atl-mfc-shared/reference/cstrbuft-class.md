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
ms.openlocfilehash: 84c67aa8ea819f420368a72a2374f800f3d89055
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317648"
---
# <a name="cstrbuft-class"></a>CStrBufT 类

此类为现有`GetBuffer``CStringT`对象提供自动资源清理`ReleaseBuffer`和调用。

## <a name="syntax"></a>语法

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>参数

*TCharType*<br/>
类的`CStrBufT`字符类型。 可以是以下值之一：

- **字符**（用于 ANSI 字符串）

- **wchar_t（** 用于 Unicode 字符串）

- TCHAR（适用于 ANSI 和 Unicode 字符串）

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|PCXSTR|指向常量字符串的指针。|
|PXSTR|指向字符串的指针。|
|`StringType`|其缓冲区将由此类模板的专门化操作的字符串类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CStrBufT：CStrBufT](#cstrbuft)|字符串缓冲区对象的构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CStrBufT：：设置长度](#setlength)|设置关联字符串对象的字符缓冲区长度。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CStrBufT：：操作员PCXSTR](#operator_pcxstr)|检索指向关联字符串对象的字符缓冲区的**const**指针。|
|[CStrBufT：：操作员PXSTR](#operator_pxstr)|检索指向关联字符串对象的字符缓冲区的指针。|

### <a name="public-constants"></a>公共常量

|名称|说明|
|----------|-----------------|
|[CStrBufT：AUTO_LENGTH](#auto_length)|在发布时自动确定字符串的新长度。|
|[CStrBufT：SET_LENGTH](#set_length)|在 GetBuffer 时间设置字符串对象的长度|

## <a name="remarks"></a>备注

此类用作包装类，用于替换对[GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[释放缓冲区](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)的调用，或[GetBufferSet](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) `ReleaseBuffer`长度和 。

主要设计为帮助器类，`CStrBufT`为开发人员提供了一种使用字符串对象的字符缓冲区的便捷方法，而不必担心如何或何时调用`ReleaseBuffer`。 这是可能的，因为包装对象在异常或多个退出代码路径的情况下自然超出范围;导致其析构函数释放字符串资源。

## <a name="requirements"></a>要求

**标题：** atlsimpstr.h

## <a name="cstrbuftauto_length"></a><a name="auto_length"></a>CStrBufT：AUTO_LENGTH

在发布时自动确定字符串的新长度。

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>备注

在发布时自动确定字符串的新长度。 字符串必须为 null 终止。

## <a name="cstrbuftcstrbuft"></a><a name="cstrbuft"></a>CStrBufT：CStrBufT

构造缓冲区对象。

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>参数

*Str*<br/>
与缓冲区关联的字符串对象。 通常`CStrBuf`，开发人员将使用预定义的类型def（TCHAR变体）、（`CStrBufA`**字符**变体）和`CStrBufW`**（wchar_t**变体）。

*n 最小长度*<br/>
字符缓冲区的最小长度。

dwFlags**<br/>
确定是否自动确定字符串长度。 可以是以下值之一：

- AUTO_LENGTH在调用[CSimpleStringT：：释放](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)时自动确定字符串长度。 字符串必须为 null 终止。 默认值。

- SET_LENGTH字符串长度设置时[，CSimpleStringT：：getBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)调用。

### <a name="remarks"></a>备注

为关联的字符串对象创建字符串缓冲区。 在构造过程中[，CSimpleStringT：获取缓冲区](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)或[CSimpleStringT：：获取缓冲区集长度](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)调用。

请注意，复制构造函数是**私有**的。

## <a name="cstrbuftoperator-pcxstr"></a><a name="operator_pcxstr"></a>CStrBufT：：操作员PCXSTR

直接访问作为 C 样式字符串存储在关联字符串对象中的字符。

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>返回值

指向字符串数据的字符指针。

### <a name="remarks"></a>备注

调用此函数以返回指向字符串对象字符缓冲区的指针。 无法使用此指针更改字符串对象的内容。

## <a name="cstrbuftoperator-pxstr"></a><a name="operator_pxstr"></a>CStrBufT：：操作员PXSTR

直接访问作为 C 样式字符串存储在关联字符串对象中的字符。

```
operator PXSTR() throw();
```

### <a name="return-value"></a>返回值

指向字符串数据的字符指针。

### <a name="remarks"></a>备注

调用此函数以返回指向字符串对象字符缓冲区的指针。 开发人员可能会使用此指针更改字符串对象的内容。

## <a name="cstrbuftpcxstr"></a><a name="pcxstr"></a>CStrBufT：:PCXSTR

指向常量字符串的指针。

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

## <a name="cstrbuftpxstr"></a><a name="pxstr"></a>CStrBufT：:PXSTR

指向字符串的指针。

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

## <a name="cstrbuftset_length"></a><a name="set_length"></a>CStrBufT：SET_LENGTH

`GetBuffer`设置字符串对象的时间长度。

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>备注

在 GetBuffer 时间设置字符串对象的长度。

确定在构造字符串缓冲区对象时是否调用[CSimpleStringT：getBufferT](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[CSimpleStringT：getBufferSet 长度](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)。

## <a name="cstrbuftsetlength"></a><a name="setlength"></a>CStrBufT：：设置长度

设置字符缓冲区的长度。

```
void SetLength(int nLength);
```

### <a name="parameters"></a>参数

*n 长度*<br/>
字符串对象的字符缓冲区的新长度。

> [!NOTE]
> 必须小于或等于`CStrBufT`中的构造函数中指定的最小缓冲区长度。

### <a name="remarks"></a>备注

调用此函数以设置缓冲区对象表示的字符串的长度。

## <a name="cstrbuftstringtype"></a><a name="stringtype"></a>CStrBufT：弦类型

其缓冲区将由此类模板的专门化操作的字符串类型。

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>备注

`TCharType`是用于专门化类模板的字符类型。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
