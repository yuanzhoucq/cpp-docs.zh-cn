---
title: CRowsetImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- CRowsetImpl class
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eece641adacd6ce918929366c4fc6dc78105e71a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098714"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl 类
提供标准 OLE DB 行集实现，而无需许多实现接口的多个继承。  
  
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
  
#### <a name="parameters"></a>参数  
 `T`  
 用户的类派生自`CRowsetImpl`。  
  
 `Storage`  
 用户记录类。  
  
 `CreatorClass`  
 包含的行集; 的属性的类通常该命令。  
  
 `ArrayType`  
 将充当用于行集的数据的存储类。 此参数默认为`CAtlArray`，但它可以是任何支持所需的功能的类。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[NameFromDBID](../../data/oledb/crowsetimpl-namefromdbid.md)|从字符串中提取**DBID**和将其复制到`bstr`中传递。|  
|[SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)|验证并将存储**DBID**两个字符串中的 s ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md))。|  
  
### <a name="overridable-methods"></a>可重写方法  
  
|||  
|-|-|  
|[GetColumnInfo](../../data/oledb/crowsetimpl-getcolumninfo.md)|检索特定客户端请求的列信息。|  
|[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)|检查以确定如果其中一种或两个参数包含字符串值，并且如果是这样，将字符串值复制到数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|  
|[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)|检查和 / 或如果，请参阅**DBID**s 包含字符串值，并且如果是这样，则将它们复制到其数据成员[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)|默认情况下， `CAtlArray` ，对到的用户记录的模板自变量 templatizes `CRowsetImpl`。 可以通过更改使用另一个数组类型类`ArrayType`模板自变量`CRowsetImpl`。|  
|[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)|包含行集的初始命令。|  
|[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)|包含行集的初始索引。|  
  
## <a name="remarks"></a>备注  
 `CRowsetImpl` 提供的静态向上转换窗体中的替代。 方法控制给定行集将在其中验证命令文本的方式。 你可以创建自己`CRowsetImpl`-样式通过使多个继承实现接口的类。 必须为其提供实现的唯一方法**执行**。 创建者方法具体取决于要创建哪种类型的行集，应为不同签名**执行**。 例如，如果你使用`CRowsetImpl`-派生类，以实现架构行集，**执行**方法将具有以下签名：  
  
 `HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`  
  
 如果要创建`CRowsetImpl`-派生类，以实现的命令或会话的行集**执行**方法将具有以下签名：  
  
 `HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`  
  
 若要实现的任何`CRowsetImpl`-派生**执行**方法，你必须填充内部的数据缓冲区 ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md))。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h