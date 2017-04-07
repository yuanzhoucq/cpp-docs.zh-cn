---
title: "CComboBoxEx 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComboBoxEx
- AFXCMN/CComboBoxEx
- AFXCMN/CComboBoxEx::CComboBoxEx
- AFXCMN/CComboBoxEx::Create
- AFXCMN/CComboBoxEx::CreateEx
- AFXCMN/CComboBoxEx::DeleteItem
- AFXCMN/CComboBoxEx::GetComboBoxCtrl
- AFXCMN/CComboBoxEx::GetEditCtrl
- AFXCMN/CComboBoxEx::GetExtendedStyle
- AFXCMN/CComboBoxEx::GetImageList
- AFXCMN/CComboBoxEx::GetItem
- AFXCMN/CComboBoxEx::HasEditChanged
- AFXCMN/CComboBoxEx::InsertItem
- AFXCMN/CComboBoxEx::SetExtendedStyle
- AFXCMN/CComboBoxEx::SetImageList
- AFXCMN/CComboBoxEx::SetItem
- AFXCMN/CComboBoxEx::SetWindowTheme
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes, CComboBoxEx class
- Windows common controls [C++], extended combo boxes
- common controls [C++], extended combo boxes
- combo boxes [C++], CComboBoxEx class
- Internet Explorer 4.0 common controls
- CComboBoxEx class
ms.assetid: 33ca960a-2409-478c-84a4-a2ee8ecfe8f7
caps.latest.revision: 26
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: e88ed701111b49e3a5d3b32868bfad8e77206086
ms.lasthandoff: 02/24/2017

---
# <a name="ccomboboxex-class"></a>CComboBoxEx 类
通过为图像列表提供支持扩展组合框控件。  
  
## <a name="syntax"></a>语法  
  
```  
class CComboBoxEx : public CComboBox  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|构造 `CComboBoxEx` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CComboBoxEx::Create](#create)|创建组合框，并将其附加到`CComboBoxEx`对象。|  
|[CComboBoxEx::CreateEx](#createex)|创建指定的 Windows 扩展样式组合框中，并将其附加到**ComboBoxEx**对象。|  
|[CComboBoxEx::DeleteItem](#deleteitem)|中移除的项从**ComboBoxEx**控件。|  
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|检索指向子组合框控件。|  
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|检索到的编辑控件部分的句柄**ComboBoxEx**控件。|  
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|检索正在使用的扩展的样式**ComboBoxEx**控件。|  
|[CComboBoxEx::GetImageList](#getimagelist)|检索指向分配给的图像列表的指针**ComboBoxEx**控件。|  
|[CComboBoxEx::GetItem](#getitem)|检索项信息给定**ComboBoxEx**项。|  
|[CComboBoxEx::HasEditChanged](#haseditchanged)|确定用户是否已更改的内容**ComboBoxEx**通过键入来编辑控件。|  
|[CComboBoxEx::InsertItem](#insertitem)|将插入新项目在**ComboBoxEx**控件。|  
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|设置中的扩展的样式**ComboBoxEx**控件。|  
|[CComboBoxEx::SetImageList](#setimagelist)|设置用于的图像列表**ComboBoxEx**控件。|  
|[CComboBoxEx::SetItem](#setitem)|设置中的项的特性**ComboBoxEx**控件。|  
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|设置的视觉样式的扩展组合框控件。|  
  
## <a name="remarks"></a>备注  
 通过使用`CComboBoxEx`若要创建组合框控件，您无需再实现您自己的图像绘制代码。 请改用`CComboBoxEx`到从图像列表的访问映像。  
  
## <a name="image-list-support"></a>图像列表支持  
 在标准组合框中，组合框的所有者负责通过创建为一个所有者描述控件的组合框中绘制图像。 当您使用`CComboBoxEx`，不需要设置的绘制样式**CBS_OWNERDRAWFIXED**和**CBS_HASSTRINGS**因为它们隐式。 否则，您必须编写代码来执行绘制操作。 一个`CComboBoxEx`控件支持每个项的最多三个映像︰ 一个用于为选定的状态，未选中状态，覆盖图像。  
  
## <a name="styles"></a>样式  
 `CComboBoxEx`支持样式**CBS_SIMPLE**， **CBS_DROPDOWN**， **CBS_DROPDOWNLIST**，和**WS_CHILD**。 当创建窗口时，传递的所有其他样式将忽略由该控件。 创建窗口后，您可以提供其他组合框样式通过调用`CComboBoxEx`成员函数[SetExtendedStyle](#setextendedstyle)。 使用这些样式，您可以︰  
  
-   要区分大小写的列表中的组的字符串搜索。  
  
-   创建组合框控件使用斜杠 （/）、 反斜杠 ('\\)，和句点 (。) 作为词分隔符的字符。 这允许用户跳转到字使用键盘快捷方式 CTRL + 箭头。  
  
-   设置组合框控件，以显示或隐藏图像。 如果不显示任何图像，组合框可以删除容纳图像的文本缩进量。  
  
-   创建包括调整其大小，使剪辑更广的组合框，它包含一个窄的组合框控件。  
  
 可以在中进一步描述这些样式标记[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)。  
  
## <a name="item-retention-and-callback-item-attributes"></a>项目的保留时间和回调项属性  
 项信息，如索引的项和图像、 缩进值和文本字符串存储在 Win32 结构[COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 该结构还包含对应于回调标志的成员。  
  
 有关详细的概念性讨论，请参阅[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 `CComboBoxEx`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="ccomboboxex"></a>CComboBoxEx::CComboBoxEx  
 调用此成员函数来创建`CComboBoxEx`对象。  
  
```  
CComboBoxEx();
```  
  
##  <a name="create"></a>CComboBoxEx::Create  
 创建组合框，并将其附加到`CComboBoxEx`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定组合框样式应用到组合框的组合。 请参阅**备注**下面有关样式的详细信息。  
  
 `rect`  
 对引用[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它是位置和组合框的大小。  
  
 `pParentWnd`  
 一个指向[CWnd](../../mfc/reference/cwnd-class.md)对象，它是组合框的父窗口 (通常`CDialog`)。 它不能**NULL**。  
  
 `nID`  
 指定组合框控件 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建对象时，非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 创建`CComboBoxEx`两个步骤中的对象︰  
  
1.  调用[CComboBoxEx](#ccomboboxex)构造`CComboBoxEx`对象。  
  
2.  调用此成员函数，它创建扩展的 Windows 组合框，并将其附加到`CComboBoxEx`对象。  
  
 当您调用**创建**，MFC 初始化的公共控件。  
  
 当您创建组合框中时，可以指定任何或所有以下组合框样式︰  
  
- **CBS_SIMPLE**  
  
- **CBS_DROPDOWN**  
  
- **CBS_DROPDOWNLIST**  
  
- **CBS_AUTOHSCROLL**  
  
- **WS_CHILD**  
  
 当创建窗口时，传递的所有其他样式将被忽略。 **ComboBoxEx**控件还支持会提供其他功能的扩展的样式。 中介绍了这些样式[ComboBoxEx 控件扩展的样式](http://msdn.microsoft.com/library/windows/desktop/bb775742)，请在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 通过调用设置这些样式[SetExtendedStyle](#setextendedstyle)。  
  
 如果您想要扩展的窗口样式用于您的控件，调用[CreateEx](#createex)而不是**创建**。  
  
##  <a name="createex"></a>CComboBoxEx::CreateEx  
 调用此函数可创建扩展的组合框控件 （子窗口） 并将其与关联`CComboBoxEx`对象。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwExStyle`  
 指定要创建的控件的扩展的样式。 扩展窗口样式的列表，请参阅`dwExStyle`参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 组合框控件的样式。 请参阅[创建](#create)有关样式的列表。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构的结构描述的大小和窗口，在中创建的工作区坐标位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是**创建**应用扩展的窗口样式、 指定的 Windows 扩展的样式前言**WS_EX_**。  
  
 `CreateEx`创建具有指定的扩展窗口样式控件`dwExStyle`。 您必须设置扩展的样式特定于扩展的组合框控件使用[SetExtendedStyle](#setextendedstyle)。 例如，使用`CreateEx`设置作为此类样式**WS_EX_CONTEXTHELP**，但使用`SetExtendedStyle`设置作为此类样式**CBES_EX_CASESENSITIVE**。 有关详细信息，请参阅主题中介绍的样式[ComboBoxEx 控件扩展样式](http://msdn.microsoft.com/library/windows/desktop/bb775742)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="deleteitem"></a>CComboBoxEx::DeleteItem  
 中移除的项从**ComboBoxEx**控件。  
  
```  
int DeleteItem(int iIndex);
```  
  
### <a name="parameters"></a>参数  
 `iIndex`  
 要删除的项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 在控件中剩余的项目数。 如果`iIndex`是无效的该函数将返回**CB_ERR**。  
  
### <a name="remarks"></a>备注  
 此成员函数实现消息的功能[CBEM_DELETEITEM](http://msdn.microsoft.com/library/windows/desktop/bb775768)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 当您调用 DeleteItem [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)消息**CBEN_DELETEITEM**通知将发送到父窗口。  
  
##  <a name="getcomboboxctrl"></a>CComboBoxEx::GetComboBoxCtrl  
 调用此成员函数以获取指向一个组合框控件中的指针`CComboBoxEx`对象。  
  
```  
CComboBox* GetComboBoxCtrl();
```  
  
### <a name="return-value"></a>返回值  
 一个指向`CComboBox`对象。  
  
### <a name="remarks"></a>备注  
 `CComboBoxEx`控件包含一个父窗口，其中封装`CComboBox`。  
  
 `CComboBox`指向返回的值的对象是临时对象，并在下一步的空闲处理期间被销毁。  
  
##  <a name="geteditctrl"></a>CComboBoxEx::GetEditCtrl  
 调用此成员函数可为组合框的编辑控件中获取的指针。  
  
```  
CEdit* GetEditCtrl();
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CEdit](../../mfc/reference/cedit-class.md)对象。  
  
### <a name="remarks"></a>备注  
 一个`CComboBoxEx`控件与创建时使用的编辑框**CBS_DROPDOWN**样式。  
  
 `CEdit`指向返回的值的对象是临时对象，并在下一步的空闲处理期间被销毁。  
  
##  <a name="getextendedstyle"></a>CComboBoxEx::GetExtendedStyle  
 调用此成员函数以获取用于扩展的样式`CComboBoxEx`控件。  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 `DWORD`值，该值包含用于组合框控件的扩展的样式。  
  
### <a name="remarks"></a>备注  
 请参阅[ComboBoxEx 控件扩展样式](http://msdn.microsoft.com/library/windows/desktop/bb775742)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]这些样式有关的详细信息。  
  
##  <a name="getimagelist"></a>CComboBoxEx::GetImageList  
 调用此成员函数以获取指向使用的图像列表的指针`CComboBoxEx`控件。  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CImageList](../../mfc/reference/cimagelist-class.md)对象。 如果失败，则此成员函数将返回**NULL**。  
  
### <a name="remarks"></a>备注  
 `CImageList`指向返回的值的对象是临时对象，并在下一步的空闲处理期间被销毁。  
  
##  <a name="getitem"></a>CComboBoxEx::GetItem  
 检索项信息给定**ComboBoxEx**项。  
  
```  
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```  
  
### <a name="parameters"></a>参数  
 `pCBItem`  
 一个指向[COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746)结构，它将会收到项信息。  
  
### <a name="return-value"></a>返回值  
 如果该操作成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现消息的功能[CBEM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb775779)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="haseditchanged"></a>CComboBoxEx::HasEditChanged  
 确定用户是否已更改的内容**ComboBoxEx**通过键入来编辑控件。  
  
```  
BOOL HasEditChanged();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果用户已在控件的编辑框中，键入否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现消息的功能[CBEM_HASEDITCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb775782)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="insertitem"></a>CComboBoxEx::InsertItem  
 将插入新项目在**ComboBoxEx**控件。  
  
```  
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```  
  
### <a name="parameters"></a>参数  
 `pCBItem`  
 一个指向[COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746)结构，它将会收到项信息。 此结构包含项的回调标志值。  
  
### <a name="return-value"></a>返回值  
 此时，如果成功，则已插入新项的索引否则为-1。  
  
### <a name="remarks"></a>备注  
 当您调用`InsertItem`、 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)消息[CBEN_INSERTITEM](http://msdn.microsoft.com/library/windows/desktop/bb775764)通知将发送到父窗口。  
  
##  <a name="setextendedstyle"></a>CComboBoxEx::SetExtendedStyle  
 调用此成员函数可设置用于扩展控件的组合框的扩展的样式。  
  
```  
DWORD SetExtendedStyle(
    DWORD dwExMask,  
    DWORD dwExStyles);
```  
  
### <a name="parameters"></a>参数  
 `dwExMask`  
 一个`DWORD`值，该值指示在哪种样式`dwExStyles`会受到影响。 中的扩展的样式`dwExMask`将会更改。 将按原样保留所有其他样式。 如果此参数为零，则所有的中的样式`dwExStyles`会受到影响。  
  
 `dwExStyles`  
 一个`DWORD`值，该值包含组合框控件设置为该控件的扩展的样式。  
  
### <a name="return-value"></a>返回值  
 一个`DWORD`值，该值包含以前用于控件的扩展的样式。  
  
### <a name="remarks"></a>备注  
 请参阅[ComboBoxEx 控件扩展样式](http://msdn.microsoft.com/library/windows/desktop/bb775742)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]这些样式有关的详细信息。  
  
 若要创建扩展与扩展的 windows 样式的控件的组合框，使用[CreateEx](#createex)。  
  
##  <a name="setimagelist"></a>CComboBoxEx::SetImageList  
 设置用于的图像列表**ComboBoxEx**控件。  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>参数  
 `pImageList`  
 一个指向`CImageList`对象，其中包含要与使用的图像`CComboBoxEx`控件。  
  
### <a name="return-value"></a>返回值  
 一个指向[CImageList](../../mfc/reference/cimagelist-class.md)对象，它包含以前使用的图像`CComboBoxEx`控件。 **NULL**如果先前不设置任何图像列表。  
  
### <a name="remarks"></a>备注  
 此成员函数实现消息的功能[CBEM_SETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb775787)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如果更改默认的编辑控件的高度，调用 Win32 函数[SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545)调整您的控件，调用后`SetImageList`，或将无法正确显示。  
  
 `CImageList`指向返回的值的对象是临时对象，并在下一步的空闲处理期间被销毁。  
  
##  <a name="setitem"></a>CComboBoxEx::SetItem  
 设置中的项的特性**ComboBoxEx**控件。  
  
```  
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```  
  
### <a name="parameters"></a>参数  
 `pCBItem`  
 一个指向[COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746)结构，它将会收到项信息。  
  
### <a name="return-value"></a>返回值  
 如果该操作成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现消息的功能[CBEM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb775788)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setwindowtheme"></a>CComboBoxEx::SetWindowTheme  
 设置的视觉样式的扩展组合框控件。  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>参数  
 `pszSubAppName`  
 指向一个包含扩展的组合框的视觉样式设置的 Unicode 字符串的指针。  
  
### <a name="return-value"></a>返回值  
 不使用返回的值。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[CBEM_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb775790)消息，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 MFCIE](../../visual-cpp-samples.md)   
 [CComboBox 类](../../mfc/reference/ccombobox-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CComboBox 类](../../mfc/reference/ccombobox-class.md)

