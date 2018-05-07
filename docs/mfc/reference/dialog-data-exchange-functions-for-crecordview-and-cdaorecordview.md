---
title: 对话框数据交换函数 CRecordView 和 CDaoRecordView 的 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXDAO/DDX_FieldCBIndex
- AFXDAO/DDX_FieldCBString
- AFXDAO/DDX_FieldCBStringExact
- AFXDAO/DDX_FieldCheck
- AFXDAO/DDX_FieldLBIndex
- AFXDAO/DDX_FieldLBString
- AFXDAO/DDX_FieldLBStringExact
- AFXDAO/DDX_FieldRadio
- AFXDAO/DDX_FieldScroll
- AFXDAO/DDX_FieldText
dev_langs:
- C++
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 538acbf4e12c1d18e8d07337c6f428a0a0dc4b1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>CRecordView 和 CDaoRecordView 的对话框数据交换函数
本主题列出了用于之间交换数据的 DDX_Field 函数[CRecordset](../../mfc/reference/crecordset-class.md)和[CRecordView](../../mfc/reference/crecordview-class.md)窗体或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)窗体。  
  
> [!NOTE]
>  DDX_Field 函数是与 DDX 函数类似，因为它们与交换数据窗体中的控件。 但与 DDX，在交换数据与视图关联的记录集对象的字段中，而不是使用记录视图本身的字段。 有关详细信息，请参阅类`CRecordView`和`CDaoRecordView`。  
  
### <a name="ddxfield-functions"></a>DDX_Field 函数  
  
|||  
|-|-|  
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|记录集字段数据成员和组合框中当前所选内容的索引之间传输整型数据[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)。|  
|[DDX_FieldCBString](#ddx_fieldcbstring)|传输`CString`数据之间的记录集字段数据成员和编辑控件的组合框中`CRecordView`或`CDaoRecordView`。 在将数据从记录集移到控件，此函数在开头指定字符串中字符的组合框中选择的项。|  
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|传输`CString`数据之间的记录集字段数据成员和编辑控件的组合框中`CRecordView`或`CDaoRecordView`。 在将数据从记录集移到控件，此函数在与指定的字符串完全匹配组合框中选择的项。|  
|[DDX_FieldCheck](#ddx_fieldcheck)|传输布尔数据之间的记录集字段数据成员和处于的复选框`CRecordView`或`CDaoRecordView`。|  
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|记录集字段数据成员和列表框中当前所选内容的索引之间传输整型数据`CRecordView`或`CDaoRecordView`。|  
|[DDX_FieldLBString](#ddx_fieldlbstring)|管理的传输[CString](../../atl-mfc-shared/reference/cstringt-class.md)的列表框控件和记录集的字段数据成员之间的数据。 在将数据从记录集移到控件，此函数的开头指定字符串中字符的列表框中选择的项。|  
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|管理的传输`CString`的列表框控件和记录集的字段数据成员之间的数据。 当将数据从记录集移到控件，此函数会选择与指定的字符串完全匹配的第一项。|  
|[DDX_FieldRadio](#ddx_fieldradio)|记录集字段数据成员和一组中的单选按钮之间传输整型数据`CRecordView`或`CDaoRecordView`。|  
|[DDX_FieldScroll](#ddx_fieldscroll)|设置或获取在滚动条控件的滚动位置`CRecordView`或`CDaoRecordView`。 从调用你[DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)函数。|  
|[DDX_FieldSlider](#ddx_fieldslider)|同步记录视图中的滑块控件的滚动块位置和`int`字段数据成员的记录集。 |
|[DDX_FieldText](#ddx_fieldtext)|重载的版本都是可用于传输`int`， **UINT**，**长**， `DWORD`， [CString](../../atl-mfc-shared/reference/cstringt-class.md)， **float****double**，**短**， [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)，和[COleCurrency](../../mfc/reference/colecurrency-class.md)记录集字段数据成员和编辑之间的数据框中`CRecordView`或`CDaoRecordView`。|  
  
##  <a name="ddx_fieldcbindex"></a>  DDX_FieldCBIndex  
 `DDX_FieldCBIndex`函数同步的组合框控件中的记录视图的列表框控件中的选定项的索引和`int`与记录视图关联的记录集字段数据成员。  
  
```  
void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,    
    int nIDC,   
    int& index,  
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,    
    int nIDC,   
    int& index,  
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *index*  
 对中关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 指向的指针[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 在将数据从记录集移到控件，此函数将在基于中指定的值控制设置所选内容*索引*。 在从记录集到控件的传输，如果记录集字段为 Null，MFC 设置的值的索引为 0。 在从控件到记录集的传输，控件是否为空或未选定任何项，记录集字段设置为 0。  
  
 如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 例如。 该示例将类似的`DDX_FieldCBIndex`。  

### <a name="requirements"></a>要求  
 **标头：** afxdao.h  

##  <a name="ddx_fieldcbstring"></a>  DDX_FieldCBString  
 `DDX_FieldCBString`函数管理的传输[CString](../../atl-mfc-shared/reference/cstringt-class.md)记录视图中的组合框控件的编辑控件之间的数据和`CString`与记录视图关联的记录集字段数据成员。  
  
```  
void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *value*  
 对中关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 指向的指针[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 此函数时将数据从记录集移到控件，组合框中指定的字符串中的字符开头的第一行中设置当前所选内容*值*。 从记录集的传输到该控件，在如果记录集字段为 Null，从组合框中删除任何所选内容和组合框编辑控件将设置为空。 在从控件到记录集的传输，控件是否为空，记录集字段设置为 Null 如果字段允许。  
  
 如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 例如。 该示例包括调用`DDX_FieldCBString`。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
## <a name="ddx_fieldcbstringexact"></a>  DDX_FieldCBStringExact  
 `DDX_FieldCBStringExact`函数管理的传输[CString](../../atl-mfc-shared/reference/cstringt-class.md)记录视图中的组合框控件的编辑控件之间的数据和`CString`与记录视图关联的记录集字段数据成员。  
  
```  
void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *value*  
 对中关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 指向的指针[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 此函数时将数据从记录集移到控件，组合框中指定的字符串完全匹配的第一行中设置当前所选内容*值*。 从记录集的传输到该控件，在如果记录集字段为 NULL，从组合框中删除任何所选内容和组合框的编辑框将设置为空。 在从控件到记录集的传输，控件是否为空，记录集字段设置为 NULL。  
  
 如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 例如。 调用`DDX_FieldCBStringExact`类似。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="ddx_fieldcheck"></a>  DDX_FieldCheck  
 `DDX_FieldCheck`函数管理的传输`int`之间复选框控件在对话框中，数据窗体视图或控件视图对象和`int`的对话框、 窗体视图或控件视图对象的数据成员。  
  
```  
void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 与控件属性关联的复选框控件资源 ID。  
  
 *value*  
 对对话框、 窗体视图或与其交换数据的控件视图对象的成员变量的引用。  
  
 `pRecordset`  
 指向的指针[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 当`DDX_FieldCheck`调用时，*值*设置为当前状态的复选框控件，或控件的状态设置为*值*，取决于传输的方向。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="ddx_fieldlbindex"></a>  DDX_FieldLBIndex  
 `DDX_FieldLBIndex`函数同步在记录视图的列表框控件中的选定项的索引和`int`与记录视图关联的记录集字段数据成员。  
  
```  
void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,    
    int nIDC,   
    int& index,  
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,    
    int nIDC,   
    int& index,  
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *index*  
 对中关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 指向的指针[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 在将数据从记录集移到控件，此函数将在基于中指定的值控制设置所选内容*索引*。 在从记录集到控件的传输，如果记录集字段为 Null，MFC 设置的值的索引为 0。 在从控件到记录集的传输，控件是否为空，记录集字段设置为 0。  
  
 如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 例如。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="ddx_fieldlbstring"></a>  DDX_FieldLBString  
 `DDX_FieldLBString`将列表框控件的当前所选内容复制到记录视图中[CString](../../atl-mfc-shared/reference/cstringt-class.md)与记录视图关联的记录集字段数据成员。  
  
```  
void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *value*  
 对中关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 指向的指针[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 按反向执行，此函数所设置的列表框中指定的字符串的字符开头的第一行中的当前选择*值*。 在从记录集到控件的传输，如果记录集字段为 Null，任何选择被删除从列表框。 在从控件到记录集的传输，控件是否为空，记录集字段设置为 Null。  
  
 如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 例如。 调用`DDX_FieldLBString`类似。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="ddx_fieldlbstringexact"></a>  DDX_FieldLBStringExact  
 `DDX_FieldLBStringExact`函数将当前选择的列表框控件复制到记录视图中[CString](../../atl-mfc-shared/reference/cstringt-class.md)与记录视图关联的记录集字段数据成员。  
  
```  
void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *value*  
 对中关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 指向的指针[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 按反向执行，此函数所设置的列表框中指定的字符串完全匹配的第一行中的当前选择*值*。 在从记录集到控件的传输，如果记录集字段为 Null，任何选择被删除从列表框。 在从控件到记录集的传输，控件是否为空，记录集字段设置为 Null。  
  
 如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 例如。 调用`DDX_FieldLBStringExact`类似。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="ddx_fieldradio"></a>  DDX_FieldRadio  
 `DDX_FieldRadio`函数将从零开始`int`的一组记录视图中的单选按钮中的当前所选的单选按钮的记录视图的记录集的成员变量。  
  
```  
void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 ID 的第一个组中 (使用样式**WS_GROUP**) 中的相邻的单选按钮控件的[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *value*  
 对中关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 指向的指针[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 如果从记录集字段传输到视图中，此函数会打开*第 n 个*单选按钮 （从零开始），然后关闭其他按钮。 按反向执行，此函数将记录集字段设置为当前在 （选中） 上的单选按钮的序号。 在从记录集到控件的传输，如果记录集字段为 Null，则选择没有按钮。 在从控件到记录集的传输，如果没有控件被选定，记录集字段设置为 Null 如果字段允许的。  
  
 如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 例如。 调用`DDX_FieldRadio`类似。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="ddx_fieldscroll"></a>  DDX_FieldScroll  
 `DDX_FieldScroll`函数同步记录视图中滚动条控件的滚动位置和`int`字段数据成员的记录集与记录视图 （或你选择将其映射到任何整数变量） 关联。  
  
```  
void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 ID 的第一个组中 (使用样式**WS_GROUP**) 中的相邻的单选按钮控件的[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *value*  
 对中关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 指向的指针[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 当将数据从记录集移到控件，此函数会将滚动条控件的滚动位置设置中指定的值为*值*。 在从记录集到控件的传输，如果记录集字段为 Null，滚动条控件设置为 0。 在从控件到记录集的传输，控件是否为空，记录集字段的值为 0。  
  
 如果你正在使用基于 ODBC 的类，请使用第一个版本。 如果你正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 例如。 调用`DDX_FieldScroll`类似。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  

  ## <a name="nameddxfieldslidera--ddxfieldslider"></a>name="ddx_fieldslider"></a>  DDX_FieldSlider
`DDX_FieldSlider`函数同步记录视图中的滑块控件的滚动块位置和`int`字段数据成员的记录集与记录视图 （或你选择将其映射到任何整数变量） 关联。  
   
### <a name="syntax"></a>语法  
  ```
   void AFXAPI DDX_FieldSlider(  
       CDataExchange* pDX,  
       int nIDC,  
       int& value,  
       CRecordset* pRecordset );  

void AFXAPI DDX_FieldSlider(  
     CDataExchange* pDX,  
     int nIDC,  
     int& value,  
     CDaoRecordset* pRecordset );  
```
### <a name="parameters"></a>参数  
 `pDX`  
 指向的指针[CDataExchange](cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 滑块控件的资源 ID。  
  
 *value*  
 对要进行交换的值的引用。 此参数会保存或将用于设置滑块控件的滚动块的当前位置。  
  
 `pRecordset`  
 到关联的指针`CRecordset`或`CDaoRecordset`与其交换数据的对象。  
   
### <a name="remarks"></a>备注  
 当将数据从记录集移到滑块，此函数会将滑块的位置设置中指定的值为*值*。 在从记录集到控件的传输，如果记录集字段为 Null，滑块控件的位置设置为 0。 在从控件到记录集的传输，控件是否为空，记录集字段的值为 0。  
  
 `DDX_FieldSlider` 不交换与滑块控件支持的设置范围，而不是只需的位置的范围信息。  
  
 如果你正在使用基于 ODBC 的类，请使用函数的第一个重写。 第二个重写使用基于 DAO 的类。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX`CRecordView`和`CDaoRecordView`字段，请参阅[记录视图](../../data/record-views-mfc-data-access.md)。 滑块控件有关的信息，请参阅[使用 CSliderCtrl](../using-csliderctrl.md)。  
   
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)常规 DDX_Field 例如。 调用`DDX_FieldSlider`类似。  
   
### <a name="requirements"></a>要求  
 **标头：** afxdao.h  
   
### <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
  
##  <a name="ddx_fieldtext"></a>  DDX_FieldText  
 `DDX_FieldText`函数管理的传输`int`，**短**，**长**， `DWORD`， [CString](../../atl-mfc-shared/reference/cstringt-class.md)， **float**， **double**， **BOOL**，或**字节**编辑框控件和记录集的字段数据成员之间的数据。  
  
```  
void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    BYTE& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    UINT& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    long& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    DWORD& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    float& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    double& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    short& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    BOOL& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    BYTE& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    long& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    DWORD& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    float& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    double& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    COleDateTime& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    COleCurrency& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *value*  
 对中关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。 值的数据类型取决于其的重载版本`DDX_FieldText`你使用。  
  
 `pRecordset`  
 指向的指针[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。 此指针使`DDX_FieldText`以检测并设置 Null 值。  
  
### <a name="remarks"></a>备注  
 有关[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象，`DDX_FieldText`还管理传输[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)，和[COleCurrency](../../mfc/reference/colecurrency-class.md)值。 一个空的编辑框控件指示 Null 值。 从记录集到控件的传输，如果记录集字段为 Null，编辑框设置为空。 在从控件到记录集的传输，控件是否为空，记录集字段设置为 Null。  
  
 使用的版本与[CRecordset](../../mfc/reference/crecordset-class.md)参数，如果你正在使用基于 ODBC 的类。 使用的版本与[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)参数，如果你正在使用基于 DAO 的类。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和更多信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 以下`DoDataExchange`函数[CRecordView](../../mfc/reference/crecordview-class.md)包含`DDX_FieldText`函数调用以三种数据类型：`IDC_COURSELIST`是一个组合框; 其他两个控件的编辑框。 对于 DAO 编程， *m_pSet*参数是一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 [!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]  

  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
    
## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
