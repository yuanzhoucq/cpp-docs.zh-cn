---
title: CComSafeArray 类
ms.date: 05/06/2019
f1_keywords:
- CComSafeArray
- ATLSAFE/ATL::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::Add
- ATLSAFE/ATL::CComSafeArray::Attach
- ATLSAFE/ATL::CComSafeArray::CopyFrom
- ATLSAFE/ATL::CComSafeArray::CopyTo
- ATLSAFE/ATL::CComSafeArray::Create
- ATLSAFE/ATL::CComSafeArray::Destroy
- ATLSAFE/ATL::CComSafeArray::Detach
- ATLSAFE/ATL::CComSafeArray::GetAt
- ATLSAFE/ATL::CComSafeArray::GetCount
- ATLSAFE/ATL::CComSafeArray::GetDimensions
- ATLSAFE/ATL::CComSafeArray::GetLowerBound
- ATLSAFE/ATL::CComSafeArray::GetSafeArrayPtr
- ATLSAFE/ATL::CComSafeArray::GetType
- ATLSAFE/ATL::CComSafeArray::GetUpperBound
- ATLSAFE/ATL::CComSafeArray::IsSizable
- ATLSAFE/ATL::CComSafeArray::MultiDimGetAt
- ATLSAFE/ATL::CComSafeArray::MultiDimSetAt
- ATLSAFE/ATL::CComSafeArray::Resize
- ATLSAFE/ATL::CComSafeArray::SetAt
- ATLSAFE/ATL::CComSafeArray::m_psa
helpviewer_keywords:
- CComSafeArray class
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
ms.openlocfilehash: d1e72d364858ea31541d574ed77bdc8ccca7d748
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327391"
---
# <a name="ccomsafearray-class"></a>CComSafeArray 类

此类是结构的`SAFEARRAY`包装器。

## <a name="syntax"></a>语法

```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在数组中的数据类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComSafearray：CComSafearray](#ccomsafearray)|构造函数。|
|[CComSafearray：*CComSafearray](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComSafearray：添加](#add)|将一个或多个元素或`SAFEARRAY`结构添加到 。 `CComSafeArray`|
|[CComSafearray：附加](#attach)|将`SAFEARRAY`结构附加到`CComSafeArray`对象。|
|[CComSafearray：：从](#copyfrom)|将`SAFEARRAY`结构的内容复制到对象中`CComSafeArray`。|
|[CComSafearray：：复制到](#copyto)|创建 `CComSafeArray` 对象的副本。|
|[CComSafeArray::Create](#create)|创建一个 `CComSafeArray` 对象。|
|[CComSafeArray::Destroy](#destroy)|销毁 `CComSafeArray` 对象。|
|[CComSafearray：:D](#detach)|从`CComSafeArray`对象分离`SAFEARRAY`。|
|[CComSafearray：GetAt](#getat)|从一维数组中检索单个元素。|
|[CComSafearray：获取计数](#getcount)|返回数组中的元素数目。|
|[CComSafearray：获取维度](#getdimensions)|返回数组中的维数。|
|[CComSafearray：获取下限](#getlowerbound)|返回数组给定维度的下限。|
|[CComSafearray：获取安全阵列](#getsafearrayptr)|返回 `m_psa` 数据成员的地址。|
|[CComSafearray：获取类型](#gettype)|返回数组中存储的数据类型。|
|[CComSafearray：获取上部](#getupperbound)|返回数组任意维度的上限。|
|[CComSafearray：：可比](#issizable)|测试是否可重设 `CComSafeArray` 对象的大小。|
|[CComSafearray：：多迪姆格拉特](#multidimgetat)|从多维数组中检索单个元素。|
|[CComSafearray：：多迪姆塞特](#multidimsetat)|设置多维数组中元素的值。|
|[CComSafearray：调整大小](#resize)|重设 `CComSafeArray` 对象的大小。|
|[CComSafearray：：Setat](#setat)|设置一维数组中元素的值。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CComSafearray：：操作员LPSAFEARRAY](#operator_lpsafearray)|将值强制转换为`SAFEARRAY`指针。|
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|从数组中检索元素。|
|[CComSafeArray：：操作员 |](#operator_eq)|赋值运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CComSafearray：m_psa](#m_psa)|此数据成员保存结构的地址`SAFEARRAY`。|

## <a name="remarks"></a>备注

`CComSafeArray`为[SAFEARRAY 数据类型](/windows/win32/api/oaidl/ns-oaidl-safearray)类提供了包装器，因此创建和管理几乎任何受 VARIANT 支持类型的单和多维数组非常简单。

`CComSafeArray` 可简化数组在进程之间的传递，此外还可以对照上限和下限检查数组索引值，从而提供额外的安全性。

`CComSafeArray` 的下限可以从任何用户定义值开始；但是，通过 C++ 访问的数组应该使用下限 0。 Visual Basic 等其他语言可以使用其他边界值（例如，-10 到 10）。

使用 [CComSafeArray::Create](#create) 可以创建 `CComSafeArray` 对象，使用 [CComSafeArray::Destroy](#destroy) 可将其删除。

`CComSafeArray` 可以包含以下 VARIANT 数据类型子集：

|VARTYPE|说明|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|字节|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglong|
|VT_R4|FLOAT|
|VT_R8|double|
|VT_DECIMAL|十进制指针|
|VT_VARIANT|变体指针|
|VT_CY|货币数据类型|

## <a name="requirements"></a>要求

**标头：** atlsafe.h

## <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]

## <a name="ccomsafearrayadd"></a><a name="add"></a>CComSafearray：添加

将一个或多个元素或`SAFEARRAY`结构添加到 。 `CComSafeArray`

```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>参数

*普萨斯克*<br/>
一个指向 `SAFEARRAY` 对象的指针。

*ulCount*<br/>
要添加到数组的对象数。

*铂*<br/>
指向要添加到数组的一个或多个对象的指针。

*t*<br/>
对要添加到数组的对象的引用。

*bCopy*<br/>
指示是否应创建数据的副本。 默认值为 TRUE。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

新对象将追加到现有`SAFEARRAY`对象的末尾。 不支持将对象添加到多维`SAFEARRAY`对象。 添加现有对象数组时，两个数组必须包含相同类型的元素。

当将 BSTR 类型或 VARIANT 的元素添加到数组时，将考虑*bCopy*标志。 TRUE 的默认值可确保在元素添加到数组时对数据进行新副本。

## <a name="ccomsafearrayattach"></a><a name="attach"></a>CComSafearray：附加

将`SAFEARRAY`结构附加到`CComSafeArray`对象。

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>参数

*普萨斯克*<br/>
指向结构的`SAFEARRAY`指针。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

将`SAFEARRAY`结构附加到`CComSafeArray`对象，使现有`CComSafeArray`方法可用。

## <a name="ccomsafearrayccomsafearray"></a><a name="ccomsafearray"></a>CComSafearray：CComSafearray

构造函数。

```
CComSafeArray();
CComSafeArray(const SAFEARRAYBOUND& bound);
CComSafeArray(ULONG  ulCount, LONG lLBound = 0);
CComSafeArray(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
CComSafeArray(const CComSafeArray& saSrc);
CComSafeArray(const SAFEARRAY& saSrc);
CComSafeArray(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>参数

*绑定*<br/>
`SAFEARRAYBOUND` 结构。

*ulCount*<br/>
数组中的元素数。

*lLBound*<br/>
下限值;即数组中第一个元素的索引。

*p绑定*<br/>
指向结构的`SAFEARRAYBOUND`指针。

*乌迪姆*<br/>
数组中的维度计数。

*萨斯尔克*<br/>
对`SAFEARRAY`结构或`CComSafeArray`对象的引用。 在这两种情况下，构造函数都使用此引用来创建数组的副本，因此在构造后不会引用数组。

*普萨斯克*<br/>
指向结构的`SAFEARRAY`指针。 构造函数使用此地址创建数组的副本，因此在构造后不会引用数组。

### <a name="remarks"></a>备注

创建一个 `CComSafeArray` 对象。

## <a name="ccomsafearrayccomsafearray"></a><a name="dtor"></a>CComSafearray：*CComSafearray

析构函数。

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>备注

释放所有分配的资源。

## <a name="ccomsafearraycopyfrom"></a><a name="copyfrom"></a>CComSafearray：：从

将`SAFEARRAY`结构的内容复制到对象中`CComSafeArray`。

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>参数

*ppArray*<br/>
指针`SAFEARRAY`到 要复制。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

此方法将 的内容`SAFEARRAY`复制到当前`CComSafeArray`对象中。 将替换数组的现有内容。

## <a name="ccomsafearraycopyto"></a><a name="copyto"></a>CComSafearray：：复制到

创建 `CComSafeArray` 对象的副本。

```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>参数

*ppArray*<br/>
指向要在其中创建新`SAFEARRAY`位置的位置的指针。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

此方法将`CComSafeArray`对象的内容复制到结构中`SAFEARRAY`。

## <a name="ccomsafearraycreate"></a><a name="create"></a>CComSafearray：创建

创建一个 `CComSafeArray`。

```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```

### <a name="parameters"></a>参数

*p绑定*<br/>
一个指向 `SAFEARRAYBOUND` 对象的指针。

*乌迪姆*<br/>
数组的维数。

*ulCount*<br/>
数组中的元素数。

*lLBound*<br/>
下限值;即数组中第一个元素的索引。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

可以从`CComSafeArray`现有`SAFEARRAYBOUND`结构和维度数创建对象，或者通过指定数组中的元素数和下限。 如果要从C++访问数组，下限应为 0。 其他语言可能允许下限的其他值（例如，Visual Basic 支持具有元素的数组，范围为 -10 到 10）。

## <a name="ccomsafearraydestroy"></a><a name="destroy"></a>CComSafeArray：:D

销毁 `CComSafeArray` 对象。

```
HRESULT Destroy();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

销毁现有`CComSafeArray`对象及其包含的所有数据。

## <a name="ccomsafearraydetach"></a><a name="detach"></a>CComSafearray：:D

从`CComSafeArray`对象分离`SAFEARRAY`。

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>返回值

返回指向`SAFEARRAY`对象的指针。

### <a name="remarks"></a>备注

此方法将`SAFEARRAY`对象从`CComSafeArray`对象中分离出来。

## <a name="ccomsafearraygetat"></a><a name="getat"></a>CComSafearray：GetAt

从一维数组中检索单个元素。

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>参数

*lIndex*<br/>
要返回的数组中值的索引编号。

### <a name="return-value"></a>返回值

返回对所需数组元素的引用。

## <a name="ccomsafearraygetcount"></a><a name="getcount"></a>CComSafearray：获取计数

返回数组中的元素数目。

```
ULONG GetCount(UINT uDim = 0) const;
```

### <a name="parameters"></a>参数

*乌迪姆*<br/>
数组维度。

### <a name="return-value"></a>返回值

返回数组中的元素数目。

### <a name="remarks"></a>备注

当与多维数组一起使用时，此方法将仅返回特定维度中的元素数。

## <a name="ccomsafearraygetdimensions"></a><a name="getdimensions"></a>CComSafearray：获取维度

返回数组中的维数。

```
UINT GetDimensions() const;
```

### <a name="return-value"></a>返回值

返回数组中的维数。

## <a name="ccomsafearraygetlowerbound"></a><a name="getlowerbound"></a>CComSafearray：获取下限

返回数组给定维度的下限。

```
LONG GetLowerBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>参数

*乌迪姆*<br/>
要为其获取下限的数组维度。 如果省略，默认值为 0。

### <a name="return-value"></a>返回值

返回下限。

### <a name="remarks"></a>备注

如果下限为 0，则表示第一个元素为元素 0 的 C 样数组。 例如，如果出现错误，此方法调用`AtlThrow`HRESULT 来描述错误。

## <a name="ccomsafearraygetsafearrayptr"></a><a name="getsafearrayptr"></a>CComSafearray：获取安全阵列

返回 `m_psa` 数据成员的地址。

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>返回值

返回指向[CComSafeArray：：m_psa](#m_psa)数据成员的指针。

## <a name="ccomsafearraygettype"></a><a name="gettype"></a>CComSafearray：获取类型

返回数组中存储的数据类型。

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>返回值

返回存储在数组中的数据类型，可以是以下任一类型：

|VARTYPE|说明|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|字节|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglong|
|VT_R4|FLOAT|
|VT_R8|double|
|VT_DECIMAL|十进制指针|
|VT_VARIANT|变体指针|
|VT_CY|货币数据类型|

## <a name="ccomsafearraygetupperbound"></a><a name="getupperbound"></a>CComSafearray：获取上部

返回数组任意维度的上限。

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>参数

*乌迪姆*<br/>
要为其获取上限的数组维度。 如果省略，默认值为 0。

### <a name="return-value"></a>返回值

返回上边界。 此值是包含的，此维度的最大有效索引。

### <a name="remarks"></a>备注

例如，如果出现错误，此方法调用`AtlThrow`HRESULT 来描述错误。

## <a name="ccomsafearrayissizable"></a><a name="issizable"></a>CComSafearray：：可比

测试是否可重设 `CComSafeArray` 对象的大小。

```
bool IsSizable() const;
```

### <a name="return-value"></a>返回值

如果 可以调整`CComSafeArray`大小，则返回 TRUE，如果无法返回 FALSE。

## <a name="ccomsafearraym_psa"></a><a name="m_psa"></a>CComSafearray：m_psa

保存访问的结构的地址`SAFEARRAY`。

```
LPSAFEARRAY m_psa;
```

## <a name="ccomsafearraymultidimgetat"></a><a name="multidimgetat"></a>CComSafearray：：多迪姆格拉特

从多维数组中检索单个元素。

```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```

### <a name="parameters"></a>参数

*阿尔指数*<br/>
指向数组中每个维度的索引矢量。 最左侧（最重要的）维度是`alIndex[0]`。

*t*<br/>
对返回的数据的引用。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="ccomsafearraymultidimsetat"></a><a name="multidimsetat"></a>CComSafearray：：多迪姆塞特

设置多维数组中元素的值。

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>参数

*阿尔指数*<br/>
指向数组中每个维度的索引矢量。 最右侧（最不显著）的维度是`alIndex`{0}。

*T*<br/>
指定新元素的值。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

这是[CComSafearray](#setat)的多维版本：setAt 。

## <a name="ccomsafearrayoperator-"></a><a name="operator_at"></a>CComSafeArray：：操作员\[\]

从数组中检索元素。

```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```

### <a name="parameters"></a>参数

*lIndex， nIndex*<br/>
数组中所需元素的索引编号。

### <a name="return-value"></a>返回值

返回相应的数组元素。

### <a name="remarks"></a>备注

执行与[CComSafeArray：：getAt](#getat)类似的功能，但是此运算符仅适用于单维数组。

## <a name="ccomsafearrayoperator-"></a><a name="operator_eq"></a>CComSafeArray：：操作员 |

赋值运算符。

```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>参数

*萨斯尔克*<br/>
对 `CComSafeArray` 对象的引用。

*普萨斯克*<br/>
一个指向 `SAFEARRAY` 对象的指针。

### <a name="return-value"></a>返回值

返回数组中存储的数据类型。

## <a name="ccomsafearrayoperator-lpsafearray"></a><a name="operator_lpsafearray"></a>CComSafearray：：操作员LPSAFEARRAY

将值强制转换为`SAFEARRAY`指针。

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>返回值

将值强制转换为`SAFEARRAY`指针。

## <a name="ccomsafearrayresize"></a><a name="resize"></a>CComSafearray：调整大小

重设 `CComSafeArray` 对象的大小。

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>参数

*p绑定*<br/>
指向`SAFEARRAYBOUND`包含有关元素数和数组下限的信息的结构的指针。

*ulCount*<br/>
调整数组中请求的对象数。

*lLBound*<br/>
下限。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

此方法仅调整最右侧维度的大小。 它不会调整返回`IsResizable`为 FALSE 的数组的大小。

## <a name="ccomsafearraysetat"></a><a name="setat"></a>CComSafearray：：Setat

设置一维数组中元素的值。

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>参数

*lIndex*<br/>
要设置的数组元素的索引编号。

*t*<br/>
已指定元素的新值。

*bCopy*<br/>
指示是否应创建数据的副本。 默认值为 TRUE。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

当将 BSTR 类型或 VARIANT 的元素添加到数组时，将考虑*bCopy*标志。 TRUE 的默认值可确保在元素添加到数组时对数据进行新副本。

## <a name="see-also"></a>另请参阅

[SAFEARRAY Data Type](/windows/win32/api/oaidl/ns-oaidl-safearray)<br/>
[CComSafeArray::Create](#create)<br/>
[CComSafeArray::Destroy](#destroy)<br/>
[类概述](../../atl/atl-class-overview.md)
