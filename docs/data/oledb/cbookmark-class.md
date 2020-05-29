---
title: CBookmark 类
ms.date: 11/04/2016
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
- ATL.CBookmark<0>.GetBuffer
- ATL.CBookmark.GetBuffer
- ATL::CBookmark<0>::GetBuffer
- ATL::CBookmark::GetBuffer
- CBookmark.GetBuffer
- ATL::CBookmark<nSize>::GetBuffer
- ATL.CBookmark<nSize>.GetBuffer
- CBookmark<0>.GetBuffer
- CBookmark<nSize>::GetBuffer
- CBookmark<0>::GetBuffer
- CBookmark<nSize>.GetBuffer
- CBookmark::GetBuffer
- CBookmark::GetSize
- ATL.CBookmark<nSize>.GetSize
- CBookmark<nSize>.GetSize
- CBookmark.GetSize
- ATL::CBookmark::GetSize
- CBookmark<0>::GetSize
- ATL::CBookmark<nSize>::GetSize
- ATL.CBookmark<0>.GetSize
- ATL::CBookmark<0>::GetSize
- ATL.CBookmark.GetSize
- CBookmark<0>.GetSize
- CBookmark<nSize>::GetSize
- CBookmark<0>::SetBookmark
- ATL.CBookmark<0>.SetBookmark
- CBookmark<0>.SetBookmark
- SetBookmark
- ATL::CBookmark::SetBookmark
- ATL::CBookmark<0>::SetBookmark
- CBookmark.SetBookmark
- ATL.CBookmark.SetBookmark
- CBookmark::SetBookmark
- CBookmark<0>::operator=
- CBookmark<0>.operator=
- ATL.CBookmark.operator=
- CBookmark::operator=
- ATL.CBookmark<0>.operator=
- ATL::CBookmark<0>::operator=
- CBookmark.operator=
- ATL::CBookmark::operator=
helpviewer_keywords:
- CBookmark class
- CBookmark class, constructor
- GetBuffer method
- GetSize method
- SetBookmark method
- = operator, with OLE DB templates
- operator =, bookmarks
- operator=, bookmarks
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
ms.openlocfilehash: d3d82ea09b7ed2c1cbaf325906b4f9b480e1eb4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359332"
---
# <a name="cbookmark-class"></a>CBookmark 类

在其缓冲区中保存书签值。

## <a name="syntax"></a>语法

```cpp
template < DBLENGTH nSize = 0 >
class CBookmark : public CBookmarkBase

template <>
class CBookmark< 0 > : public CBookmarkBase
```

### <a name="parameters"></a>参数

*nSize*<br/>
书签缓冲区的大小（以字节为单位）。 当*nSize*为零时，将在运行时动态创建书签缓冲区。

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[CBook标志](#cbookmark)|构造函数|
|[GetBuffer](#getbuffer)|检索指向缓冲区的指针。|
|[GetSize](#getsize)|检索以字节为单位的缓冲区大小。|
|[设置书签](#setbookmark)|设置书签值。|

### <a name="operators"></a>运算符

|||
|-|-|
|[运算符 |](#operator)|将一个`CBookmark`类分配给另一个类。|

## <a name="remarks"></a>备注

`CBookmark<0>`是 模板专业化的`CBookmark`。其缓冲区在运行时动态创建。

## <a name="cbookmarkcbookmark"></a><a name="cbookmark"></a>CBook标志：：CBookmark

构造函数。

### <a name="syntax"></a>语法

```cpp
CBookmark();
CBookmark(DBLENGTH nSize);
```

#### <a name="parameters"></a>参数

*nSize*<br/>
[in] 书签缓冲区的大小（以字节为单位）。

### <a name="remarks"></a>备注

第一个函数将缓冲区设置为 NULL 并将缓冲区大小设置为 0。 第二个函数将缓冲区大小设置为*nSize，* 将缓冲区设置为*nSize*字节的字节数组。

> [!NOTE]
> 此功能仅在 中`CBookmark<0>`可用。

## <a name="cbookmarkgetbuffer"></a><a name="getbuffer"></a>CBook标志：获取缓冲区

检索指向书签缓冲区的指针。

### <a name="syntax"></a>语法

```cpp
virtual BYTE* GetBuffer() const throw();
```

### <a name="return-value"></a>返回值

指向书签缓冲区的指针。

## <a name="cbookmarkgetsize"></a><a name="getsize"></a>CBook标志：获取 Size

检索书签缓冲区的大小。

### <a name="syntax"></a>语法

```cpp
virtual DBLENGTH GetSize() const throw();
```

### <a name="return-value"></a>返回值

缓冲区的大小（以字节为单位）。

## <a name="cbookmarksetbookmark"></a><a name="setbookmark"></a>CBook标志：：设置书签

将*pBuffer*引用的书签值复制到缓冲区`CBookmark`，并将缓冲区大小设置为*nSize*。

### <a name="syntax"></a>语法

```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();
```

#### <a name="parameters"></a>参数

*nSize*<br/>
[在]书签缓冲区的大小。

*pBuffer*<br/>
[在]指向包含书签值的字节数组的指针。

### <a name="return-value"></a>返回值

标准 HRESULT。

### <a name="remarks"></a>备注

此功能仅在 中`CBookmark<0>`可用。

## <a name="cbookmarkoperator-"></a><a name="operator"></a>CBook标志：：运算符 |

将一个 `CBookmark` 对象分配给其他对象。

### <a name="syntax"></a>语法

```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();
```

### <a name="remarks"></a>备注

此运算符仅在 中`CBookmark<0>`才需要。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)
