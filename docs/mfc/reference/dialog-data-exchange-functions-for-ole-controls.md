---
title: 对话框数据交换函数 OLE 控件的 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXDISP/DDX_OCBool
- AFXDISP/DDX_OCBoolRO
- AFXDISP/DDX_OCColor
- AFXDISP/DDX_OCColorRO
- AFXDISP/DDX_OCFloat
- AFXDISP/DDX_OCFloatRO
- AFXDISP/DDX_OCInt
- AFXDISP/DDX_OCIntRO
- AFXDISP/DDX_OCShort
- AFXDISP/DDX_OCShortRO
- AFXDISP/DDX_OCText
- AFXDISP/DDX_OCTextRO
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5dd7e1b9b18e8478cfa4e61a22806cf067cb3699
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375968"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>OLE 控件的对话框数据交换函数
本主题列出了用于对话框、 窗体视图或控件视图对象中 OLE 控件的属性和对话框、 窗体视图或控件视图对象的数据成员之间交换数据的 DDX_OC 函数。  
  
### <a name="ddxoc-functions"></a>DDX_OC 函数  
  
|||  
|-|-|  
|[DDX_OCBool](#ddx_ocbool)|管理的传输**BOOL** OLE 控件的属性之间的数据和**BOOL**数据成员。|  
|[DDX_OCBoolRO](#ddx_ocboolro)|管理的传输**BOOL** OLE 控件的只读属性之间的数据和**BOOL**数据成员。|  
|[DDX_OCColor](#ddx_occolor)|管理的传输**OLE_COLOR** OLE 控件的属性之间的数据和**OLE_COLOR**数据成员。|  
|[DDX_OCColorRO](#ddx_occolorro)|管理的传输**OLE_COLOR** OLE 控件的只读属性之间的数据和**OLE_COLOR**数据成员。|  
|[DDX_OCFloat](#ddx_ocfloat)|管理的传输**float** (或**double**) 之间的 OLE 控件属性的数据和**float** (或**double**) 数据成员。|  
|[DDX_OCFloatRO](#ddx_ocfloatro)|管理的传输**float** (或**double**) OLE 控件的只读属性之间的数据和**float** (或**double**) 数据成员。|  
|[DDX_OCInt](#ddx_ocint)|管理的传输`int`(或**长**) 之间的 OLE 控件属性的数据和`int`(或**长**) 数据成员。|  
|[DDX_OCIntRO](#ddx_ocintro)|管理的传输`int`(或**长**) OLE 控件的只读属性之间的数据和`int`(或**长**) 数据成员。|  
|[DDX_OCShort](#ddx_ocshort)|管理的传输**短**OLE 控件的属性之间的数据和**短**数据成员。|  
|[DDX_OCShortRO](#ddx_ocshortro)|管理的传输**短**OLE 控件的只读属性之间的数据和**短**数据成员。|  
|[DDX_OCText](#ddx_octext)|管理的传输**CString** OLE 控件的属性之间的数据和**CString**数据成员。|  
|[DDX_OCTextRO](#ddx_octextro)|管理的传输**CString** OLE 控件的只读属性之间的数据和**CString**数据成员。|  
  
##  <a name="ddx_ocbool"></a>  DDX_OCBool  
 `DDX_OCBool`函数管理的传输**BOOL** OLE 控件在对话框中，属性之间的数据窗体视图或控件视图对象和一个**BOOL**数据成员的对话框中，窗体视图或控件视图对象。  
  
```   
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    BOOL& value);
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 对话框、窗体视图或控件视图对象中 OLE 控件的 ID。  
  
 `dispid`  
 该控件的属性的调度 ID。  
  
 *value*  
 对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头：** afxdisp.h  
  
##  <a name="ddx_ocboolro"></a>  DDX_OCBoolRO  
 `DDX_OCBoolRO`函数管理的传输**BOOL** OLE 控件在对话框中，只读属性之间的数据窗体视图或控件视图对象和一个**BOOL**对话框中的数据成员窗体视图或控件视图对象。  
  
```   
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    BOOL& value);
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 对话框、窗体视图或控件视图对象中 OLE 控件的 ID。  
  
 `dispid`  
 该控件的属性的调度 ID。  
  
 *value*  
 对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="ddx_occolor"></a>  DDX_OCColor  
 `DDX_OCColor`函数管理的传输**OLE_COLOR** OLE 控件在对话框中，属性之间的数据窗体视图或控件视图对象和一个**OLE_COLOR**对话框中的数据成员窗体视图或控件视图对象。  
  
```   
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    OLE_COLOR& value);
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 对话框、窗体视图或控件视图对象中 OLE 控件的 ID。  
  
 `dispid`  
 该控件的属性的调度 ID。  
  
 *value*  
 对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="ddx_occolorro"></a>  DDX_OCColorRO  
 `DDX_OCColorRO`函数管理的传输**OLE_COLOR** OLE 控件在对话框中，只读属性之间的数据窗体视图或控件视图对象和一个**OLE_COLOR**的数据成员对话框、 窗体视图或控件视图对象。  
  
```   
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    OLE_COLOR& value);
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 对话框、窗体视图或控件视图对象中 OLE 控件的 ID。  
  
 `dispid`  
 该控件的属性的调度 ID。  
  
 *value*  
 对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="ddx_ocfloat"></a>  DDX_OCFloat  
 `DDX_OCFloat`函数管理的传输**float** (或**double**) 之间的 OLE 控件在对话框中，属性的数据窗体视图或控件视图对象和一个**float**(或**double**) 的对话框、 窗体视图或控件视图对象的数据成员。  
  
```   
void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    float& value);

void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    double& value);
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 对话框、窗体视图或控件视图对象中 OLE 控件的 ID。  
  
 `dispid`  
 该控件的属性的调度 ID。  
  
 *value*  
 对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="ddx_ocfloatro"></a>  DDX_OCFloatRO  
 `DDX_OCFloatRO`函数管理的传输**float** (或**double**) 之间的 OLE 控件在对话框中，只读属性的数据窗体视图或控件视图对象和一个**float** (或**double**) 的对话框、 窗体视图或控件视图对象的数据成员。  
  
```   
void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    float& value);

void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    double& value);
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 对话框、窗体视图或控件视图对象中 OLE 控件的 ID。  
  
 `dispid`  
 该控件的属性的调度 ID。  
  
 *value*  
 对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="ddx_ocint"></a>  DDX_OCInt  
 `DDX_OCInt`函数管理的传输`int`(或**长**) 之间的 OLE 控件在对话框中，属性的数据窗体视图或控件视图对象和一个`int`(或**长时间**) 的对话框、 窗体视图或控件视图对象的数据成员。  
  
```   
void AFXAPI DDX_OCInt(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    int& value);

void AFXAPI DDX_OCInt(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    long& value);
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 对话框、窗体视图或控件视图对象中 OLE 控件的 ID。  
  
 `dispid`  
 该控件的属性的调度 ID。  
  
 *value*  
 对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="ddx_ocintro"></a>  DDX_OCIntRO  
 `DDX_OCIntRO`函数管理的传输`int`(或**长**) 之间的 OLE 控件在对话框中，只读属性的数据窗体视图或控件视图对象和一个`int`(或**长**) 的对话框、 窗体视图或控件视图对象的数据成员。  
  
```   
void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    int& value);

void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    long& value);
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 对话框、窗体视图或控件视图对象中 OLE 控件的 ID。  
  
 `dispid`  
 该控件的属性的调度 ID。  
  
 *value*  
 对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="ddx_ocshort"></a>  DDX_OCShort  
 `DDX_OCShort`函数管理对话框中，窗体视图中 OLE 控件的属性之间的短的数据传输或控件视图对象和短的数据成员的对话框中，窗体视图，或控件视图对象。  
  
```   
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    short& value);
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 对话框、窗体视图或控件视图对象中 OLE 控件的 ID。  
  
 `dispid`  
 该控件的属性的调度 ID。  
  
 *value*  
 对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="ddx_ocshortro"></a>  DDX_OCShortRO  
 `DDX_OCShortRO`函数管理短之间数据传输的 OLE 控件在对话框中，窗体视图的只读属性或控件视图对象和短的数据成员的对话框中，窗体视图，或控件视图对象。  
  
```   
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    short& value);
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 对话框、窗体视图或控件视图对象中 OLE 控件的 ID。  
  
 `dispid`  
 该控件的属性的调度 ID。  
  
 *value*  
 对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="ddx_octext"></a>  DDX_OCText  
 **DDX_OCText**函数管理的传输**CString** OLE 控件在对话框中，属性之间的数据窗体视图或控件视图对象和一个**CString**数据对话框、 窗体视图或控件视图对象的成员。  
  
```   
void AFXAPI DDX_OCText(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    CString& value); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向的指针**CDataExchange**对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 对话框、窗体视图或控件视图对象中 OLE 控件的 ID。  
  
 `dispid`  
 该控件的属性的调度 ID。  
  
 *value*  
 对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="ddx_octextro"></a>  DDX_OCTextRO  
 `DDX_OCTextRO` 函数管理对话框、窗体视图或控件视图对象中 OLE 控件的只读属性与对话框、窗体视图或控件视图对象的 `CString` 数据成员之间 `CString` 数据的传输。  
  
```  
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    CString& value); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 对话框、窗体视图或控件视图对象中 OLE 控件的 ID。  
  
 `dispid`  
 该控件的属性的调度 ID。  
  
 *value*  
 对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  

### <a name="requirements"></a>要求  
  **标头**afxdisp.h
    
## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
