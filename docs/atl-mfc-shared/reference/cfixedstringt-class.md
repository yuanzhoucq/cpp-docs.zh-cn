---
title: CFixedStringT 类
ms.date: 03/27/2019
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
ms.openlocfilehash: fe096185f6f0b71ad45757cd0b75ab13c41e5f5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317831"
---
# <a name="cfixedstringt-class"></a>CFixedStringT 类

此类表示具有固定字符缓冲区的字符串对象。

## <a name="syntax"></a>语法

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>参数

*字符串类型*<br/>
用作固定字符串对象的基类，可以是任何`CStringT`基于的类型。 一些示例`CString`包括`CStringA`和`CStringW`。

*t_nChars*<br/>
缓冲区中存储的字符数。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CFixedStringT：CFixedStringT](#cfixedstringt)|字符串对象的构造函数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CFixedStringT：：运算符 |](#operator_eq)|为`CFixedStringT`对象分配新值。|

## <a name="remarks"></a>备注

此类是基于 的自定义字符串类的示例`CStringT`。 虽然相似，但两个类在实现上有所不同。 和 之间的`CFixedStringT``CStringT`主要区别是：

- 初始字符缓冲区作为对象的一部分分配，并且具有*大小t_nChars*。 这允许`CFixedString`对象出于性能目的占用连续内存块。 但是，如果`CFixedStringT`对象的内容增长到*超出t_nChars，* 则缓冲区将动态分配。

- `CFixedStringT`对象的字符缓冲区的长度始终相同 *（t_nChars*）。 `CStringT`对象的缓冲区大小没有限制。

- 的`CFixedStringT`内存管理器是自定义的，因此不允许在两个或多个`CFixedStringT`对象之间共享[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)对象。 `CStringT`对象没有此限制。

有关字符串对象的自定义`CFixedStringT`和内存管理的详细信息，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IAtlStringMgr`

`StringType`

`CFixedStringMgr`

`CFixedStringT`

## <a name="requirements"></a>要求

**标题：** cstringt.h

## <a name="cfixedstringtcfixedstringt"></a><a name="cfixedstringt"></a>CFixedStringT：CFixedStringT

构造 `CFixedStringT` 对象。

```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT(const StringType& strSrc);
CFixedStringT(const StringType::XCHAR* pszSrc);
explicit CFixedStringT(const StringType::YCHAR* pszSrc);
explicit CFixedStringT(const unsigned char* pszSrc);
```

### <a name="parameters"></a>参数

*皮茨斯尔克*<br/>
要复制到此`CFixedStringT`对象的 null 终止字符串。

*斯特斯尔克*<br/>
要复制到`CFixedStringT`此`CFixedStringT`对象的现有对象。

*普斯特林姆格*<br/>
指向对象的内存管理器的`CFixedStringT`指针。 有关 的详细信息`IAtlStringMgr`和内存管理`CFixedStringT`，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

### <a name="remarks"></a>备注

由于构造函数将输入数据复制到新的分配存储中，因此您应该注意可能会出现内存异常。 其中一些构造函数充当转换函数。

## <a name="cfixedstringtoperator-"></a><a name="operator_eq"></a>CFixedStringT：：运算符 |

使用新数据重新初始化`CFixedStringT`现有对象。

```
CFixedStringT<StringType, t_nChars>& operator=(
    const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT<StringType, t_nChars>& operator=(const char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& strSrc);
```

### <a name="parameters"></a>参数

*皮茨斯尔克*<br/>
要复制到此`CFixedStringT`对象的 null 终止字符串。

*斯特斯尔克*<br/>
要复制到`CFixedStringT`此`CFixedStringT`对象的现有。

### <a name="remarks"></a>备注

您应该注意，每当使用赋值运算符时，都可能发生内存异常，因为通常分配新存储来保存生成的`CFixedStringT`对象。

## <a name="see-also"></a>另请参阅

[CStringT 类](../../atl-mfc-shared/reference/cstringt-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
