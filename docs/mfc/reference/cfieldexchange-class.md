---
title: "CFieldExchange 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
dev_langs:
- C++
helpviewer_keywords:
- enum FieldType, CFieldExchange
- RFX (record field exchange) [C++]
- RFX (record field exchange) [C++], classes for
- CFieldExchange class
- FieldType enumeration
- data types [C++], custom
- enum FieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 948f13dc54fcd83941bab8e63b2ab2704d84cb87
ms.lasthandoff: 02/24/2017

---
# <a name="cfieldexchange-class"></a>CFieldExchange 类
支持数据库类使用的记录字段交换 (RFX) 和批量记录字段交换 (Bulk RFX) 例程。  
  
## <a name="syntax"></a>语法  
  
```  
class CFieldExchange  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CFieldExchange::IsFieldType](#isfieldtype)|返回非零，当前操作是否适合于所更新字段的类型。|  
|[CFieldExchange::SetFieldType](#setfieldtype)|指定的记录集数据成员的类型 — 列或参数，直到下一步调用由所有以下 RFX 函数调用`SetFieldType`。|  
  
## <a name="remarks"></a>备注  
 `CFieldExchange`没有基类的类。  
  
 如果您正在编写数据交换例程的自定义数据类型或当您要实现批量取行;，使用此类否则，您将不直接使用此类。 RFX 和 Bulk RFX 之间交换数据的记录集对象的字段数据成员和数据源上的当前记录的相应字段。  
  
> [!NOTE]
>  如果您正在使用的数据访问对象 (DAO) 类，而不是开放式数据库连接 (ODBC) 类，可以使用类[CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md)相反。 有关详细信息，请参阅文章[概述︰ 数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
 一个`CFieldExchange`对象提供的上下文信息所需的记录字段交换或批量记录字段交换才能放置。 `CFieldExchange`对象支持多个操作，包括绑定参数和字段数据成员和当前记录的字段上设置各种标志。 RFX 和 Bulk RFX 操作均由定义类型的记录集类数据成员上`enum` **FieldType**中`CFieldExchange`。 可能**FieldType**的值为︰  
  
- **CFieldExchange::outputColumn**字段数据成员。  
  
- **CFieldExchange::inputParam**或**CFieldExchange::param**对于输入的参数的数据成员。  
  
- **CFieldExchange::outputParam**对于输出参数的数据成员。  
  
- **CFieldExchange::inoutParam**输入/输出参数的数据成员。  
  
 大多数类的成员函数和数据成员提供了用于编写您自己的自定义 RFX 例程。 您将使用`SetFieldType`频繁。 有关详细信息，请参阅文章[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)和[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)。 批量取行有关的信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 有关 RFX 和 Bulk RFX 全局函数的详细信息，请参阅[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)此引用的 MFC 宏和全局部分中。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CFieldExchange`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdb.h  
  
##  <a name="isfieldtype"></a>CFieldExchange::IsFieldType  
 如果您编写您自己 RFX 函数，请调用`IsFieldType`您确定是否可以针对特定字段或参数数据成员类型执行当前操作的函数的开头 ( **CFieldExchange::outputColumn**， **CFieldExchange::inputParam**， **CFieldExchange::param**， **CFieldExchange::outputParam**，或**CFieldExchange::inoutParam**)。  
  
```  
BOOL IsFieldType(UINT* pnField);
```  
  
### <a name="parameters"></a>参数  
 *pnField*  
 此参数中返回的字段或参数的数据成员的序列号。 此数字对应于该数据成员的顺序[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[CRecordset::DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)函数。  
  
### <a name="return-value"></a>返回值  
 如果当前操作可以执行在当前的字段或参数类型为非。  
  
### <a name="remarks"></a>备注  
 请遵循现有的 RFX 函数的模型。  
  
##  <a name="setfieldtype"></a>CFieldExchange::SetFieldType  
 您需要调用`SetFieldType`在记录集类的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)重写。  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>参数  
 `nFieldType`  
 值为**枚举 FieldType**中声明`CFieldExchange`，可以是以下项之一︰  
  
- **CFieldExchange::outputColumn**  
  
- **CFieldExchange::inputParam**  
  
- **CFieldExchange::param**  
  
- **CFieldExchange::outputParam**  
  
- **CFieldExchange::inoutParam**  
  
### <a name="remarks"></a>备注  
 对于字段数据成员，您必须调用`SetFieldType`参数为**CFieldExchange::outputColumn**后, 跟对 RFX 或批量 RFX 函数的调用。 如果尚未实现批量取行，则类向导会将此`SetFieldType`的字段映射部分中为您调用`DoFieldExchange`。  
  
 如果您对参数化记录集类，则必须调用`SetFieldType`再次重申，之外任何字段映射部分中后, 跟 RFX 调用为所有参数的数据成员。 每种类型的参数数据成员必须具有其自己`SetFieldType`调用。 下表可区分不同的值将传递给`SetFieldType`来表示您的类的参数数据成员︰  
  
|SetFieldType 参数值|参数数据成员的类型|  
|----------------------------------|-----------------------------------|  
|**CFieldExchange::inputParam**|输入的参数。 一个值，传递到记录集的查询或存储的过程。|  
|**CFieldExchange::param**|与相同**CFieldExchange::inputParam**。|  
|**CFieldExchange::outputParam**|输出参数。 记录集的存储过程的返回值。|  
|**CFieldExchange::inoutParam**|输入/输出参数。 传递到，并从记录集的存储过程返回一个值。|  
  
 一般情况下，必须通过调用前面 RFX 函数调用与字段数据成员或参数数据成员关联的每个组`SetFieldType`。 `nFieldType`每个参数`SetFieldType`调用标识按照 RFX 函数调用所表示的数据成员的类型`SetFieldType`调用。  
  
 有关处理输出参数和输入/输出参数的详细信息，请参阅`CRecordset`成员函数[FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset)。 有关 RFX 和 Bulk RFX 函数的详细信息，请参阅主题[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。 有关批量取行的相关信息，请参阅文章[记录集︰ 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>示例  
 此示例演示多次调用附带的数据对的调用 RFX 函数`SetFieldType`。 请注意，`SetFieldType`通过调用`pFX`指针，指向`CFieldExchange`对象。  
  
 [!code-cpp[NVC_MFCDatabase 第&33;](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRecordset 类](../../mfc/reference/crecordset-class.md)

