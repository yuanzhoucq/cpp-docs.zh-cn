---
title: "CDateTimeCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CloseMonthCal
- AFXDTCTL/CDateTimeCtrl::Create
- AFXDTCTL/CDateTimeCtrl::GetDateTimePickerInfo
- AFXDTCTL/CDateTimeCtrl::GetIdealSize
- AFXDTCTL/CDateTimeCtrl::GetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::GetMonthCalCtrl
- AFXDTCTL/CDateTimeCtrl::GetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::GetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::GetRange
- AFXDTCTL/CDateTimeCtrl::GetTime
- AFXDTCTL/CDateTimeCtrl::SetFormat
- AFXDTCTL/CDateTimeCtrl::SetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::SetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::SetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::SetRange
- AFXDTCTL/CDateTimeCtrl::SetTime
dev_langs:
- C++
helpviewer_keywords:
- DateTimePicker control [MFC], CDateTimeCtrl class
- date-picking functionality
- CDateTimeCtrl class
- DateTimePicker control [MFC]
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: e5407934021abdb64dfb625e3dfb2c1841b7a5f0
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl 类
封装日期和时间选取器控件功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CDateTimeCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CDateTimeCtrl::CDateTimeCtrl](#cdatetimectrl)|构造 `CDateTimeCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CDateTimeCtrl::CloseMonthCal](#closemonthcal)|关闭当前的日期和时间选取器控件。|  
|[CDateTimeCtrl::Create](#create)|创建日期和时间选取器控件，并将其附加到`CDateTimeCtrl`对象。|  
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|检索当前日期和时间选取器控件的信息。|  
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|返回当前日期或时间显示所需的日期和时间选取器控件的理想大小。|  
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|检索日期和时间选取器控件中的月日历的指定部分的颜色。|  
|[Cdatetimectrl:: Getmonthcalctrl](#getmonthcalctrl)|检索`CMonthCalCtrl`与日期和时间选取器控件关联的对象。|  
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|检索当前使用的日期和时间选取器控件子月历控件的字体。|  
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|获取当前日期和时间选取器控件的样式。|  
|[CDateTimeCtrl::GetRange](#getrange)|检索当前最小值和最大允许的日期和时间选取器控件的系统时间。|  
|[CDateTimeCtrl::GetTime](#gettime)|从日期和时间选取器控件中检索当前所选的时间，并将其放在指定的`SYSTEMTIME`结构。|  
|[Cdatetimectrl:: Setformat](#setformat)|将根据给定的格式字符串的日期和时间选取器控件的显示设置。|  
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|设置月历日期和时间选取器控件内的指定部分的颜色。|  
|[CDateTimeCtrl::SetMonthCalFont](#setmonthcalfont)|设置日期和时间选取器控件的子月历控件将使用的字体。|  
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|将当前日期和时间选取器控件的样式设置。|  
|[CDateTimeCtrl::SetRange](#setrange)|设置日期和时间选取器控件的最小值和最大允许的系统时间。|  
|[CDateTimeCtrl::SetTime](#settime)|在日期和时间选取器控件中设置的时间。|  
  
## <a name="remarks"></a>备注  
 日期和时间选取器控件 （DTP 控件） 提供了一个简单的界面来交换与用户的日期和时间信息。 此接口包含的字段，其中每个显示存储在该控件的日期和时间信息的一部分。 用户可以更改通过更改给定字段中的字符串的内容存储在该控件的信息。 用户可以移动字段之间使用鼠标或键盘。  
  
 通过将各种样式应用于该对象创建它时，可以自定义日期和时间选取器控件。 请参阅[日期和时间选取器控件样式](http://msdn.microsoft.com/library/windows/desktop/bb761728)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]关于特定于日期和时间选取器控件的样式的详细信息。 您可以设置使用格式样式的 DTP 控件的显示格式。 在"格式样式"中描述这些格式样式[!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)]主题[日期和时间选取器控件样式](http://msdn.microsoft.com/library/windows/desktop/bb761728)。  
  
 日期和时间选取器控件还使用通知和中所述的回调[使用 CDateTimeCtrl](../../mfc/using-cdatetimectrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDateTimeCtrl`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdtctl.h  
  
##  <a name="cdatetimectrl"></a>CDateTimeCtrl::CDateTimeCtrl  
 构造 `CDateTimeCtrl` 对象。  
  
```  
CDateTimeCtrl();
```  
  
##  <a name="closemonthcal"></a>CDateTimeCtrl::CloseMonthCal  
 关闭当前的日期和时间选取器控件。  
  
```  
void CloseMonthCal() const;  
```  
  
### <a name="remarks"></a>备注  
 此方法可发送[DTM_CLOSEMONTHCAL](http://msdn.microsoft.com/library/windows/desktop/bb761753)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_dateTimeCtrl`，也就是说，用来以编程方式访问日期和时间选取器控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例将关闭当前的日期和时间选取器控件上下拉日历。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&5;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]  
  
##  <a name="create"></a>CDateTimeCtrl::Create  
 创建日期和时间选取器控件，并将其附加到`CDateTimeCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定日期时间控件样式的组合。 请参阅[日期和时间选取器控件样式](http://msdn.microsoft.com/library/windows/desktop/bb761728)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关日期和时间选取器样式的详细信息。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它是位置和日期和时间选取器控件的大小。  
  
 `pParentWnd`  
 一个指向[CWnd](../../mfc/reference/cwnd-class.md)是日期和时间选取器控件的父窗口的对象。 它不能**NULL**。  
  
 `nID`  
 指定日期和时间选取器控件的控件 id。  
  
### <a name="return-value"></a>返回值  
 如果创建成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
  
##### <a name="to-create-a-date-and-time-picker-control"></a>若要创建的日期和时间选取器控件  
  
1.  调用[CDateTimeCtrl](#cdatetimectrl)构造`CDateTimeCtrl`对象。  
  
2.  调用此成员函数，它能创建 Windows 日期和时间选取器控件并将其附加到`CDateTimeCtrl`对象。  
  
 当您调用**创建**，常见的控件进行了初始化。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&1;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]  
  
##  <a name="getdatetimepickerinfo"></a>CDateTimeCtrl::GetDateTimePickerInfo  
 检索当前日期和时间选取器控件的信息。  
  
```   
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[out] `pDateTimePickerInfo`|一个指向[DATETIMEPICKERINFO](http://msdn.microsoft.com/library/windows/desktop/bb761729)结构，它接收当前日期和时间选取器控件的说明。<br /><br /> 调用方负责分配此结构。 但是，此方法初始化`cbSize`结构中的成员。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[DTM_GETDATETIMEPICKERINFO](http://msdn.microsoft.com/library/windows/desktop/bb761755)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_dateTimeCtrl`，也就是说，用来以编程方式访问日期和时间选取器控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例指示是否已成功检索当前日期和时间选取器控件的信息。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&4;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]  
  
##  <a name="getmonthcalcolor"></a>CDateTimeCtrl::GetMonthCalColor  
 检索日期和时间选取器控件中的月日历的指定部分的颜色。  
  
```  
COLORREF GetMonthCalColor(int iColor) const;  
```  
  
### <a name="parameters"></a>参数  
 `iColor`  
 `int`值，该值指定要检索的月份日历的颜色区域。 值的列表，请参阅`iColor`参数[SetMonthCalColor](#setmonthcalcolor)。  
  
### <a name="return-value"></a>返回值  
 一个**COLORREF**值，该值表示颜色设置月历控件的指定部分，如果操作成功。 如果不成功，则该函数返回-1。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[DTM_GETMCCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761759)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&2;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]  
  
##  <a name="getmonthcalctrl"></a>Cdatetimectrl:: Getmonthcalctrl  
 检索`CMonthCalCtrl`与日期和时间选取器控件关联的对象。  
  
```  
CMonthCalCtrl* GetMonthCalCtrl() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)对象，或**NULL**如果不成功或窗口不可见。  
  
### <a name="remarks"></a>备注  
 日期和时间选取器控件创建一个子月历控件，当用户单击下拉箭头。 当`CMonthCalCtrl`不再需要对象，它将被销毁，因此您的应用程序必须不依赖于存储表示日期时间选取器控件子月的日历中的对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&3;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]  
  
##  <a name="getmonthcalfont"></a>CDateTimeCtrl::GetMonthCalFont  
 获取当前使用的日期和时间选取器控件月历控件的字体。  
  
```  
CFont* GetMonthCalFont() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CFont](../../mfc/reference/cfont-class.md)对象，或**NULL**如果不成功。  
  
### <a name="remarks"></a>备注  
 `CFont`指向返回的值的对象是临时对象，并在下一步的空闲处理期间被销毁。  
  
##  <a name="getmonthcalstyle"></a>CDateTimeCtrl::GetMonthCalStyle  
 获取下拉月历控件的当前日期和时间选取器控件与该键关联的样式。  
  
```  
DWORD GetMonthCalStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 样式的日期和时间选取器控件样式的下拉列表月历控件，这是一个按位组合 （或者）。 有关详细信息，请参阅[月份的日历控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760919)。  
  
### <a name="remarks"></a>备注  
 此方法可发送[DTM_GETMCSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb761763)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getrange"></a>CDateTimeCtrl::GetRange  
 检索当前最小值和最大允许的日期和时间选取器控件的系统时间。  
  
```  
DWORD GetRange(
    COleDateTime* pMinRange,  
    COleDateTime* pMaxRange) const;  
  
DWORD GetRange(
    CTime* pMinRange,  
    CTime* pMaxRange) const;  
```  
  
### <a name="parameters"></a>参数  
 `pMinRange`  
 一个指向[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，其中包含中允许的最早时间`CDateTimeCtrl`对象。  
  
 `pMaxRange`  
 一个指向`COleDateTime`对象或`CTime`对象，其中包含中允许的最晚时间`CDateTimeCtrl`对象。  
  
### <a name="return-value"></a>返回值  
 一个`DWORD`值，该值包含指示的范围设置的标志。 如果  
  
 `return value & GDTR_MAX` == 0  
  
 然后第二个参数才有效。 同样，如果  
  
 `return value & GDTR_MIN` == 0  
  
 然后第一个参数才有效。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[DTM_GETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761767)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在 MFC 的实现中，您可以指定`COleDateTime`或`CTime`用法。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&4;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]  
  
##  <a name="gettime"></a>CDateTimeCtrl::GetTime  
 从日期和时间选取器控件中检索当前所选的时间，并将其放在指定的`SYSTEMTIME`结构。  
  
```  
BOOL GetTime(COleDateTime& timeDest) const;  
DWORD GetTime(CTime& timeDest) const;  
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;  
```  
  
### <a name="parameters"></a>参数  
 *timeDest*  
 在第一个版本中，对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)将收到系统时间信息的对象。 在第二个版本中，对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)将收到系统时间信息的对象。  
  
 *pTimeDest*  
 一个指向[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)接收系统时间信息的结构。 不能**NULL**。  
  
### <a name="return-value"></a>返回值  
 在第一个版本中，如果已成功写入时间，则为非`COleDateTime`对象; 否则为 0。 在第二个和第三个版本中，`DWORD`值等于**dwFlag**成员中设置[NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730)结构。 请参阅**备注**节的详细信息。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[DTM_GETSYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/bb761769)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 中的 MFC 实现**GetTime**，您可以使用`COleDateTime`或`CTime`类，也可以使用`SYSTEMTIME`结构来存储的时间信息。  
  
 返回值`DWORD`在第二个和第三个版本中，更高版本，指示是否将日期和时间选取器控件设置为"无日期"状态时，如中所示[NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730)结构成员`dwFlags`。 如果返回的值等于**GDT_NONE**，控件将状态设置为"无日期"，并使用**DTS_SHOWNONE**样式。 如果返回的值等于**GDT_VALID**，系统时间已成功存储在目标位置。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&5;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]  
  
##  <a name="getidealsize"></a>CDateTimeCtrl::GetIdealSize  
 返回当前日期或时间显示所需的日期和时间选取器控件的理想大小。  
  
```  
BOOL GetIdealSize(LPSIZE psize) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[out] `psize`|指向[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构，其中包含该控件的理想大小。|  
  
### <a name="return-value"></a>返回值  
 返回值也始终`true`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[DTM_GETIDEALSIZE](http://msdn.microsoft.com/library/windows/desktop/bb761757)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_dateTimeCtrl`，也就是说，用来以编程方式访问日期和时间选取器控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例检索要显示日期和时间选取器控件的理想大小。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&2;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]  
  
##  <a name="setformat"></a>Cdatetimectrl:: Setformat  
 将根据给定的格式字符串的日期和时间选取器控件的显示设置。  
  
```  
BOOL SetFormat(LPCTSTR pstrFormat);
```  
  
### <a name="parameters"></a>参数  
 *pstrFormat*  
 指向一个定义所需的显示的零终止格式字符串的指针。 将此参数设置为**NULL**会将控件重置为当前样式的默认格式字符串。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
> [!NOTE]
>  用户输入不确定成功或失败，此调用。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[DTM_SETFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb761771)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&6;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]  
  
##  <a name="setmonthcalcolor"></a>CDateTimeCtrl::SetMonthCalColor  
 设置月历日期和时间选取器控件内的指定部分的颜色。  
  
```  
COLORREF SetMonthCalColor(
    int iColor,  
    COLORREF ref);
```  
  
### <a name="parameters"></a>参数  
 `iColor`  
 `int`值，该值指定要设置的月份的日历控件的哪个区域。 此值可以是下列其中一项。  
  
|值|含义|  
|-----------|-------------|  
|MCSC_BACKGROUND|设置显示不同的月份的背景色。|  
|MCSC_MONTHBK|设置显示在一个月中的背景色。|  
|MCSC_TEXT|设置用于在一个月中显示文本的颜色。|  
|MCSC_TITLEBK|设置显示在日历的标题的背景色。|  
|MCSC_TITLETEXT|设置用于显示日历的标题中的文本的颜色。|  
|MCSC_TRAILINGTEXT|设置用来显示标头和尾部天文本的颜色。 标头和后续日期是从显示在当前日历前后月份的天数。|  
  
 `ref`  
 一个**COLORREF**值，该值表示将会为月日历的指定区域设置的颜色。  
  
### <a name="return-value"></a>返回值  
 一个**COLORREF**值，该值表示月历控件的指定部分上一个颜色设置，如果操作成功。 否则，该消息返回-1。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[DTM_SETMCCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761773)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)。  
  
##  <a name="setmonthcalfont"></a>CDateTimeCtrl::SetMonthCalFont  
 设置日期和时间选取器控件的子月历控件将使用的字体。  
  
```  
void SetMonthCalFont(
    HFONT hFont,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `hFont`  
 将设置的字体的句柄。  
  
 `bRedraw`  
 指定是否应立即绘该控件后设置字体。 将此参数设置为**TRUE**导致控件重绘其自身。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[DTM_SETMCFONT](http://msdn.microsoft.com/library/windows/desktop/bb761775)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&7;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]  
  
> [!NOTE]
>  如果使用此代码，您需要使的成员您`CDialog`的派生类调用`m_MonthFont`类型的**CFont**。  
  
##  <a name="setmonthcalstyle"></a>CDateTimeCtrl::SetMonthCalStyle  
 设置下拉月历控件的当前日期和时间选取器控件与该键关联的样式。  
  
```  
DWORD SetMonthCalStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `dwStyle`|一个新的月份的日历月份的日历控件样式的按位组合 (OR) 的控件样式。 有关详细信息，请参阅[月份的日历控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760919)。|  
  
### <a name="return-value"></a>返回值  
 上一个下拉列表月历控件的样式。  
  
### <a name="remarks"></a>备注  
 此方法可发送[DTM_SETMCSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb761778)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_dateTimeCtrl`，也就是说，用来以编程方式访问日期和时间选取器控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置日期和时间选取器控件来显示周数，发生在星期几，及没有今日指示器的天的缩写名称。  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;&3;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]  
  
##  <a name="setrange"></a>CDateTimeCtrl::SetRange  
 设置日期和时间选取器控件的最小值和最大允许的系统时间。  
  
```  
BOOL SetRange(
    const COleDateTime* pMinRange,  
    const COleDateTime* pMaxRange);

 
BOOL SetRange(
    const CTime* pMinRange,  
    const CTime* pMaxRange);
```  
  
### <a name="parameters"></a>参数  
 `pMinRange`  
 一个指向[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，其中包含中允许的最早时间`CDateTimeCtrl`对象。  
  
 `pMaxRange`  
 一个指向`COleDateTime`对象或`CTime`对象，其中包含中允许的最晚时间`CDateTimeCtrl`对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[DTM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761780)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在 MFC 的实现中，您可以指定`COleDateTime`或`CTime`用法。 如果`COleDateTime`对象具有**NULL**状态，将删除范围。 如果`CTime`指针或`COleDateTime`指针**NULL**，将删除范围。  
  
### <a name="example"></a>示例  
  请参阅示例[CDateTimeCtrl::GetRange](#getrange)。  
  
##  <a name="settime"></a>CDateTimeCtrl::SetTime  
 在日期和时间选取器控件中设置的时间。  
  
```  
BOOL SetTime(const COleDateTime& timeNew);  
BOOL SetTime(const CTime* pTimeNew);  
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```  
  
### <a name="parameters"></a>参数  
 *timeNew*  
 对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含为控件设置。  
  
 *pTimeNew*  
 在第二个版本更高版本，一个指向[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，其中包含将控件设置的时间。 在上面的指针的第三版[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构，其中包含将控件设置的时间。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[DTM_SETSYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/bb761782)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 中的 MFC 实现**SetTime**，您可以使用`COleDateTime`或`CTime`类，也可以使用`SYSTEMTIME`结构，来设置的时间信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CDateTimeCtrl #&8;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CMNCTRL1](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMonthCalCtrl 类](../../mfc/reference/cmonthcalctrl-class.md)

