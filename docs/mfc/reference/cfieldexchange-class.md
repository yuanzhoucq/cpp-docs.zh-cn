---
title: CFieldExchange 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
dev_langs:
- C++
helpviewer_keywords:
- CFieldExchange [MFC], IsFieldType
- CFieldExchange [MFC], SetFieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96c70bc7c6c506d033b39ca55ba2b1a090767b5d
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951678"
---
# <a name="cfieldexchange-class"></a>CFieldExchange 类
支持数据库类使用的记录字段交换 (RFX) 和批量记录字段交换 (Bulk RFX) 例程。  
  
## <a name="syntax"></a>语法  
  
```  
class CFieldExchange  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFieldExchange::IsFieldType](#isfieldtype)|返回非零，当前操作是否适合于所更新字段的类型。|  
|[CFieldExchange::SetFieldType](#setfieldtype)|指定的记录集数据成员的类型-列或参数-直到下一步调用由所有以下调用 RFX 函数`SetFieldType`。|  
  
## <a name="remarks"></a>备注  
 `CFieldExchange` 没有基类。  
  
 如果你正在编写数据交换例程的自定义数据类型或当你要实现批量行提取;，使用此类否则，你将直接使用此类。 RFX 和批量 RFX 交换字段数据成员的记录集对象和数据源上的当前记录的相应字段之间的数据。  
  
> [!NOTE]
>  如果你正在使用的数据访问对象 (DAO) 类，而不是开放式数据库连接 (ODBC) 类，可以使用类[CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md)相反。 有关详细信息，请参阅文章[概述： 数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
 A`CFieldExchange`对象提供的上下文信息需要记录字段交换或批量记录字段交换，才能放置。 `CFieldExchange` 对象支持多个操作，包括绑定参数和字段数据成员并设置当前记录的字段上的各种标志。 由定义的类型的记录集类数据成员执行 RFX 和批量 RFX 操作**枚举** **FieldType**中`CFieldExchange`。 可能**FieldType**的值为：  
  
- **CFieldExchange::outputColumn**字段数据成员。  
  
- **CFieldExchange::inputParam**或**CFieldExchange::param**为输入的参数数据成员。  
  
- **CFieldExchange::outputParam**输出参数数据成员。  
  
- **CFieldExchange::inoutParam**输入/输出参数数据成员。  
  
 大多数类的成员函数和数据成员提供有关编写你自己的自定义 RFX 例程。 你将使用`SetFieldType`频繁。 有关详细信息，请参阅文章[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)和[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)。 有关批量行提取的信息，请参阅文章[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 有关 RFX 和批量 RFX 全局函数的详细信息，请参阅[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)此引用的 MFC 宏和全局函数部分中。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CFieldExchange`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdb.h  
  
##  <a name="isfieldtype"></a>  CFieldExchange::IsFieldType  
 如果你编写你自己 RFX 函数，请调用`IsFieldType`您确定是否可以对特定字段或参数数据成员类型执行当前操作的函数的开头 ( **CFieldExchange::outputColumn**， **CFieldExchange::inputParam**， **CFieldExchange::param**， **CFieldExchange::outputParam**，或**CFieldExchange::inoutParam**).  
  
```  
BOOL IsFieldType(UINT* pnField);
```  
  
### <a name="parameters"></a>参数  
 *pnField*  
 此参数中返回的字段或参数的数据成员的顺序号。 此数字对应于中的数据成员的顺序[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[CRecordset::DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)函数。  
  
### <a name="return-value"></a>返回值  
 如果当前操作可以执行在当前的字段或参数类型，则为非 0。  
  
### <a name="remarks"></a>备注  
 遵循现有的 RFX 函数的模型。  
  
##  <a name="setfieldtype"></a>  CFieldExchange::SetFieldType  
 你需要调用`SetFieldType`在记录集类的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)重写。  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>参数  
 *nFieldType*  
 值为**枚举 FieldType**中声明`CFieldExchange`，这可以是以下之一：  
  
- **CFieldExchange::outputColumn**  
  
- **CFieldExchange::inputParam**  
  
- **CFieldExchange::param**  
  
- **CFieldExchange::outputParam**  
  
- **CFieldExchange::inoutParam**  
  
### <a name="remarks"></a>备注  
 为字段数据成员，必须调用`SetFieldType`其中参数**CFieldExchange::outputColumn**后, 跟对 RFX 或批量 RFX 函数的调用。 如果你尚未实现批量行提取，则 ClassWizard 会将此`SetFieldType`的字段映射部分中为您调用`DoFieldExchange`。  
  
 如果你将参数化记录集类，则必须调用`SetFieldType`同样，任何字段映射部分中，外部跟 RFX 调用为所有参数的数据成员。 每种类型的参数数据成员必须有其自己的`SetFieldType`调用。 下表区分不同的值可以传递给`SetFieldType`来表示您的类的参数数据成员：  
  
|SetFieldType 参数值|参数数据成员的类型|  
|----------------------------------|-----------------------------------|  
|**CFieldExchange::inputParam**|输入的参数。 一个值，传递到记录集的查询或存储的过程。|  
|**CFieldExchange::param**|与相同**CFieldExchange::inputParam**。|  
|**CFieldExchange::outputParam**|输出参数。 记录集的存储过程返回值。|  
|**CFieldExchange::inoutParam**|输入/输出参数。 一个值，是传递给及返回的记录集的存储过程。|  
  
 一般情况下，字段数据成员或参数数据成员与关联的 RFX 函数调用的每个组前面必须是对的调用`SetFieldType`。 *NFieldType*每个参数`SetFieldType`调用标识由按照 RFX 函数调用的数据成员的类型`SetFieldType`调用。  
  
 有关处理输出参数和输入/输出参数的详细信息，请参阅`CRecordset`成员函数[FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset)。 有关 RFX 和批量 RFX 函数的详细信息，请参阅主题[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。 有关批量行提取的相关信息，请参阅文章[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>示例  
 此示例演示对附带调用 RFX 函数的几个调用`SetFieldType`。 请注意，`SetFieldType`通过调用`pFX`指向`CFieldExchange`对象。  
  
 [!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRecordset 类](../../mfc/reference/crecordset-class.md)
