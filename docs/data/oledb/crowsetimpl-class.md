---
title: CRowsetImpl 类
ms.date: 11/04/2016
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
- CRowsetImpl::GetCommandFromID
- GetCommandFromID
- CRowsetImpl.GetCommandFromID
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
- CRowsetImpl.m_rgRowData
- CRowsetImpl::m_rgRowData
- CRowsetImpl::m_strCommandText
- CRowsetImpl.m_strCommandText
- CRowsetImpl::m_strIndexText
- CRowsetImpl.m_strIndexText
helpviewer_keywords:
- CRowsetImpl class
- NameFromDBID method
- SetCommandText method
- GetColumnInfo method
- GetCommandFromID method
- ValidateCommandID method
- m_rgRowData
- m_strCommandText
- m_strIndexText
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
ms.openlocfilehash: 35a80503597b7e59ec10618b9c8e18e0e69f018e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221505"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl 类

提供标准 OLE DB 行集实现，无需多次继承多个实现接口。

## <a name="syntax"></a>语法

```cpp
template <
   class T,
   class Storage,
   class CreatorClass,
   class ArrayType = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class RowsetInterface = IRowsetImpl <T, IRowset>
>
class CRowsetImpl :
   public CComObjectRootEx<CreatorClass::_ThreadModel>,
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>
```

### <a name="parameters"></a>参数

*T*<br/>
从派生的用户的类 `CRowsetImpl` 。

*存储*<br/>
用户记录类。

*CreatorClass*<br/>
包含行集属性的类;通常为命令。

*ArrayType*<br/>
将充当行集数据的存储的类。 此参数默认为 `CAtlArray` ，但它可以是支持所需功能的任何类。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[NameFromDBID](#namefromdbid)|从中提取字符串 `DBID` ，并将其复制到传入的*bstr* 。|
|[SetCommandText](#setcommandtext)|验证并将 `DBID` s 存储在两个字符串中（[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)）。|

### <a name="overridable-methods"></a>可重写方法

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|检索特定客户端请求的列信息。|
|[GetCommandFromID](#getcommandfromid)|检查是否有一个或两个参数包含字符串值，如果是，则将字符串值复制到[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)的数据成员。|
|[ValidateCommandID](#validatecommandid)|检查是否有一个或两个 `DBID` 包含字符串值，如果是，则将它们复制到其数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_rgRowData](#rgrowdata)|默认情况下， `CAtlArray` templatizes 的用户记录模板参数 `CRowsetImpl` 。 可以通过将模板参数更改为来使用另一个数组类型类 `ArrayType` `CRowsetImpl` 。|
|[m_strCommandText](#strcommandtext)|包含行集的初始命令。|
|[m_strIndexText](#strindextext)|包含行集的初始索引。|

## <a name="remarks"></a>备注

`CRowsetImpl`提供静态向上转换形式的重写。 方法控制给定行集验证命令文本的方式。 你可以 `CRowsetImpl` 通过使实现接口成为多个继承类来创建自己的类。 必须为其提供实现的唯一方法是 `Execute` 。 根据要创建的行集的类型，creator 方法将需要不同的签名 `Execute` 。 例如，如果使用 `CRowsetImpl` 派生类实现架构行集，则该 `Execute` 方法将具有以下签名：

`HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`

如果要创建 `CRowsetImpl` 派生类以实现命令行集或会话的行集，则该 `Execute` 方法将具有以下签名：

`HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`

若要实现任何 `CRowsetImpl` 派生 `Execute` 方法，必须填充内部数据缓冲区（[m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)）。

## <a name="crowsetimplnamefromdbid"></a><a name="namefromdbid"></a>CRowsetImpl：： NameFromDBID

从中提取字符串 `DBID` ，并将其复制到传入的*bstr* 。

### <a name="syntax"></a>语法

```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,
   CComBSTR& bstr,
   bool bIndex);
```

#### <a name="parameters"></a>参数

*pDBID*<br/>
中一个指针，指向要从中 `DBID` 提取字符串的。

*bstr*<br/>
中用于放置字符串副本的[CComBSTR](../../atl/reference/ccombstr-class.md)引用 `DBID` 。

*bIndex*<br/>
[in] **`true`** 如果为索引 `DBID` ，则为; 如果表为，则为 **`false`** `DBID` 。

### <a name="return-value"></a>返回值

标准的 HRESULT。 `DBID`此方法将返回 DB_E_NOINDEX 或 DB_E_NOTABLE，具体取决于是否为表或索引（由*bIndex*表示）。

### <a name="remarks"></a>备注

此方法由 `CRowsetImpl` [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)和[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)的实现调用。

## <a name="crowsetimplsetcommandtext"></a><a name="setcommandtext"></a>CRowsetImpl：： SetCommandText

验证并将 `DBID` s 存储在两个字符串中（[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)）。

### <a name="syntax"></a>语法

```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>参数

*pTableID*<br/>
中指向 `DBID` 表示表 ID 的的指针。

*pIndexID*<br/>
中指向 `DBID` 表示索引 ID 的的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

`SetCommentText`方法是由 `CreateRowset` 的静态模板化方法调用的 `IOpenRowsetImpl` 。

此方法通过向上转换指针调用[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)和[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)委托其工作。

## <a name="crowsetimplgetcolumninfo"></a><a name="getcolumninfo"></a>CRowsetImpl：： GetColumnInfo

检索特定客户端请求的列信息。

### <a name="syntax"></a>语法

```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,
   ULONG* pcCols);
```

#### <a name="parameters"></a>参数

*函数*<br/>
中指向用户的 `CRowsetImpl` 派生类的指针。

*pcCols*<br/>
中指向返回的列数的指针（输出）。

### <a name="return-value"></a>返回值

指向静态结构的指针 `ATLCOLUMNINFO` 。

### <a name="remarks"></a>备注

此方法是一种高级重写。

此方法由多个基实现类调用以检索特定客户端请求的列信息。 通常，此方法由调用 `IColumnsInfoImpl` 。 如果重写此方法，则必须在派生类中放置方法的版本 `CRowsetImpl` 。 由于方法可能放在非模板化类中，因此必须将*pv*更改为相应的 `CRowsetImpl` 派生类。

下面的示例演示了 `GetColumnInfo` 用法。 在此示例中， `CMyRowset` 是一个 `CRowsetImpl` 派生类。 若要重写 `GetColumnInfo` 此类的所有实例，请在类定义中放置以下方法 `CMyRowset` ：

[!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]

## <a name="crowsetimplgetcommandfromid"></a><a name="getcommandfromid"></a>CRowsetImpl：： GetCommandFromID

检查是否有一个或两个参数包含字符串值，如果是，则将字符串值复制到[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)的数据成员。

### <a name="syntax"></a>语法

```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>参数

*pTableID*<br/>
中指向 `DBID` 表示表 ID 的的指针。

*pIndexID*<br/>
中指向 `DBID` 表示索引 ID 的的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法通过静态向上传递来调用， `CRowsetImpl` 以填充[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)的数据成员。 默认情况下，此方法会检查是否有一个或两个参数包含字符串值。 如果这些值包含字符串值，则此方法会将字符串值复制到数据成员。 通过在派生类中放置具有此签名的方法 `CRowsetImpl` ，将调用方法，而不是基实现。

## <a name="crowsetimplvalidatecommandid"></a><a name="validatecommandid"></a>CRowsetImpl：： ValidateCommandID

检查是否有一个或两个 `DBID` 包含字符串值，如果是，则将它们复制到其数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。

### <a name="syntax"></a>语法

```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>参数

*pTableID*<br/>
中指向 `DBID` 表示表 ID 的的指针。

*pIndexID*<br/>
中指向 `DBID` 表示索引 ID 的的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法通过静态向上传递来调用， `CRowsetImpl` 以填充其数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。 默认情况下，此方法会检查是否有一个或两个 `DBID` 包含字符串值，如果是，则将它们复制到其数据成员。 通过在派生类中放置具有此签名的方法 `CRowsetImpl` ，将调用方法，而不是基实现。

## <a name="crowsetimplm_rgrowdata"></a><a name="rgrowdata"></a>CRowsetImpl：： m_rgRowData

默认情况下， `CAtlArray` templatizes 的用户记录模板参数 `CRowsetImpl` 。

### <a name="syntax"></a>语法

```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;
```

### <a name="remarks"></a>备注

*ArrayType*是的模板参数 `CRowsetImpl` 。

## <a name="crowsetimplm_strcommandtext"></a><a name="strcommandtext"></a>CRowsetImpl：： m_strCommandText

包含行集的初始命令。

### <a name="syntax"></a>语法

```cpp
CComBSTR CRowsetBaseImpl::m_strCommandText;
```

## <a name="crowsetimplm_strindextext"></a><a name="strindextext"></a>CRowsetImpl：： m_strIndexText

包含行集的初始索引。

### <a name="syntax"></a>语法

```cpp
CComBSTR CRowsetBaseImpl::m_strIndexText;
```
