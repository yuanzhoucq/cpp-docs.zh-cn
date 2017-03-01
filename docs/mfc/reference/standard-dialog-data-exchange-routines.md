---
title: "标准对话框数据交换例程 |Microsoft 文档"
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
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
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
ms.openlocfilehash: 15bd88000a7a035ed416b7e1c0640488039079ab
ms.lasthandoff: 02/24/2017

---
# <a name="standard-dialog-data-exchange-routines"></a>标准对话框数据交换例程
本主题列出了为常见的 MFC 对话框控件使用的标准对话框数据交换 (DDX) 例程。  
  
> [!NOTE]
>  标头文件 afxdd_.h 中定义了标准对话框数据交换例程。 但是，应用程序应包括 afxwin.h。  
  
### <a name="ddx-functions"></a>DDX 函数  
  
|||  
|-|-|  
|[DDX_CBIndex](#ddx_cbindex)|初始化或检索当前选择的组合框控件的索引。|  
|[DDX_CBString](#ddx_cbstring)|初始化或检索一个组合框控件的编辑字段的当前内容。|  
|[DDX_CBStringExact](#ddx_cbstringexact)|初始化或检索一个组合框控件的编辑字段的当前内容。|  
|[DDX_Check](#ddx_check)|初始化或检索一个复选框控件的当前状态。|  
|[DDX_Control](#ddx_control)|子类给定的控件在对话框中。|  
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|初始化或检索日期和时间选取器控件的日期和/或时间数据。|  
|[DDX_IPAddress](#ddx_ipaddress)|初始化或检索 IP 地址控件的当前值。|  
|[DDX_LBIndex](#ddx_lbindex)|初始化或检索当前选择的列表框控件的索引。|  
|[DDX_LBString](#ddx_lbstring)|初始化或检索列表框控件中的当前所选内容。|  
|[DDX_LBStringExact](#ddx_lbstringexact)|初始化或检索列表框控件中的当前所选内容。|  
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|初始化或检索月历控件的当前值。|  
|[DDX_Radio](#ddx_radio)|初始化或检索单选按钮控件组中当前处于选中状态的单选控件的基于 0 的索引。|  
|[DDX_Scroll](#ddx_scroll)|初始化或检索滚动控件的滚动块的当前位置。|  
|[DDX_Slider](#ddx_slider)|初始化或检索滑块控件的滚动块的当前位置。|  
|[DDX_Text](#ddx_text)|初始化或检索一个编辑控件的当前值。|  
  
##  <a name="a-nameddxcbindexa--ddxcbindex"></a><a name="ddx_cbindex"></a>DDX_CBIndex  
 `DDX_CBIndex`函数管理的传输`int`在对话框中，一个组合框控件之间的数据窗体视图中或控制 view 对象和一个`int`数据成员的对话框中，窗体视图或控件视图对象。  
  
```  
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 组合框控件的控件属性关联的资源 ID。  
  
 *索引*  
 对对话框中，窗体视图中或与之交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_CBIndex`调用时，*索引*设置为当前选定项的组合框中的索引。 如果未不选定任何项，*索引*设置为 0。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddxcbstringa--ddxcbstring"></a><a name="ddx_cbstring"></a>DDX_CBString  
 `DDX_CBString`函数管理的传输`CString`之间的组合框控件在对话框中，编辑控件的数据窗体视图中或控制 view 对象和一个`CString`数据成员的对话框中，窗体视图或控件视图对象。  
  
```  
void AFXAPI DDX_CBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 组合框控件的控件属性关联的资源 ID。  
  
 *值*  
 对对话框中，窗体视图中或与之交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_CBString`调用时，*值*设置为当前的组合框选择。 如果未不选定任何项，*值*设置为长度为零的字符串。  
  
> [!NOTE]
>  如果对组合框下拉列表框中，交换的值仅限于 255 个字符。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddxcbstringexacta--ddxcbstringexact"></a><a name="ddx_cbstringexact"></a>DDX_CBStringExact  
 `DDX_CBStringExact`函数管理的传输`CString`之间的组合框控件在对话框中，编辑控件的数据窗体视图中或控制 view 对象和一个`CString`数据成员的对话框中，窗体视图或控件视图对象。  
  
```  
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 组合框控件的控件属性关联的资源 ID。  
  
 *值*  
 对对话框中，窗体视图中或与之交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_CBStringExact`调用时，*值*设置为当前的组合框选择。 如果未不选定任何项，*值*设置为长度为零的字符串。  
  
> [!NOTE]
>  如果对组合框下拉列表框中，交换的值仅限于 255 个字符。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddxchecka--ddxcheck"></a><a name="ddx_check"></a>DDX_Check  
 `DDX_Check`函数管理的传输`int`在对话框中，一个复选框控件之间的数据窗体视图中或控制 view 对象和一个`int`数据成员的对话框中，窗体视图或控件视图对象。  
  
```  
void AFXAPI DDX_Check(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 与控件属性关联的复选框控件资源 ID。  
  
 *值*  
 对对话框中，窗体视图中或与之交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_Check`调用时，*值*设置为复选框控件的当前状态。 有关可能的状态值的列表，请参阅[BM_GETCHECK](http://msdn.microsoft.com/library/windows/desktop/bb775986)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddxcontrola--ddxcontrol"></a><a name="ddx_control"></a>DDX_Control  
 `DDX_Control`函数指定的控件的子类`nIDC`、 的对话框中，窗体视图或控件视图对象。  
  
```  
void AFXAPI DDX_Control(
    CDataExchange* pDX,  
    int nIDC,  
    CWnd& rControl);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。  
  
 `nIDC`  
 要子类化控件的资源 ID。  
  
 *rControl*  
 对对话框中，窗体视图中或指定的控件相关联的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 `pDX`由框架提供对象时`DoDataExchange`调用函数。 因此，`DDX_Control`只应在重写中调用`DoDataExchange`。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddxdatetimectrla--ddxdatetimectrl"></a><a name="ddx_datetimectrl"></a>DDX_DateTimeCtrl  
 `DDX_DateTimeCtrl`函数管理之间的日期和时间选取器控件的日期和/或时间数据传输 ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) 对话框框中或窗体视图对象，并且在[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对话框框中或窗体视图对象的数据成员。  
  
```  
void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    CTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    COleDateTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。 不需要删除此对象。  
  
 `nIDC`  
 与成员变量关联的日期和时间选取器控件资源 ID。  
  
 *值*  
 在前两个版本中，对引用`CTime`或`COleDateTime`成员变量，对话框中，窗体视图中或与之交换数据的控件视图对象。 在第三个版本中，对引用`CString`数据成员控件视图对象。  
  
### <a name="remarks"></a>备注  
 当`DDX_DateTimeCtrl`调用时，*值*设置为当前日期和时间选取器控件或控件的状态设置为*值*，取决于交换的方向。  
  
 在上面的第三版`DDX_DateTimeCtrl`管理的传输`CString`日期之间的数据时间控件和一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)控件视图对象的数据成员。 字符串格式使用当前区域设置的规则来格式化日期和时间。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddxipaddressa--ddxipaddress"></a><a name="ddx_ipaddress"></a>DDX_IPAddress  
 `DDX_IPAddress`函数管理 IP 地址控件和控件的视图对象的一个数据成员之间传输数据。  
  
```  
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,  
    int nIDC,  
    DWORD& value);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 与控件属性关联的 IP 地址控件资源 ID。  
  
 *值*  
 对引用`DWORD`包含四个字段的值的 IP 地址控件。 字段填充或读取，如下所示。  
  
|字段|包含的字段值的位|  
|-----------|-------------------------------------|  
|3|0 到 7|  
|2|8 到 15|  
|1|16 到 23|  
|0|24 到 31 之间|  
  
 使用 Win32 [IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378)读取该值，或使用[IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380)填写值。 这些消息中描述了[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 当`DDX_IPAddress`调用时，*值*或者从 IP 地址控件，读取或*值*写入到该控件，具体取决于交换的方向。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddxlbindexa--ddxlbindex"></a><a name="ddx_lbindex"></a>DDX_LBIndex  
 `DDX_LBIndex`函数管理的传输`int`在对话框中，列表框控件之间的数据窗体视图中或控制 view 对象和一个`int`数据成员的对话框中，窗体视图或控件视图对象。  
  
```  
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 控件属性关联的列表框控件资源 ID。  
  
 *索引*  
 对对话框中，窗体视图中或与之交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_LBIndex`调用时，*索引*设置为当前选定项的列表框中的索引。 如果未不选定任何项，*索引*设置为-1。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddxlbstringa--ddxlbstring"></a><a name="ddx_lbstring"></a>DDX_LBString  
 `DDX_LBString`函数管理的传输`CString`在对话框中，列表框控件之间的数据窗体视图中或控制 view 对象和一个`CString`数据成员的对话框中，窗体视图或控件视图对象。  
  
```  
void AFXAPI DDX_LBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 控件属性关联的列表框控件资源 ID。  
  
 *值*  
 对对话框中，窗体视图中或与之交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_LBString`调用以将数据传输到一个列表框控件，其开头与匹配的控件中的第一项*值*处于选中状态。 (若要匹配的整个项，而不只是一个前缀，使用[DDX_LBStringExact](#ddx_lbstringexact)。)如果没有匹配项，不选择任何项目。 匹配不区分大小写。  
  
 当`DDX_LBString`调用以将数据从一个列表框控件，传输*值*设置为当前列表框中所选内容。 如果未不选定任何项，*值*设置为长度为零的字符串。  
  
> [!NOTE]
>  如果列表框中，一个下拉列表框交换的值仅限于 255 个字符。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddxlbstringexacta--ddxlbstringexact"></a><a name="ddx_lbstringexact"></a>DDX_LBStringExact  
 `DDX_CBStringExact`函数管理的传输`CString`之间的列表框控件在对话框中，编辑控件的数据窗体视图中或控制 view 对象和一个`CString`数据成员的对话框中，窗体视图或控件视图对象。  
  
```  
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 控件属性关联的列表框控件资源 ID。  
  
 *值*  
 对对话框中，窗体视图中或与之交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_LBStringExact`调用以将数据传输到一个列表框控件，与匹配的控件中的第一项*值*处于选中状态。 (若要匹配只是一个前缀，而不是整个项目，使用[DDX_LBString](#ddx_lbstring)。)如果没有匹配项，不选择任何项目。 匹配不区分大小写。  
  
 当`DDX_CBStringExact`调用以将数据从一个列表框控件，传输*值*设置为当前列表框中所选内容。 如果未不选定任何项，*值*设置为长度为零的字符串。  
  
> [!NOTE]
>  如果列表框中，一个下拉列表框交换的值仅限于 255 个字符。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddxmonthcalctrla--ddxmonthcalctrl"></a><a name="ddx_monthcalctrl"></a>DDX_MonthCalCtrl  
 `DDX_MonthCalCtrl`函数管理月历控件之间的日期数据传输 ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) 对话框中，窗体视图或控件视图对象以及[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)数据成员的对话框中，窗体视图或控件视图对象。  
  
```  
void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    CTime& value);

void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    COleDateTime& value);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。 不需要删除此对象。  
  
 `nIDC`  
 月历控件的资源 ID 与成员变量关联。  
  
 *值*  
 对引用`CTime`或`COleDateTime`的对话框中，窗体视图中或与之交换数据的控件视图对象的成员变量。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  该控件管理日期值。 时间对象中的时间字段将设置为反映控制窗口的创建时间或在通过调用该控件中设置了任何时间`CMonthCalCtrl::SetCurSel`。  
  
 当`DDX_MonthCalCtrl`调用时，*值*设置为月历控件的当前状态。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddxradioa--ddxradio"></a><a name="ddx_radio"></a>DDX_Radio  
 `DDX_Radio`函数管理的传输`int`单选控件在对话框中，组之间的数据窗体视图中或控制 view 对象和一个`int`数据成员的对话框中，窗体视图或控件视图对象。 值`int`确定数据成员时根据哪个单选按钮组中的处于选中状态。  
  
```  
void AFXAPI DDX_Radio(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 在组中的第一个单选控件资源 ID。  
  
 *值*  
 对对话框中，窗体视图中或与之交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_Radio`调用时，*值*设置为单选按钮控件组的当前状态。 值设置为从 0 开始的索引当前处于选中状态的单选控件或-1，如果没有单选控件进行检查。  
  
 例如，在第一个单选按钮组中的情况下选中 （带有 WS_GROUP 样式的按钮） 的值`int`成员为 0，依此类推。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddxscrolla--ddxscroll"></a><a name="ddx_scroll"></a>DDX_Scroll  
 `DDX_Scroll`函数管理的传输`int`之间滚动条控件在对话框中，数据窗体视图中或控制 view 对象和一个`int`数据成员的对话框中，窗体视图或控件视图对象。  
  
```  
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向 `CDataExchange` 对象的指针。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 与控件属性关联的滚动条控件的资源 ID。  
  
 *值*  
 对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_Scroll`调用时，*值*设置为该控件的滚动块的当前位置。 使用控件的滚动块的当前位置相关联的值的详细信息，请参阅[GetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787585)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddxslidera--ddxslider"></a><a name="ddx_slider"></a>DDX_Slider  
 `DDX_Slider`函数管理的传输`int`对话框框中或窗体视图中的滑块控件之间的数据和`int`对话框框中或窗体视图对象的数据成员。  
  
```  
void AFXAPI DDX_Slider(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 滑块控件的资源 ID。  
  
 *值*  
 对要交换值的引用。 此参数包含，或设置滑块控件的当前位置。  
  
### <a name="remarks"></a>备注  
 当`DDX_Slider`调用时，*值*设置为当前控件的滚动块的位置或接收的值的位置，具体取决于交换的方向。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 关于滑块控件的信息，请参阅[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="a-nameddxtexta--ddxtext"></a><a name="ddx_text"></a>DDX_Text  
 `DDX_Text`函数管理的传输`int`， **UINT**，**长**， `DWORD`， `CString`， **float**，或**double**之间在对话框中，一个编辑控件的数据窗体视图中，或控制视图和一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)数据成员的对话框中，窗体视图或控件视图对象。  
  
```  
void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    BYTE& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    short& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    UINT& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    long& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    DWORD& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    float& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    double& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    COleCurrency& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    COleDateTime& value);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 一个指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 编辑控件在对话框中，窗体视图或控件视图对象的 ID。  
  
 *值*  
 对对话框中，窗体视图或控件视图对象中的数据成员的引用。 数据类型*值*取决于它的重载版本`DDX_Text`您使用。  
  
### <a name="remarks"></a>备注  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  

### <a name="requirements"></a>要求  
  **标头**afxdd_.h  

## <a name="see-also"></a>另请参阅  
 [标准对话框数据验证例程](../../mfc/reference/standard-dialog-data-validation-routines.md)   
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

