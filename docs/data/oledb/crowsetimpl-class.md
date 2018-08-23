---
title: CRowsetImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
- GetColumnInfo
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1583a5cb6ff67943bde8af530593dff94986d551
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340470"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl 类
提供标准的 OLE DB 行集实现，而无需许多实现接口的多个继承。  
  
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
 *T*  
 用户的类派生自`CRowsetImpl`。  
  
 *存储*  
 用户记录类。  
  
 *CreatorClass*  
 包含为行集; 属性的类通常该命令。  
  
 *ArrayType*  
 将充当用于行集的数据的存储类。 此参数默认为`CAtlArray`，但也可以是任何类都支持所需的功能。  

## <a name="requirements"></a>要求  
 **标头：** atldb.h
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[NameFromDBID](#namefromdbid)|从字符串中提取`DBID`并将其复制到*bstr*中传递。|  
|[SetCommandText](#setcommandtext)|验证，并将存储`DBID`中的两个字符串 ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)并[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md))。|  
  
### <a name="overridable-methods"></a>可重写方法  
  
|||  
|-|-|  
|[GetColumnInfo](#getcolumninfo)|检索特定客户端请求的列信息。|  
|[GetCommandFromID](#getcommandfromid)|检查，如果一个或两个参数包含字符串的值，如果是这样，将字符串值复制到数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)并[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|  
|[ValidateCommandID](#validatecommandid)|检查和 / 或如果，请参阅`DBID`s 包含字符串值，并且如果是这样，则将它们复制到其数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)并[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_rgRowData](#rgrowdata)|默认情况下`CAtlArray`上的用户记录的模板参数的 templatizes `CRowsetImpl`。 可以通过更改使用另一个数组类型类`ArrayType`模板参数`CRowsetImpl`。|  
|[m_strCommandText](#strcommandtext)|包含行集的初始命令。|  
|[m_strIndexText](#strindextext)|包含行集的初始索引。|  
  
## <a name="remarks"></a>备注  
 `CRowsetImpl` 提供静态向上转换的窗体中重写。 方法控制给定行集将在其中验证命令文本的方式。 可以创建你自己`CRowsetImpl`-样式通过使多个继承实现接口的类。 必须为其提供实现的唯一方法`Execute`。 创建者方法将具体取决于要创建哪种类型的行集，需要为不同的签名`Execute`。 例如，如果使用的`CRowsetImpl`的派生类，以实现架构行集，`Execute`方法将具有以下签名：  
  
 `HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`  
  
 如果要创建`CRowsetImpl`的派生类，以实现的命令或会话的行集`Execute`方法将具有以下签名：  
  
 `HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`  
  
 若要实现的任何`CRowsetImpl`的派生`Execute`方法，您必须填充内部数据缓冲区 ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md))。  

## <a name="namefromdbid"></a> Crowsetimpl:: Namefromdbid
从字符串中提取`DBID`并将其复制到*bstr*中传递。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,  
   CComBSTR& bstr,  
   bool bIndex);  
```  
  
#### <a name="parameters"></a>参数  
 *pDBID*  
 [in]一个指向`DBID`要从中提取字符串。  
  
 *bstr*  
 [in]一个[CComBSTR](../../atl/reference/ccombstr-class.md)要存放一份引用`DBID`字符串。  
  
 *bIndex*  
 [in]**，则返回 true**如果索引`DBID`;**false**如果表`DBID`。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT。 具体取决于是否`DBID`表或索引 (为由*bIndex*)，该方法将返回 DB_E_NOINDEX 或 DB_E_NOTABLE。  
  
### <a name="remarks"></a>备注  
 调用此方法`CRowsetImpl`的实现[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)并[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)。 
  
## <a name="setcommandtext"></a> Crowsetimpl:: Setcommandtext
验证，并将存储`DBID`中的两个字符串 ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)并[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md))。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>参数  
 *pTableID*  
 [in]一个指向`DBID`表示表 id。  
  
 *pIndexID*  
 [in]一个指向`DBID`表示索引 id。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT。  
  
### <a name="remarks"></a>备注  
 `SetCommentText`调用方法`CreateRowset`，静态模板化的方法`IOpenRowsetImpl`。  
  
 此方法将其工作委托通过调用[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)并[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)通过一个向上转换的指针。 

## <a name="getcolumninfo"></a> Crowsetimpl:: Getcolumninfo
检索特定客户端请求的列信息。  
  
### <a name="syntax"></a>语法  
  
```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,  
   ULONG* pcCols);  
```  
  
#### <a name="parameters"></a>参数  
 *pv*  
 [in]指向用户的`CRowsetImpl`派生的类。  
  
 *pcCols*  
 [in]返回列的指针 （输出） 的数字。  
  
### <a name="return-value"></a>返回值  
 指向静态`ATLCOLUMNINFO`结构。  
  
### <a name="remarks"></a>备注  
 此方法是高级重写。  
  
 若要为特定的客户端请求检索列信息的多个基实现类调用此方法。 通常情况下，将调用此方法`IColumnsInfoImpl`。 如果重写此方法，必须将放在方法的版本在`CRowsetImpl`-派生的类。 因为该方法将会放入非模板化类，则必须更改*pv*到适当`CRowsetImpl`-派生的类。  
  
 下面的示例演示`GetColumnInfo`使用情况。 在此示例中，`CMyRowset`是`CRowsetImpl`-派生的类。 若要重写`GetColumnInfo`的此类的所有实例，将都放置中的以下方法`CMyRowset`类定义：  
  
 [!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]  

## <a name="getcommandfromid"></a> Crowsetimpl:: Getcommandfromid
检查，如果一个或两个参数包含字符串的值，如果是这样，将字符串值复制到数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)并[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>参数  
 *pTableID*  
 [in]一个指向`DBID`表示表的 id。  
  
 *pIndexID*  
 [in]一个指向`DBID`表示索引的 id。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT。  
  
### <a name="remarks"></a>备注  
 调用此方法通过由静态向上`CRowsetImpl`填充的数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)并[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。 默认情况下，此方法检查，查阅其中一种或这两个参数是否包含字符串值。 如果它们包含字符串值，此方法将字符串值复制到的数据成员。 通过将放置具有此签名中的方法在`CRowsetImpl`-派生的类，而不是基实现将调用您的方法。 

## <a name="validatecommandid"></a> Crowsetimpl:: Validatecommandid
检查和 / 或如果，请参阅`DBID`s 包含字符串值，并且如果是这样，则将它们复制到其数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)并[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>参数  
 *pTableID*  
 [in]一个指向`DBID`表示表 id。  
  
 *pIndexID*  
 [in]一个指向`DBID`表示索引 id。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT。  
  
### <a name="remarks"></a>备注  
 调用此方法通过由静态向上`CRowsetImpl`填充其数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)并[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。 默认情况下，此方法检查和 / 或如果，请参阅`DBID`s 包含字符串值，并且如果是这样，则将它们复制到其数据成员。 通过将放置具有此签名中的方法在`CRowsetImpl`-派生的类，而不是基实现将调用您的方法。  

## <a name="rgrowdata"></a> Crowsetimpl:: M_rgrowdata
默认情况下`CAtlArray`上的用户记录的模板参数的 templatizes `CRowsetImpl`。  
  
### <a name="syntax"></a>语法  
  
```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;  
```  
  
### <a name="remarks"></a>备注  
 *ArrayType*为模板参数`CRowsetImpl`。  

## <a name="strcommandtext"></a> Crowsetimpl:: M_strcommandtext
包含行集的初始命令。  
  
### <a name="syntax"></a>语法  
  
```cpp
CComBSTR CRowsetBaseImpl::m_strCommandText;  
```  

## <a name="strindextext"></a> Crowsetimpl:: M_strindextext
包含行集的初始索引。  
  
### <a name="syntax"></a>语法  
  
```cpp
CComBSTR CRowsetBaseImpl::m_strIndexText;  
``` 