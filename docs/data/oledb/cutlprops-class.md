---
title: CUtlProps 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CUtlProps
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
- CUtlProps
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
- SetPropValue
- ATL::CUtlProps<T>::SetPropValue
- ATL.CUtlProps<T>.SetPropValue
- ATL.CUtlProps.SetPropValue
- CUtlProps::SetPropValue
- CUtlProps<T>::SetPropValue
- CUtlProps.SetPropValue
- CUtlProps<T>.SetPropValue
- ATL::CUtlProps::SetPropValue
dev_langs:
- C++
helpviewer_keywords:
- CUtlProps class
- GetPropValue method
- IsValidValue method
- OnInterfaceRequested method
- OnPropertyChanged method
- SetPropValue method
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 661ac13acd1d8eac0ecde9af9fa08875b99153e3
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39336975"
---
# <a name="cutlprops-class"></a>CUtlProps 类
实现多个 OLE DB 属性接口的属性 (例如， `IDBProperties`， `IDBProperties`，和`IRowsetInfo`)。  
  
## <a name="syntax"></a>语法

```cpp
template < class T >  
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase  
```  
  
### <a name="parameters"></a>参数  
 *T*  
 包含的类`BEGIN_PROPSET_MAP`。  

## <a name="requirements"></a>要求  
 **标头：** atldb.h  

## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetPropValue](#getpropvalue)|从属性集获取的属性。|  
|[IsValidValue](#isvalidvalue)|用于设置属性之前验证值。|  
|[OnInterfaceRequested](#oninterfacerequested)|使用者对象创建接口上调用的方法时，处理请求的可选接口。|  
|[OnPropertyChanged](#onpropertychanged)|设置要处理所链接的属性的属性后调用。|  
|[SetPropValue](#setpropvalue)|在属性集中设置一个属性。|  
  
## <a name="remarks"></a>备注  
 此类大部分是实现详细信息。  
  
 `CUtlProps` 在内部设置的属性包含两个成员： [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md)并[SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)。  
  
 属性集映射中使用的宏的详细信息，请参阅[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)并[END_PROPSET_MAP](../../data/oledb/end-propset-map.md)。  
  
## <a name="getpropvalue"></a> Cutlprops:: Getpropvalue
从属性集获取的属性。  
  
### <a name="syntax"></a>语法  
  
```cpp
OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,  
   DBPROPID dwPropId,  
   VARIANT* pvValue);  
```  
  
#### <a name="parameters"></a>参数  
 *pguidPropSet*  
 [in]属性集的 GUID。  
  
 *dwPropId*  
 [in]属性索引。  
  
 *pvValue*  
 [out]指向一个变量，该包含新属性值的指针。  
  
### <a name="return-value"></a>返回值  
 `Failure` 在出现故障，如果成功，则为 S_OK。

## <a name="isvalidvalue"></a> Cutlprops:: Isvalidvalue
用于设置属性之前验证值。  
  
### <a name="syntax"></a>语法  
  
```cpp
virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,  
   DBPROP* pDBProp);  
```  
  
#### <a name="parameters"></a>参数  
 *iCurSet*  
 属性集数组; 中的索引如果只有一个属性集，则为零。  
  
 *pDBProp*  
 属性 ID 和中的新值[DBPROP](https://msdn.microsoft.com/library/ms717970.aspx)结构。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT。 默认返回值为 S_OK。  
  
### <a name="remarks"></a>备注  
 如果你想要运行上一个值，您将要使用将属性设置任何验证例程，应重写此函数。 例如，您可以验证 DBPROP_AUTH_PASSWORD 针对密码表来确定有效的值。 

## <a name="oninterfacerequested"></a> Cutlprops:: Oninterfacerequested
处理请求的可选接口，使用者调用的方法时对象之一上创建接口。  
  
### <a name="syntax"></a>语法  
  
```cpp
virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);  
```  
  
#### <a name="parameters"></a>参数  
 *riid*  
 [in]所请求的接口的 IID。 有关更多详细信息，请参阅的说明*riid*的参数`ICommand::Execute`中*OLE DB 程序员参考*(中*MDAC SDK*)。  
  
### <a name="remarks"></a>备注  
 `OnInterfaceRequested` 使用者调用的方法时对象之一上创建接口处理的可选接口的使用者请求 (如`IDBCreateSession`， `IDBCreateCommand`， `IOpenRowset`，或`ICommand`)。 它设置为所请求的接口对应的 OLE DB 属性。 例如，如果使用者请求`IID_IRowsetLocate`，`OnInterfaceRequested`设置`DBPROP_IRowsetLocate`接口。 执行此操作在行集创建期间维护正确的状态。  
  
 当使用者调用时调用此方法`IOpenRowset::OpenRowset`或`ICommand::Execute`。  
  
 如果使用者将打开一个对象，并请求的可选接口，该提供程序应设置为 variant_true，则该接口与相关联的属性。 若要允许在特定于属性处理`OnInterfaceRequested`之前的提供程序，将调用`Execute`调用方法。 默认情况下，`OnInterfaceRequested`处理以下接口：  
  
-   `IRowsetLocate`  
  
-   `IRowsetChange`  
  
-   `IRowsetUpdate`  
  
-   `IConnectionPointContainer`  
  
-   `IRowsetScroll`  
  
 如果你想要处理其他接口，重写过程函数在数据源、 会话、 命令或行集类中的此函数。 重写应经过正常设置/获取属性接口，以确保，设置属性还将设置链接的任何属性 (请参阅[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md))。  

## <a name="onpropertychanged"></a> Cutlprops:: Onpropertychanged
设置要处理所链接的属性的属性后调用。  
  
### <a name="syntax"></a>语法  
  
```cpp
virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,  
   DBPROP* pDBProp);  
```  
  
#### <a name="parameters"></a>参数  
 *iCurSet*  
 属性集数组; 中的索引如果只有一个属性集，则为零。  
  
 *pDBProp*  
 属性 ID 和中的新值[DBPROP](https://msdn.microsoft.com/library/ms717970.aspx)结构。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT。 默认返回值为 S_OK。  
  
### <a name="remarks"></a>备注  
 如果你想要处理所链接的属性，例如书签或更新其值是依赖于另一个属性的值应重写此函数。  
  
### <a name="example"></a>示例  
 在此函数中，用户可以通过中的属性 ID`DBPROP*`参数。 现在，就可以比较根据链接到属性 ID。 如果找到该属性，`SetProperties`现在将设置与其他属性结合使用的属性使用调用。 在此情况下，如果一个获取`DBPROP_IRowsetLocate`， `DBPROP_LITERALBOOKMARKS`，或`DBPROP_ORDEREDBOOKMARKS`属性，可以设置`DBPROP_BOOKMARKS`属性。  
  
 [!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]  
  
## <a name="setpropvalue"></a> Cutlprops:: Setpropvalue
在属性集中设置一个属性。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,  
   DBPROPID dwPropId,  
   VARIANT* pvValue);  
```  
  
#### <a name="parameters"></a>参数  
 *pguidPropSet*  
 [in]属性集的 GUID。  
  
 *dwPropId*  
 [in]属性索引。  
  
 *pvValue*  
 [in]指向一个变量，该包含新属性值的指针。  
  
### <a name="return-value"></a>返回值  
 `Failure` 在出现故障，如果成功，则为 S_OK。 

## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)