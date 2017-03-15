---
title: "标准对话框数据验证例程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
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
ms.openlocfilehash: 87cf0389b7b58579a8674d4075d2601186b1ae95
ms.lasthandoff: 02/24/2017

---
# <a name="standard-dialog-data-validation-routines"></a>标准对话框数据验证例程
本主题列出了为常见的 MFC 对话框控件使用的标准对话框数据验证 (DDV) 例程。  
  
> [!NOTE]
>  标头文件 afxdd_.h 中定义了标准对话框数据交换例程。 但是，应用程序应包括 afxwin.h。  
  
### <a name="ddv-functions"></a>DDV 函数  
  
|||  
|-|-|  
|[DDV_MaxChars](#ddv_maxchars)|验证给定的控件值中的字符数不超过给定的最大值。|  
|[DDV_MinMaxByte](#ddv_minmaxbyte)|验证给定的控件值不超过给定**字节**范围。|  
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|验证给定的控件值不超过给定的时间范围。|  
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|验证给定的控件值不超过给定**double**范围。|  
|[DDV_MinMaxDWord](#ddv_minmaxdword)|验证给定的控件值不超过给定**DWORD**范围。|  
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|验证给定的控件值不超过给定**float**范围。|  
|[DDV_MinMaxInt](#ddv_minmaxint)|验证给定的控件值不超过给定**int**范围。|  
|[DDV_MinMaxLong](#ddv_minmaxlong)|验证给定的控件值不超过给定**长**范围。|  
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|验证给定的控件值不超过给定**LONGLONG**范围。|  
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|验证给定的控件值不超过给定的日期范围。|  
|[DDV_MinMaxShort](#ddv_minmaxshort)|验证给定的控件值不超过给定**短**范围。|  
|[DDV_MinMaxSlider](#ddv_minmaxslider)|验证给定的滑块控件值在给定范围内。|  
|[DDV_MinMaxUInt](#ddv_minmaxuint)|验证给定的控件值不超过给定**UINT**范围。|  
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|验证给定的控件值不超过给定**ULONGLONG**范围。|  
  

  
##  <a name="a-nameddvmaxcharsa--ddvmaxchars"></a><a name="ddv_maxchars"></a>DDV_MaxChars  
 调用`DDV_MaxChars`以验证与相关联的控件中的字符量*值*不超过*nChars*。  
  
```   
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,  
    CString const& value,  
    int nChars); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 *值*  
 对对话框中，窗体视图或与其验证数据的控件视图对象的成员变量的引用。  
  
 `nChars`  
 允许的字符的最大数量。  
  
### <a name="remarks"></a>备注  
 DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddvminmaxbytea--ddvminmaxbyte"></a><a name="ddv_minmaxbyte"></a>DDV_MinMaxByte  
 调用`DDV_MinMaxByte`验证控件中的值与关联*值*介于之间`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,  
    BYTE value,  
    BYTE minVal,  
    BYTE maxVal); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 *值*  
 对对话框中，窗体视图或与其验证数据的控件视图对象的成员变量的引用。  
  
 `minVal`  
 最小值 (类型的**字节**) 允许。  
  
 `maxVal`  
 最大值 (类型的**字节**) 允许。  
  
### <a name="remarks"></a>备注  
 DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddvminmaxdatetimea--ddvminmaxdatetime"></a><a name="ddv_minmaxdatetime"></a>DDV_MinMaxDateTime  
 调用`DDV_MinMaxDateTime`以验证日期和时间选取器中的时间/日期值控制 ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) 与关联*refValue*介于之间`refMinRange`和`refMaxRange`。  
  
```   
void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,  
    CTime& refValue,  
    const CTime* refMinRange,  
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,  
    COleDateTime& refValue,  
    const COleDateTime* refMinRange,  
    const COleDateTime* refMaxRange); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。 不需要删除此对象。  
  
 *refValue*  
 对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)与对话框中，窗体视图或控件视图对象的成员变量关联的对象。 此对象包含要验证的数据。  
  
 `refMinRange`  
 最小日期/时间允许的值。  
  
 `refMaxRange`  
 允许的最大日期/时间值。  
  
### <a name="remarks"></a>备注  
 DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddvminmaxdoublea--ddvminmaxdouble"></a><a name="ddv_minmaxdouble"></a>DDV_MinMaxDouble  
 调用`DDV_MinMaxDouble`验证控件中的值与关联*值*介于之间`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,  
    double const& value,  
    double minVal,  
    double maxVal); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 *值*  
 对对话框中，窗体视图或与其验证数据的控件视图对象的成员变量的引用。  
  
 `minVal`  
 最小值 (类型的**double**) 允许。  
  
 `maxVal`  
 最大值 (类型的**double**) 允许。  
  
### <a name="remarks"></a>备注  
 DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddvminmaxdworda--ddvminmaxdword"></a><a name="ddv_minmaxdword"></a>DDV_MinMaxDWord  
 调用`DDV_MinMaxDWord`验证控件中的值与关联*值*介于之间`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,  
    DWORD const& value,  
    DWORD minVal,  
    DWORD maxVal); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 *值*  
 对对话框中，窗体视图或与其验证数据的控件视图对象的成员变量的引用。  
  
 `minVal`  
 最小值 (类型的`DWORD`) 允许。  
  
 `maxVal`  
 最大值 (类型的`DWORD`) 允许。  
  
### <a name="remarks"></a>备注  
 DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddvminmaxfloata--ddvminmaxfloat"></a><a name="ddv_minmaxfloat"></a>DDV_MinMaxFloat  
 调用`DDV_MinMaxFloat`验证控件中的值与关联*值*介于之间`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,  
    float value,  
    float minVal,  
    float maxVal); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 *值*  
 对对话框中，窗体视图或与其验证数据的控件视图对象的成员变量的引用。  
  
 `minVal`  
 最小值 (类型的**float**) 允许。  
  
 `maxVal`  
 最大值 (类型的**float**) 允许。  
  
### <a name="remarks"></a>备注  
 DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddvminmaxinta--ddvminmaxint"></a><a name="ddv_minmaxint"></a>DDV_MinMaxInt  
 调用`DDV_MinMaxInt`验证控件中的值与关联*值*介于之间`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,  
    int value,  
    int minVal,  
    int maxVal); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 *值*  
 对对话框中，窗体视图或与其验证数据的控件视图对象的成员变量的引用。  
  
 `minVal`  
 最小值 (类型的`int`) 允许。  
  
 `maxVal`  
 最大值 (类型的`int`) 允许。  
  
### <a name="remarks"></a>备注  
 DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddvminmaxlonga--ddvminmaxlong"></a><a name="ddv_minmaxlong"></a>DDV_MinMaxLong  
 调用`DDV_MinMaxLong`验证控件中的值与关联*值*介于之间`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,  
    long value,  
    long minVal,  
    long maxVal); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 *值*  
 对对话框中，窗体视图或与其验证数据的控件视图对象的成员变量的引用。  
  
 `minVal`  
 最小值 (类型的**长**) 允许。  
  
 `maxVal`  
 最大值 (类型的**长**) 允许。  
  
### <a name="remarks"></a>备注  
 DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddvminmaxlonglonga--ddvminmaxlonglong"></a><a name="ddv_minmaxlonglong"></a>DDV_MinMaxLongLong  
 调用`DDV_MinMaxLongLong`验证控件中的值与关联*值*介于之间`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,  
    LONGLONG value,  
    LONGLONG minVal,  
    LONGLONG maxVal); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 *值*  
 对对话框中，窗体视图或与其验证数据的控件视图对象的成员变量的引用。  
  
 `minVal`  
 最小值 (类型的**LONGLONG**) 允许。  
  
 `maxVal`  
 最大值 (类型的**LONGLONG**) 允许。  
  
### <a name="remarks"></a>备注  
 DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddvminmaxmontha--ddvminmaxmonth"></a><a name="ddv_minmaxmonth"></a>DDV_MinMaxMonth  
 调用`DDV_MinMaxMonth`若要验证的时间/日期值在月历控件 ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) 与关联*refValue*介于之间`refMinRange`和`refMaxRange`。  
  
```   
void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,  
    CTime& refValue,  
    const CTime* refMinRange,  
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,  
    COleDateTime& refValue,  
    const COleDateTime* refMinRange,  
    const COleDateTime* refMaxRange); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 *refValue*  
 对类型的对象的引用`CTime`或`COleDateTime`与对话框中的成员变量相关联，窗体视图中，或控制视图对象。 此对象包含要验证的数据。 MFC 将传递此引用时`DDV_MinMaxMonth`调用。  
  
 `refMinRange`  
 最小日期/时间允许的值。  
  
 `refMaxRange`  
 允许的最大日期/时间值。  
  
### <a name="remarks"></a>备注  
 DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddvminmaxshorta--ddvminmaxshort"></a><a name="ddv_minmaxshort"></a>DDV_MinMaxShort  
 调用`DDV_MinMaxShort`验证控件中的值与关联*值*介于之间`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,  
    short value,  
    short minVal,  
    short maxVal); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 *值*  
 对对话框中，窗体视图或与其验证数据的控件视图对象的成员变量的引用。  
  
 `minVal`  
 最小值 (类型的**短**) 允许。  
  
 `maxVal`  
 最大值 (类型的**短**) 允许。  
  
### <a name="remarks"></a>备注  
 DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddvminmaxslidera--ddvminmaxslider"></a><a name="ddv_minmaxslider"></a>DDV_MinMaxSlider  
 调用`DDV_MinMaxSlider`验证控件中的值与关联*值*介于之间`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,  
    DWORD value,  
    DWORD minVal,  
    DWORD maxVal); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 *值*  
 要验证的值对的引用。 此参数包含，或设置滑块控件的滚动块的当前位置。  
  
 `minVal`  
 允许的最小值。  
  
 `maxVal`  
 允许的最大值。  
  
### <a name="remarks"></a>备注  
 DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 关于滑块控件的信息，请参阅[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddvminmaxuinta--ddvminmaxuint"></a><a name="ddv_minmaxuint"></a>DDV_MinMaxUInt  
 调用`DDV_MinMaxUInt`验证控件中的值与关联*值*介于之间`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,  
    UINT value,  
    UINT minVal,  
    UINT maxVal); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 *值*  
 对对话框中，窗体视图或与其验证数据的控件视图对象的成员变量的引用。  
  
 `minVal`  
 最小值 (类型的**UINT**) 允许。  
  
 `maxVal`  
 最大值 (类型的**UINT**) 允许。  
  
### <a name="remarks"></a>备注  
 DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddvminmaxulonglonga--ddvminmaxulonglong"></a><a name="ddv_minmaxulonglong"></a>DDV_MinMaxULongLong  
 调用`DDV_MinMaxULongLong`验证控件中的值与关联*值*介于之间`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,  
    ULONGLONG value,  
    ULONGLONG  minVal ,  
    ULONGLONG  maxVal); 
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 *值*  
 对对话框中，窗体视图或与其验证数据的控件视图对象的成员变量的引用。  
  
 `minVal`  
 最小值 (类型的**ULONGLONG**) 允许。  
  
 `maxVal`  
 最大值 (类型的**ULONGLONG**) 允许。  
  
### <a name="remarks"></a>备注  
 DDV 有关详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  

### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
    
## <a name="see-also"></a>另请参阅  
 [标准对话框数据交换例程](../../mfc/reference/standard-dialog-data-exchange-routines.md)   
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

