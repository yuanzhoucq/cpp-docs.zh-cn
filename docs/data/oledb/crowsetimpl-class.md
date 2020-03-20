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
ms.openlocfilehash: 9c2e5923fe35287a7586cd4b52bc60e4a5b27b2d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545569"
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

### <a name="parameters"></a>parameters

*T*<br/>
派生自 `CRowsetImpl`的用户的类。

*存储*<br/>
用户记录类。

*CreatorClass*<br/>
包含行集属性的类;通常为命令。

*ArrayType*<br/>
将充当行集数据的存储的类。 此参数默认为 `CAtlArray`，但它可以是支持所需功能的任何类。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[NameFromDBID](#namefromdbid)|从 `DBID` 提取字符串，并将其复制到传入的*bstr* 。|
|[SetCommandText](#setcommandtext)|验证和存储两个字符串中的 `DBID`（[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)）。|

### <a name="overridable-methods"></a>可重写方法

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|检索特定客户端请求的列信息。|
|[GetCommandFromID](#getcommandfromid)|检查是否有一个或两个参数包含字符串值，如果是，则将字符串值复制到[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)的数据成员。|
|[ValidateCommandID](#validatecommandid)|检查是否有一个或两个 `DBID`都包含字符串值，如果是，则将它们复制到其数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_rgRowData](#rgrowdata)|默认情况下，将 templatizes 用户记录模板参数 `CRowsetImpl`的 `CAtlArray`。 可以通过将 `ArrayType` 模板参数更改为 `CRowsetImpl`来使用另一个数组类型类。|
|[m_strCommandText](#strcommandtext)|包含行集的初始命令。|
|[m_strIndexText](#strindextext)|包含行集的初始索引。|

## <a name="remarks"></a>备注

`CRowsetImpl` 提供静态向上转换形式的重写。 方法控制给定行集验证命令文本的方式。 通过使实现接口成为多重继承的，可以创建自己的 `CRowsetImpl`样式类。 您必须为其提供实现的唯一方法是 `Execute`。 根据要创建的行集的类型，creator 方法将需要 `Execute`的不同签名。 例如，如果使用 `CRowsetImpl`派生类实现架构行集，则 `Execute` 方法将具有以下签名：

`HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`

如果要创建 `CRowsetImpl`派生类以实现命令行集或会话的行集，则 `Execute` 方法将具有以下签名：

`HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`

若要实现任何 `CRowsetImpl`派生的 `Execute` 方法，必须填充内部数据缓冲区（[m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)）。

## <a name="crowsetimplnamefromdbid"></a><a name="namefromdbid"></a>CRowsetImpl：： NameFromDBID

从 `DBID` 提取字符串，并将其复制到传入的*bstr* 。

### <a name="syntax"></a>语法

```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,
   CComBSTR& bstr,
   bool bIndex);
```

#### <a name="parameters"></a>parameters

*pDBID*<br/>
中指向要从中提取字符串的 `DBID` 的指针。

*bstr*<br/>
中[CComBSTR](../../atl/reference/ccombstr-class.md)引用，用于放置 `DBID` 字符串的副本。

*bIndex*<br/>
中如果索引 `DBID`，则为**true** ;如果表 `DBID`，则**为 false** 。

### <a name="return-value"></a>返回值

标准的 HRESULT。 根据 `DBID` 是表还是索引（由*bIndex*表示），该方法将返回 DB_E_NOINDEX 或 DB_E_NOTABLE。

### <a name="remarks"></a>备注

此方法由[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)和[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)的 `CRowsetImpl` 实现调用。

## <a name="crowsetimplsetcommandtext"></a><a name="setcommandtext"></a>CRowsetImpl：： SetCommandText

验证和存储两个字符串中的 `DBID`（[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)）。

### <a name="syntax"></a>语法

```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>parameters

*pTableID*<br/>
中指向表示表 ID 的 `DBID` 的指针。

*pIndexID*<br/>
中指向表示索引 ID 的 `DBID` 的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

`SetCommentText` 方法由 `CreateRowset`（`IOpenRowsetImpl`的静态模板化方法）调用。

此方法通过向上转换指针调用[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)和[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)委托其工作。

## <a name="crowsetimplgetcolumninfo"></a><a name="getcolumninfo"></a>CRowsetImpl：： GetColumnInfo

检索特定客户端请求的列信息。

### <a name="syntax"></a>语法

```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,
   ULONG* pcCols);
```

#### <a name="parameters"></a>parameters

*函数*<br/>
中指向用户的 `CRowsetImpl` 派生类的指针。

*pcCols*<br/>
中指向返回的列数的指针（输出）。

### <a name="return-value"></a>返回值

指向静态 `ATLCOLUMNINFO` 结构的指针。

### <a name="remarks"></a>备注

此方法是一种高级重写。

此方法由多个基实现类调用以检索特定客户端请求的列信息。 通常，`IColumnsInfoImpl`会调用此方法。 如果重写此方法，则必须在 `CRowsetImpl`派生类中放置方法的版本。 由于方法可能放在非模板化类中，因此必须将*pv*更改为相应的 `CRowsetImpl`派生类。

下面的示例演示 `GetColumnInfo` 用法。 在此示例中，`CMyRowset` 是 `CRowsetImpl`派生类。 若要重写此类的所有实例的 `GetColumnInfo`，请在 `CMyRowset` 类定义中放置以下方法：

[!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]

## <a name="crowsetimplgetcommandfromid"></a><a name="getcommandfromid"></a>CRowsetImpl：： GetCommandFromID

检查是否有一个或两个参数包含字符串值，如果是，则将字符串值复制到[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)的数据成员。

### <a name="syntax"></a>语法

```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>parameters

*pTableID*<br/>
中指向表示表 ID 的 `DBID` 的指针。

*pIndexID*<br/>
中指向表示索引 ID 的 `DBID` 的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法通过 `CRowsetImpl` 的静态向上传递来调用，以填充[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)的数据成员。 默认情况下，此方法会检查是否有一个或两个参数包含字符串值。 如果这些值包含字符串值，则此方法会将字符串值复制到数据成员。 通过在 `CRowsetImpl`派生类中放置具有此签名的方法，将调用方法，而不是基实现。

## <a name="crowsetimplvalidatecommandid"></a><a name="validatecommandid"></a>CRowsetImpl：： ValidateCommandID

检查是否有一个或两个 `DBID`都包含字符串值，如果是，则将它们复制到其数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。

### <a name="syntax"></a>语法

```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>parameters

*pTableID*<br/>
中指向表示表 ID 的 `DBID` 的指针。

*pIndexID*<br/>
中指向表示索引 ID 的 `DBID` 的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法通过 `CRowsetImpl` 的静态向上传递来调用，以填充其数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。 默认情况下，此方法会检查是否有一个或两个 `DBID`包含字符串值，如果是，则将它们复制到其数据成员。 通过在 `CRowsetImpl`派生类中放置具有此签名的方法，将调用方法，而不是基实现。

## <a name="crowsetimplm_rgrowdata"></a><a name="rgrowdata"></a>CRowsetImpl：： m_rgRowData

默认情况下，将 templatizes 用户记录模板参数 `CRowsetImpl`的 `CAtlArray`。

### <a name="syntax"></a>语法

```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;
```

### <a name="remarks"></a>备注

*ArrayType*是 `CRowsetImpl`的模板参数。

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