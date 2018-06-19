---
title: 标准对话框数据交换例程 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f6c79a96439605bcf9ab670c1f75dda2d50169f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377650"
---
# <a name="standard-dialog-data-exchange-routines"></a>标准对话框数据交换例程
本主题列出在常见的 MFC 对话框控件使用的标准对话框数据交换 (DDX) 例程。  
  
> [!NOTE]
>  标头文件 afxdd_.h 中定义的标准对话框数据交换例程。 但是，应用程序应包括 afxwin.h。  
  
### <a name="ddx-functions"></a>DDX 函数  
  
|||  
|-|-|  
|[DDX_CBIndex](#ddx_cbindex)|初始化或检索的当前选择的组合框控件的索引。|  
|[DDX_CBString](#ddx_cbstring)|初始化或检索的组合框控件的编辑字段的当前内容。|  
|[DDX_CBStringExact](#ddx_cbstringexact)|初始化或检索的组合框控件的编辑字段的当前内容。|  
|[DDX_Check](#ddx_check)|初始化或检索的复选框控件的当前状态。|  
|[DDX_Control](#ddx_control)|子类对话框中的给定的控件。|  
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|初始化或检索日期和时间选取器控件的日期和/或时间数据。|  
|[DDX_IPAddress](#ddx_ipaddress)|初始化或检索的 IP 地址控件的当前值。|  
|[DDX_LBIndex](#ddx_lbindex)|初始化或检索的当前选择的列表框控件的索引。|  
|[DDX_LBString](#ddx_lbstring)|初始化或检索的列表框控件中当前所选内容。|  
|[DDX_LBStringExact](#ddx_lbstringexact)|初始化或检索的列表框控件中当前所选内容。|
|[DDX_ManagedControl](#ddx_managedcontrol)|创建.NET 控件匹配控件的资源 id。|  
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|初始化或检索月历控件的当前值。|  
|[DDX_Radio](#ddx_radio)|初始化或检索的单选控件组中当前选中的单选控件的基于 0 的索引。|  
|[DDX_Scroll](#ddx_scroll)|初始化或检索滚动控件的滚动块的当前位置。|  
|[DDX_Slider](#ddx_slider)|初始化或检索滑块控件的滚动块的当前位置。|  
|[DDX_Text](#ddx_text)|初始化或检索一个编辑控件的当前值。|  
  
##  <a name="ddx_cbindex"></a>  DDX_CBIndex  
 `DDX_CBIndex`函数管理的传输`int`在对话框中，组合框控件之间的数据窗体视图或控件视图对象和一个`int`的对话框、 窗体视图或控件视图对象的数据成员。  
  
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
  
 *index*  
 对对话框、 窗体视图或与其交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_CBIndex`调用时，*索引*设置为当前的组合框选择的索引。 如果未不选定任何项，*索引*设置为 0。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="ddx_cbstring"></a>  DDX_CBString  
 `DDX_CBString`函数管理的传输`CString`之间的组合框控件在对话框中，编辑控件的数据窗体视图或控件视图对象和一个`CString`的对话框、 窗体视图或控件视图对象的数据成员。  
  
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
  
 *value*  
 对对话框、 窗体视图或与其交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_CBString`调用时，*值*设置为当前的组合框选择。 如果未不选定任何项，*值*设置为长度为零的字符串。  
  
> [!NOTE]
>  如果组合框下拉列表框中，交换的值仅限于 255 个字符。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="ddx_cbstringexact"></a>  DDX_CBStringExact  
 `DDX_CBStringExact`函数管理的传输`CString`之间的组合框控件在对话框中，编辑控件的数据窗体视图或控件视图对象和一个`CString`的对话框、 窗体视图或控件视图对象的数据成员。  
  
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
  
 *value*  
 对对话框、 窗体视图或与其交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_CBStringExact`调用时，*值*设置为当前的组合框选择。 如果未不选定任何项，*值*设置为长度为零的字符串。  
  
> [!NOTE]
>  如果组合框下拉列表框中，交换的值仅限于 255 个字符。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="ddx_check"></a>  DDX_Check  
 `DDX_Check`函数管理的传输`int`之间复选框控件在对话框中，数据窗体视图或控件视图对象和一个`int`的对话框、 窗体视图或控件视图对象的数据成员。  
  
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
  
 *value*  
 对对话框、 窗体视图或与其交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_Check`调用时，*值*设置为复选框控件的当前状态。 有关可能状态的值的列表，请参阅[BM_GETCHECK](http://msdn.microsoft.com/library/windows/desktop/bb775986) Windows SDK 中。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="ddx_control"></a>  DDX_Control  
 `DDX_Control`函数指定的控件的子类`nIDC`、 对话框、 窗体视图或控件视图对象。  
  
```  
void AFXAPI DDX_Control(
    CDataExchange* pDX,  
    int nIDC,  
    CWnd& rControl);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。  
  
 `nIDC`  
 要子类化控件资源 ID。  
  
 *rControl*  
 对对话框、 窗体视图或与指定控件的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 `pDX`框架通过提供对象时`DoDataExchange`调用函数。 因此，`DDX_Control`仅应在重写中调用`DoDataExchange`。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="ddx_datetimectrl"></a>  DDX_DateTimeCtrl  
 `DDX_DateTimeCtrl`函数管理之间的日期和时间选取器控件的日期和/或时间数据传输 ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) 对话框框中或窗体视图对象，也可能[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对话框框中或窗体视图对象的数据成员。  
  
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
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。 你不需要删除此对象。  
  
 `nIDC`  
 与成员变量关联的日期和时间选取器控件资源 ID。  
  
 *value*  
 在前两个版本中，对引用`CTime`或`COleDateTime`成员变量、 对话框、 窗体视图或控件视图对象与其交换数据。 在第三个版本中，对引用`CString`数据成员控件视图对象。  
  
### <a name="remarks"></a>备注  
 当`DDX_DateTimeCtrl`调用时，*值*设置为当前的日期和时间选取器控件或控件的状态设置为*值*，取决于 exchange 的方向。  
  
 在更高版本，第三个版本`DDX_DateTimeCtrl`管理的传输`CString`日期之间的数据时间控件和[CString](../../atl-mfc-shared/reference/cstringt-class.md)的控件视图对象的数据成员。 字符串格式都是使用当前区域设置的规则用于格式化日期和时间。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  

   

 
## <a name="ddx_managedcontrol"></a>  DDX_ManagedControl
创建.NET 控件匹配控件的资源 id。  
   
### <a name="syntax"></a>语法  
  ```  
template <typename T>  
void DDX_ManagedControl(  
     CDataExchange* pDX,   
     int nIDC,   
     CWinFormsControl<T>& control );  
```
### <a name="parameters"></a>参数  
 `pDX`  
 指向的指针[CDataExchange 类](cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 与控件属性关联的控件的资源 ID。  
  
 `control`  
 对引用[CWinFormsControl 类](cwinformscontrol-class.md)对象。  
   
### <a name="remarks"></a>备注  
 `DDX_ManagedControl` 调用[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)创建控件匹配资源控件 id。 使用`DDX_ManagedControl`若要从资源 Id 创建控件[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)。 对于数据交换，不需要使用 Windows 窗体控件与 DDX/DDV 函数。  
  
 有关详细信息，请参阅[如何： 使用 Windows 窗体执行 DDX/DDV 数据绑定](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)。  
   
### <a name="requirements"></a>要求  
 **标头：** afxwinforms.h  
   
### <a name="see-also"></a>请参阅  
 [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)   
 [CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
 

  
##  <a name="ddx_ipaddress"></a>  DDX_IPAddress  
 `DDX_IPAddress`函数管理 IP 地址控件和控件视图对象的数据成员之间的数据传输。  
  
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
  
 *value*  
 对引用`DWORD`包含四个字段的值的 IP 地址控件。 字段被填充，或阅读，如下所示。  
  
|字段|包含的字段值的位|  
|-----------|-------------------------------------|  
|3|0 到 7|  
|2|8 到 15|  
|1|16 至 23|  
|0|24 到 31 之间|  
  
 使用 Win32 [IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378)以读取值，或使用[IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380)以填充值。 这些消息是 Windows SDK 中所述。  
  
### <a name="remarks"></a>备注  
 当`DDX_IPAddress`调用时，*值*或者从 IP 地址控件中，读取或*值*写入到该控件，具体取决于 exchange 的方向。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="ddx_lbindex"></a>  DDX_LBIndex  
 `DDX_LBIndex`函数管理的传输`int`在对话框中，列表框控件之间的数据窗体视图或控件视图对象和`int`的对话框、 窗体视图或控件视图对象的数据成员。  
  
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
 列表框控件的控件属性关联的资源 ID。  
  
 *index*  
 对对话框、 窗体视图或与其交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_LBIndex`调用时，*索引*设置的当前列表框中选择的索引。 如果未不选定任何项，*索引*设置为-1。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="ddx_lbstring"></a>  DDX_LBString  
 `DDX_LBString`函数管理的传输`CString`在对话框中，列表框控件之间的数据窗体视图或控件视图对象和一个`CString`的对话框、 窗体视图或控件视图对象的数据成员。  
  
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
 列表框控件的控件属性关联的资源 ID。  
  
 *value*  
 对对话框、 窗体视图或与其交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_LBString`调用以将数据传输到一个列表框控件，其开头与匹配的控件中的第一项*值*选择。 (若要匹配的整个项而不是只需前缀，使用[DDX_LBStringExact](#ddx_lbstringexact)。)如果没有匹配项，没有选择项目。 匹配不区分大小写。  
  
 当`DDX_LBString`调用以将数据从一个列表框控件，传输*值*设置为当前的列表框中选择。 如果未不选定任何项，*值*设置为长度为零的字符串。  
  
> [!NOTE]
>  如果列表框中，一个下拉列表框交换的值仅限于 255 个字符。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="ddx_lbstringexact"></a>  DDX_LBStringExact  
 `DDX_CBStringExact`函数管理的传输`CString`之间的列表框控件在对话框中，编辑控件的数据窗体视图或控件视图对象和一个`CString`的对话框、 窗体视图或控件视图对象的数据成员。  
  
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
 列表框控件的控件属性关联的资源 ID。  
  
 *value*  
 对对话框、 窗体视图或与其交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_LBStringExact`调用以将数据传输到一个列表框控件，与匹配的控件中的第一项*值*选择。 (若要匹配只需前缀而不是整个项，使用[DDX_LBString](#ddx_lbstring)。)如果没有匹配项，没有选择项目。 匹配不区分大小写。  
  
 当`DDX_CBStringExact`调用以将数据从一个列表框控件，传输*值*设置为当前的列表框中选择。 如果未不选定任何项，*值*设置为长度为零的字符串。  
  
> [!NOTE]
>  如果列表框中，一个下拉列表框交换的值仅限于 255 个字符。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="ddx_monthcalctrl"></a>  DDX_MonthCalCtrl  
 `DDX_MonthCalCtrl`函数管理月历控件之间的日期数据传输 ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) 对话框中，窗体视图或控件视图对象，也可能[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)的对话框、 窗体视图或控件视图对象的数据成员。  
  
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
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。 你不需要删除此对象。  
  
 `nIDC`  
 与成员变量时，月历控件的资源 ID 相关联。  
  
 *value*  
 对引用`CTime`或`COleDateTime`的对话框、 窗体视图或与其交换数据的控件视图对象的成员变量。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  控件管理日期值。 时对象中的时间字段将设置为反映控件窗口的创建时间或通过调用控件中设置的任意时间`CMonthCalCtrl::SetCurSel`。  
  
 当`DDX_MonthCalCtrl`调用时，*值*设置为月历控件的当前状态。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="ddx_radio"></a>  DDX_Radio  
 `DDX_Radio`函数管理的传输`int`对话框中中的单选控件组之间的数据窗体视图或控件视图对象和一个`int`的对话框、 窗体视图或控件视图对象的数据成员。 值`int`确定数据成员时根据的单选按钮组内的处于选中状态。  
  
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
 组中的第一个单选控件资源 ID。  
  
 *value*  
 对对话框、 窗体视图或与其交换数据的控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_Radio`调用时，*值*设置为单选按钮控件组的当前状态。 值设置为当前选中的单选控件基于 0 的索引或-1，如果没有单选控件进行检查。  
  
 例如，在第一个单选按钮组中的情况下选中的值的 （带有 WS_GROUP 样式的按钮）`int`成员为 0，依此类推。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="ddx_scroll"></a>  DDX_Scroll  
 `DDX_Scroll`函数管理的传输`int`之间滚动条控件在对话框中，数据窗体视图或控件视图对象和`int`的对话框、 窗体视图或控件视图对象的数据成员。  
  
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
 与控件属性关联的滚动条控件资源 ID。  
  
 *value*  
 对与其交换数据的对话框、窗体视图或控件视图对象的成员变量的引用。  
  
### <a name="remarks"></a>备注  
 当`DDX_Scroll`调用时，*值*设置为控件的滚动块的当前位置。 关联控件的滚动块的当前位置的值的详细信息，请参阅[GetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787585) Windows SDK 中。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="ddx_slider"></a>  DDX_Slider  
 `DDX_Slider`函数管理的传输`int`对话框框中或窗体视图中的滑块控件之间的数据和`int`对话框框中或窗体视图对象的数据成员。  
  
```  
void AFXAPI DDX_Slider(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>参数  
 `pDX`  
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 滑块控件的资源 ID。  
  
 *value*  
 对要进行交换的值的引用。 此参数包含，或设置滑块控件的当前位置。  
  
### <a name="remarks"></a>备注  
 当`DDX_Slider`调用时，*值*设置为控件的滚动块的当前位置或值接收到的位置，具体取决于 exchange 的方向。  
  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。 滑块控件有关的信息，请参阅[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdd_.h  
  
##  <a name="ddx_text"></a>  DDX_Text  
 `DDX_Text`函数管理的传输`int`， **UINT**，**长**， `DWORD`， `CString`， **float**，或**double**之间在对话框中，编辑控件的数据窗体视图，或控件视图和[CString](../../atl-mfc-shared/reference/cstringt-class.md)的对话框、 窗体视图或控件视图对象的数据成员。  
  
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
 指向的指针[CDataExchange](../../mfc/reference/cdataexchange-class.md)对象。 框架提供了此对象以建立数据交换的上下文，包括其方向。  
  
 `nIDC`  
 编辑控件在对话框、 窗体视图或控件视图对象的 ID。  
  
 *value*  
 对对话框、 窗体视图或控件视图对象中的数据成员的引用。 数据类型*值*依赖于其中的重载版本`DDX_Text`你使用。  
  
### <a name="remarks"></a>备注  
 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../../mfc/dialog-data-exchange-and-validation.md)。  

### <a name="requirements"></a>要求  
  **标头**afxdd_.h  

## <a name="see-also"></a>请参阅  
 [标准对话框数据验证例程](../../mfc/reference/standard-dialog-data-validation-routines.md)   
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
