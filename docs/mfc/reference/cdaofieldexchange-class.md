---
title: "CDaoFieldExchange 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
dev_langs:
- C++
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4a62d3f9631d4e2807bf12e1eda3bd4b4f5112
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange 类
支持 DAO 数据库类使用的 DAO 记录字段交换 (DFX) 例程。  
  
## <a name="syntax"></a>语法  
  
```  
class CDaoFieldExchange  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|返回非零，当前操作是否适合于所更新字段的类型。|  
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|指定的记录集数据成员的类型-列或参数-由 DFX 函数对所有后续调用，直到下一步调用`SetFieldType`。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoFieldExchange::m_nOperation](#m_noperation)|正在执行的调用当前记录集的 DFX 操作`DoFieldExchange`成员函数。|  
|[CDaoFieldExchange::m_prs](#m_prs)|指向记录集的 DFX 执行操作的指针。|  
  
## <a name="remarks"></a>备注  
 `CDaoFieldExchange`没有基类。  
  
 如果你正在编写自定义数据类型; 数据交换例程，使用此类否则，你将直接使用此类。 DFX 之间交换数据的字段数据成员你[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象和相应的字段中的数据源上的当前记录。 DFX 管理两个方向的交换，从数据源和数据源。 请参阅[技术注意 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)有关编写自定义 DFX 例程信息。  
  
> [!NOTE]
>  DAO 数据库类有别于基于开放式数据库连接 (ODBC) 的 MFC 数据库类。 DAO 数据库类的所有名称都具有"CDao"前缀。 你仍可以访问 ODBC 数据源对于 DAO 类。 通常情况下，基于 DAO 的 MFC 类是比基于 ODBC 的 MFC 类的功能更强大。 基于 DAO 的类可以访问数据，包括通过 ODBC 驱动程序，通过其自己的数据库引擎。 它们还支持数据定义语言 (DDL) 操作，如添加表通过而无需自行调用 DAO 的类。  
  
> [!NOTE]
>  DAO 记录字段交换 (DFX) 是非常类似于基于 ODBC 的 MFC 数据库类中的记录字段交换 (RFX) ( `CDatabase`， `CRecordset`)。 如果你了解 RFX，你将发现易于使用 DFX。  
  
 A`CDaoFieldExchange`对象提供的上下文信息需要用于 DAO 记录字段交换做好准备。 `CDaoFieldExchange`对象支持多个操作，包括绑定参数和字段数据成员并设置当前记录的字段上的各种标志。 由定义的类型的记录集类数据成员上执行 DFX 操作`enum` **FieldType**中`CDaoFieldExchange`。 可能**FieldType**的值为：  
  
- **CDaoFieldExchange::outputColumn**字段数据成员。  
  
- **CDaoFieldExchange::param**参数数据成员。  
  
 [IsValidOperation](#isvalidoperation)为编写你自己的自定义 DFX 例程提供成员函数。 你将使用[SetFieldType](#setfieldtype)中经常你[CDaoRecordset::DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)函数。 有关 DFX 全局函数的详细信息，请参阅[记录字段交换函数](../../mfc/reference/record-field-exchange-functions.md)。 有关为你自己的数据类型编写自定义 DFX 例程的信息，请参阅[技术注意 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CDaoFieldExchange`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxdao.h  
  
##  <a name="isvalidoperation"></a>CDaoFieldExchange::IsValidOperation  
 如果你编写你自己 DFX 函数，请调用`IsValidOperation`您确定是否可以对特定字段数据成员类型执行当前操作的函数的开头 ( **CDaoFieldExchange::outputColumn**或**CDaoFieldExchange::param**)。  
  
```  
BOOL IsValidOperation();
```  
  
### <a name="return-value"></a>返回值  
 当前操作是否适合所更新字段的类型，则为非 0。  
  
### <a name="remarks"></a>备注  
 某些 DFX 机制所执行的操作仅适用于一种可能的字段类型。 遵循现有的 DFX 函数的模型。  
  
 有关编写自定义 DFX 例程的其他信息，请参阅[技术注意 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。  
  
##  <a name="m_noperation"></a>CDaoFieldExchange::m_nOperation  
 标识要执行的操作[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与字段 exchange 对象相关联的对象。  
  
### <a name="remarks"></a>备注  
 `CDaoFieldExchange`对象提供多种不同的记录集的 DFX 操作的上下文。  
  
> [!NOTE]
>  **PSEUDONULL**下面 MarkForAddNew 和 SetFieldNull 操作下所述的值是用来标记字段 Null 值。 DAO 记录字段交换机制 (DFX) 使用此值来确定哪些字段已显式标记为 Null。 **PSEUDONULL**不需要[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)和[COleCurrency](../../mfc/reference/colecurrency-class.md)字段。  
  
 可能的值的**m_nOperation**是：  
  
|操作|描述|  
|---------------|-----------------|  
|**AddToParameterList**|生成**参数**SQL 语句子句。|  
|**AddToSelectList**|生成**选择**SQL 语句子句。|  
|**BindField**|将数据库中的字段绑定到你的应用程序中的内存位置。|  
|**BindParam**|设置记录集的查询的参数的值。|  
|**修正**|设置字段的 Null 状态。|  
|**AllocCache**|分配用于检查"脏"中的字段记录集的缓存。|  
|**StoreField**|将当前记录保存到缓存。|  
|**LoadField**|还原中记录集的缓存的数据成员变量。|  
|**FreeCache**|释放缓存用于检查"脏"中的字段记录集。|  
|`SetFieldNull`|将字段的状态设置为 Null，且值为**PSEUDONULL**。|  
|**MarkForAddNew**|字段标记为"脏"的如果不**PSEUDONULL**。|  
|**MarkForEdit**|如果它们不匹配的缓存，标记字段"脏"。|  
|**SetDirtyField**|设置字段值标记为"脏"。|  
|**DumpField**|转储字段的内容 （仅限调试）。|  
|**MaxDFXOperation**|用于输入检查。|  
  
##  <a name="m_prs"></a>CDaoFieldExchange::m_prs  
 包含指向的[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与关联的对象`CDaoFieldExchange`对象。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setfieldtype"></a>CDaoFieldExchange::SetFieldType  
 调用`SetFieldType`中你`CDaoRecordset`类的`DoFieldExchange`重写。  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>参数  
 `nFieldType`  
 值为**枚举 FieldType**中声明`CDaoFieldExchange`，可以是下列操作之一：  
  
- **CDaoFieldExchange::outputColumn**  
  
- **CDaoFieldExchange::param**  
  
### <a name="remarks"></a>备注  
 通常情况下，ClassWizard 将为你编写此调用。 如果你编写自己的函数，并使用该向导来编写你`DoFieldExchange`函数中，添加到字段映射外部函数的调用。 如果不使用该向导，不将字段映射。 在调用之前对 DFX 函数，一个用于你的类，每个字段数据成员的调用和标识的字段类型**CDaoFieldExchange::outputColumn**。  
  
 如果你将参数化记录集类，你应为所有参数数据成员 （之外字段映射中） 添加 DFX 调用以及前面通过调用这些调用`SetFieldType`。 将值传递**CDaoFieldExchange::param**。 (相反，可以使用[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)并设置其参数值。)  
  
 一般情况下，字段数据成员或参数数据成员与关联的 DFX 函数调用的每个组前面必须是对的调用`SetFieldType`。 `nFieldType`每个参数`SetFieldType`调用标识的 DFX 函数调用，请按照所表示的数据成员的类型`SetFieldType`调用。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)
