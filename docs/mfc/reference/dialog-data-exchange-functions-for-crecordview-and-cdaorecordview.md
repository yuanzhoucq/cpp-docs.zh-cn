---
title: "CRecordView 和 CDaoRecordView 的对话框数据交换的函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.data
dev_langs:
- C++
helpviewer_keywords:
- DDX_Field functions
- ODBC [C++], dialog data exchange (DDX) support
- DDX (dialog data exchange) [C++], database support
- DDX (dialog data exchange) [C++], functions
- databases [C++], dialog data exchange (DDX) support
- DAO [C++], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
caps.latest.revision: 13
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 682c845aa2c915be69aee0d5e95f820573cd6084
ms.lasthandoff: 02/24/2017

---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>CRecordView 和 CDaoRecordView 的对话框数据交换函数
本主题列出了用于之间交换数据的 DDX_Field 函数[CRecordset](../../mfc/reference/crecordset-class.md)和[CRecordView](../../mfc/reference/crecordview-class.md)窗体或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)窗体。  
  
> [!NOTE]
>  DDX_Field 函数是与 DDX 函数一样的在交换在窗体中使用控件的数据。 但与不同的 DDX，在交换数据的视图关联的记录集对象的字段而不是与字段的记录视图本身。 有关详细信息，请参见类`CRecordView`和`CDaoRecordView`。  
  
### <a name="ddxfield-functions"></a>DDX_Field 函数  
  
|||  
|-|-|  
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|记录集字段数据成员与组合框中当前所选内容的索引之间传输的整数数据[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)。|  
|[DDX_FieldCBString](#ddx_fieldcbstring)|传输`CString`数据之间的记录集字段数据成员和编辑控件的组合框中`CRecordView`或`CDaoRecordView`。 移动数据时从记录集到控件，此函数以指定字符串中字符的组合框中选择的项。|  
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|传输`CString`数据之间的记录集字段数据成员和编辑控件的组合框中`CRecordView`或`CDaoRecordView`。 移动数据时从记录集到控件，此函数的指定的字符串完全匹配的组合框中选择的项。|  
|[DDX_FieldCheck](#ddx_fieldcheck)|将布尔型数据传输之间的记录集字段数据成员中的复选框`CRecordView`或`CDaoRecordView`。|  
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|记录集字段数据成员与列表框中当前所选内容的索引之间传输的整数数据`CRecordView`或`CDaoRecordView`。|  
|[DDX_FieldLBString](#ddx_fieldlbstring)|管理的传输[CString](../../atl-mfc-shared/reference/cstringt-class.md)列表框控件和记录集的字段数据成员之间的数据。 移动数据时从记录集到控件，此函数以指定字符串中字符开头的列表框中选择的项。|  
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|管理的传输`CString`列表框控件和记录集的字段数据成员之间的数据。 如果将数据从记录集移动到该控件，此函数将选择与指定的字符串完全匹配的第一项。|  
|[DDX_FieldRadio](#ddx_fieldradio)|记录集字段数据成员与一组中的单选按钮之间传输的整数数据`CRecordView`或`CDaoRecordView`。|  
|[DDX_FieldScroll](#ddx_fieldscroll)|设置或获取在滚动条控件的滚动位置`CRecordView`或`CDaoRecordView`。 从调用您[DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)函数。|  
|[DDX_FieldText](#ddx_fieldtext)|重载的版本将可供传输`int`， **UINT**，**长**， `DWORD`， [CString](../../atl-mfc-shared/reference/cstringt-class.md)， **float**， **double**，**短**， [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)，和[COleCurrency](../../mfc/reference/colecurrency-class.md)数据之间的记录集字段数据成员和编辑框中`CRecordView`或`CDaoRecordView`。|  
  
##  <a name="a-nameddxfieldcbindexa--ddxfieldcbindex"></a><a name="ddx_fieldcbindex"></a>DDX_FieldCBIndex  
 `DDX_FieldCBIndex`函数同步在记录视图中的组合框控件的列表框控件中的选定项的索引和`int`记录视图与关联的记录集字段数据成员。  
  
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
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *索引*  
 对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 移动数据时从记录集到控件，此函数中的选择设置中指定的值，根据控制*索引*。 从记录集到控件的传输，如果记录集字段为 Null，MFC 设置索引的值为 0。 在从控件到记录集的传输，控件是否为空或未选定任何项，记录集字段设置为 0。  
  
 如果您正在使用基于 ODBC 的类，请使用第一个版本。 如果您正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和详细信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)有关常规 DDX_Field 示例。 此示例将为类似的`DDX_FieldCBIndex`。  

### <a name="requirements"></a>要求  
 **标头︰** afxdao.h  

##  <a name="a-nameddxfieldcbstringa--ddxfieldcbstring"></a><a name="ddx_fieldcbstring"></a>DDX_FieldCBString  
 `DDX_FieldCBString`函数管理的传输[CString](../../atl-mfc-shared/reference/cstringt-class.md)之间在记录视图中的组合框控件的编辑控件的数据和`CString`记录视图与关联的记录集字段数据成员。  
  
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
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *值*  
 对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 此函数时将数据从记录集移动到该控件，组合框中指定的字符串中字符开头的第一行中设置当前所选内容*值*。 在从记录集的传输到该控件，如果记录集字段为 Null，从组合框中删除任何所选内容，然后组合框中的编辑控件将设置为空。 在从控件到记录集的传输，如果该控件为空，记录集字段是将设置为 Null 如果该字段允许。  
  
 如果您正在使用基于 ODBC 的类，请使用第一个版本。 如果您正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和详细信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)有关常规 DDX_Field 示例。 该示例包括调用`DDX_FieldCBString`。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
## <a name="a-nameddxfieldcbstringexacta--ddxfieldcbstringexact"></a><a name="ddx_fieldcbstringexact"></a>DDX_FieldCBStringExact  
 `DDX_FieldCBStringExact`函数管理的传输[CString](../../atl-mfc-shared/reference/cstringt-class.md)之间在记录视图中的组合框控件的编辑控件的数据和`CString`记录视图与关联的记录集字段数据成员。  
  
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
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *值*  
 对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 此函数时将数据从记录集移动到该控件，组合框中指定的字符串完全匹配的第一行中设置当前所选内容*值*。 在从记录集的传输到该控件，如果记录集字段为 NULL，从组合框中删除任何所选内容，然后组合框的编辑框将设置为空。 在从控件到记录集的传输，如果该控件为空，记录集字段设置为 NULL。  
  
 如果您正在使用基于 ODBC 的类，请使用第一个版本。 如果您正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和详细信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)有关常规 DDX_Field 示例。 调用`DDX_FieldCBStringExact`类似。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="a-nameddxfieldchecka--ddxfieldcheck"></a><a name="ddx_fieldcheck"></a>DDX_FieldCheck  
 `DDX_FieldCheck`函数管理的传输`int`在对话框中，一个复选框控件之间的数据窗体视图中或控制 view 对象和一个`int`数据成员的对话框中，窗体视图或控件视图对象。  
  
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
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 与控件属性关联的复选框控件资源 ID。  
  
 *值*  
 对对话框中，窗体视图中或与之交换数据的控件视图对象的成员变量的引用。  
  
 `pRecordset`  
 一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 当`DDX_FieldCheck`调用时，*值*设置为复选框控件的当前状态，或者该控件的状态设置为*值*，取决于传输的方向。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="a-nameddxfieldlbindexa--ddxfieldlbindex"></a><a name="ddx_fieldlbindex"></a>DDX_FieldLBIndex  
 `DDX_FieldLBIndex`函数同步在记录视图中的列表框控件中的选定项的索引和`int`记录视图与关联的记录集字段数据成员。  
  
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
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *索引*  
 对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 移动数据时从记录集到控件，此函数中的选择设置中指定的值，根据控制*索引*。 从记录集到控件的传输，如果记录集字段为 Null，MFC 设置索引的值为 0。 在从控件到记录集的传输，如果该控件为空，记录集字段设置为 0。  
  
 如果您正在使用基于 ODBC 的类，请使用第一个版本。 如果您正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和详细信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)有关常规 DDX_Field 示例。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="a-nameddxfieldlbstringa--ddxfieldlbstring"></a><a name="ddx_fieldlbstring"></a>DDX_FieldLBString  
 `DDX_FieldLBString`将列表框控件的当前所选内容复制到记录视图中[CString](../../atl-mfc-shared/reference/cstringt-class.md)记录视图与关联的记录集字段数据成员。  
  
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
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *值*  
 对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 在相反方向，此函数所设置的列表框中指定的字符串字符开头的第一行中的当前所选内容*值*。 在上从记录集到控件的传输，记录集字段为 Null，如果任何所选内容被删除从列表框。 在从控件到记录集的传输，如果该控件为空，记录集字段设置为 Null。  
  
 如果您正在使用基于 ODBC 的类，请使用第一个版本。 如果您正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和详细信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)有关常规 DDX_Field 示例。 调用`DDX_FieldLBString`类似。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="a-nameddxfieldlbstringexacta--ddxfieldlbstringexact"></a><a name="ddx_fieldlbstringexact"></a>DDX_FieldLBStringExact  
 `DDX_FieldLBStringExact`函数将列表框控件的当前所选内容复制到记录视图中[CString](../../atl-mfc-shared/reference/cstringt-class.md)记录视图与关联的记录集字段数据成员。  
  
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
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *值*  
 对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 在相反方向，此函数所设置的列表框中指定的字符串完全匹配的第一行中的当前所选内容*值*。 在上从记录集到控件的传输，记录集字段为 Null，如果任何所选内容被删除从列表框。 在从控件到记录集的传输，如果该控件为空，记录集字段设置为 Null。  
  
 如果您正在使用基于 ODBC 的类，请使用第一个版本。 如果您正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和详细信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)有关常规 DDX_Field 示例。 调用`DDX_FieldLBStringExact`类似。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="a-nameddxfieldradioa--ddxfieldradio"></a><a name="ddx_fieldradio"></a>DDX_FieldRadio  
 `DDX_FieldRadio`函数将从零开始`int`中一组单选按钮在记录视图中的当前所选的单选按钮的记录视图的记录集的成员变量。  
  
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
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 ID 的第一个组中 (使用样式**WS_GROUP**) 中的相邻的单选按钮控件[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *值*  
 对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 当从记录集字段传输到视图，此函数将打开*第 n 个*单选按钮 （从零开始），然后关闭其他按钮。 按反向执行此函数将记录集字段设置为当前在 （选中） 上的单选按钮的序号。 在从记录集到控件的传输，如果记录集字段为 Null，没有按钮处于选中状态。 在从控件到记录集的传输，如果没有控件被选定，记录集字段是将设置为 Null 如果该字段允许的。  
  
 如果您正在使用基于 ODBC 的类，请使用第一个版本。 如果您正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和详细信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)有关常规 DDX_Field 示例。 调用`DDX_FieldRadio`类似。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="a-nameddxfieldscrolla--ddxfieldscroll"></a><a name="ddx_fieldscroll"></a>DDX_FieldScroll  
 `DDX_FieldScroll`函数同步在记录视图中滚动条控件的滚动位置和一个`int`与记录视图 （或您选择将其映射到任何整数变量） 关联的记录集字段数据成员。  
  
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
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 *nIDC\**  
 ID 的第一个组中 (使用样式**WS_GROUP**) 中的相邻的单选按钮控件[CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *值*  
 对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。  
  
 `pRecordset`  
 一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。  
  
### <a name="remarks"></a>备注  
 移动数据时从记录集到控件，此函数会将滚动条控件的滚动位置设置中指定的值为*值*。 在从记录集到控件的传输，如果记录集字段为 Null，滚动条控件设置为 0。 在从控件到记录集的传输，如果该控件为空，记录集字段的值为 0。  
  
 如果您正在使用基于 ODBC 的类，请使用第一个版本。 如果您正在使用基于 DAO 的类，请使用第二个版本。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和详细信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 请参阅[DDX_FieldText](#ddx_fieldtext)有关常规 DDX_Field 示例。 调用`DDX_FieldScroll`类似。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="a-nameddxfieldtexta--ddxfieldtext"></a><a name="ddx_fieldtext"></a>DDX_FieldText  
 `DDX_FieldText`函数管理的传输`int`，**短**，**长**， `DWORD`， [CString](../../atl-mfc-shared/reference/cstringt-class.md)， **float**， **double**， **BOOL**，或**字节**的编辑框控件和记录集的字段数据成员之间的数据。  
  
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
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 中的控件的 ID [CRecordView](../../mfc/reference/crecordview-class.md)或[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)对象。  
  
 *值*  
 对关联的字段数据成员的引用`CRecordset`或`CDaoRecordset`对象。 值的数据类型取决于它的重载版本`DDX_FieldText`您使用。  
  
 `pRecordset`  
 一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)与其交换数据的对象。 此指针使`DDX_FieldText`来检测和设置 Null 值。  
  
### <a name="remarks"></a>备注  
 有关[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)对象，`DDX_FieldText`还可管理传输[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)，和[COleCurrency](../../mfc/reference/colecurrency-class.md)值。 一个空的编辑框控件指示 Null 值。 在从记录集到控件的传输，如果记录集字段为 Null，编辑框将设置为空。 在从控件到记录集的传输，如果该控件为空，记录集字段设置为 Null。  
  
 使用的版本与[CRecordset](../../mfc/reference/crecordset-class.md)参数，如果您正在使用基于 ODBC 的类。 使用的版本与[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)参数，如果您正在使用基于 DAO 的类。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 有关示例和详细信息的 DDX [CRecordView](../../mfc/reference/crecordview-class.md)和[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)字段，请参阅文章[记录视图](../../data/record-views-mfc-data-access.md)。  
  
### <a name="example"></a>示例  
 以下`DoDataExchange`函数[CRecordView](../../mfc/reference/crecordview-class.md)包含`DDX_FieldText`函数调用的三种数据类型︰`IDC_COURSELIST`是一个组合框; 其他两个控件的编辑框。 对于 DAO 编程， *m_pSet*参数是一个指向[CRecordset](../../mfc/reference/crecordset-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 [!code-cpp[NVC_MFCDatabase #&43;](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]  

  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
    
## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

