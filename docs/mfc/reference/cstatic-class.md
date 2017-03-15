---
title: "CStatic 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStatic
dev_langs:
- C++
helpviewer_keywords:
- enhanced metafiles
- cursors, displaying
- static controls
- controls [MFC], static
- icons, displaying
- CStatic class
- enhanced metafiles, displaying
- bitmaps, displaying
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
caps.latest.revision: 21
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
ms.openlocfilehash: 0209fad1b84b782cdec7927cb5a04e9bb3083d64
ms.lasthandoff: 02/24/2017

---
# <a name="cstatic-class"></a>CStatic 类
提供 Windows 静态控件功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CStatic : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CStatic::CStatic](#cstatic)|构造 `CStatic` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CStatic::Create](#create)|创建 Windows 静态控件，并将其附加到`CStatic`对象。|  
|[CStatic::DrawItem](#drawitem)|若要绘制一个所有者描述的静态控件的替代。|  
|[CStatic::GetBitmap](#getbitmap)|检索与以前设置的位图的句柄[SetBitmap](#setbitmap)。|  
|[CStatic::GetCursor](#getcursor)|检索与以前设置的光标图像的句柄[SetCursor](#setcursor)。|  
|[CStatic::GetEnhMetaFile](#getenhmetafile)|检索与以前设置的增强型图元文件的句柄[SetEnhMetaFile](#setenhmetafile)。|  
|[CStatic::GetIcon](#geticon)|检索与以前设置的图标的句柄[SetIcon](#seticon)。|  
|[CStatic::SetBitmap](#setbitmap)|指定要在静态控件中显示的位图。|  
|[CStatic::SetCursor](#setcursor)|指定要在静态控件中显示的光标图像。|  
|[CStatic::SetEnhMetaFile](#setenhmetafile)|指定要在静态控件中显示增强型图元文件。|  
|[CStatic::SetIcon](#seticon)|指定要在静态控件中显示的图标。|  
  
## <a name="remarks"></a>备注  
 静态控件显示的文本字符串、 框、 矩形、 图标、 光标、 位图或增强型图元文件。 它可以用于添加标签、 框中，或单独的其他控件。 静态控件通常不接受任何输入，并不提供任何输出;但是，它可以通知其父级的鼠标单击操作，如果使用创建**SS_NOTIFY**样式。  
  
 在两个步骤中创建静态控件。 首先，调用构造函数来构造`CStatic`对象，然后调用[创建](#create)成员函数来创建静态控件并将其附加到`CStatic`对象。  
  
 如果您创建`CStatic`（通过对话框资源） 的对话框内的对象`CStatic`当用户关闭对话框中，将自动销毁对象。  
  
 如果您创建`CStatic`对象在窗口中，您可能还需要将其销毁。 一个`CStatic`的时间段内堆栈上创建的对象将自动销毁。 如果您创建`CStatic`使用堆上的对象**新**函数，则必须调用**删除**上要完成此操作与之对其进行销毁的对象。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatic`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="a-namecreatea--cstaticcreate"></a><a name="create"></a>CStatic::Create  
 创建 Windows 静态控件，并将其附加到`CStatic`对象。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszText,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID = 0xffff);
```  
  
### <a name="parameters"></a>参数  
 `lpszText`  
 指定要放置在控件中的文本。 如果**NULL**，没有文本将可见。  
  
 `dwStyle`  
 指定静态控件的窗口样式。 应用的任意组合[静态控件样式](../../mfc/reference/static-styles.md)到控件。  
  
 `rect`  
 指定的位置和静态控件的大小。 它可为`RECT`结构或`CRect`对象。  
  
 `pParentWnd`  
 指定`CStatic`父窗口中，通常`CDialog`对象。 它不能**NULL**。  
  
 `nID`  
 指定静态控件的控件 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 构造`CStatic`两个步骤中的对象。 首先，调用构造函数`CStatic`，然后调用**创建**，它创建 Windows 静态控件并将其附加到`CStatic`对象。  
  
 将应用以下[窗口样式](../../mfc/reference/window-styles.md)到静态控件︰  
  
- **WS_CHILD**始终  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
 如果您打算在静态控件中显示位图、 光标、 图标或图元文件，您将需要应用以下项之一[静态样式](../../mfc/reference/static-styles.md):  
  
- **SS_BITMAP**针对位图使用此样式。  
  
- **SS_ICON**光标和图标使用此样式。  
  
- **SS_ENHMETAFILE**对增强型图元文件中使用此样式。  
  
 对于游标、 位图或图标，可能还想要使用下列样式︰  
  
- **SS_CENTERIMAGE**使用来居中对齐静态控件中的图像。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic #&1;](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]  
  
##  <a name="a-namecstatica--cstaticcstatic"></a><a name="cstatic"></a>CStatic::CStatic  
 构造 `CStatic` 对象。  
  
```  
CStatic();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic #&2;](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]  
  
##  <a name="a-namedrawitema--cstaticdrawitem"></a><a name="drawitem"></a>CStatic::DrawItem  
 由框架来绘制一个所有者描述的静态控件调用。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDrawItemStruct`  
 一个指向[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)结构。 该结构包含有关要绘制的项和绘图所需的类型信息。  
  
### <a name="remarks"></a>备注  
 重写此函数可实现绘制一个所有者绘制的**CStatic**对象 (该控件具有该样式**SS_OWNERDRAW**)。  
  
##  <a name="a-namegetbitmapa--cstaticgetbitmap"></a><a name="getbitmap"></a>CStatic::GetBitmap  
 获取在位图中，与以前设置的句柄[SetBitmap](#setbitmap)，也就是说，与关联`CStatic`。  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前位图的句柄或**NULL**如果未不设置任何位图。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic #&3;](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="a-namegetcursora--cstaticgetcursor"></a><a name="getcursor"></a>CStatic::GetCursor  
 获取光标，与以前设置的句柄[SetCursor](#setcursor)，也就是说，与关联`CStatic`。  
  
```  
HCURSOR GetCursor();
```  
  
### <a name="return-value"></a>返回值  
 当前光标的句柄或**NULL**如果尚未设置无游标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic #&4;](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="a-namegetenhmetafilea--cstaticgetenhmetafile"></a><a name="getenhmetafile"></a>CStatic::GetEnhMetaFile  
 获取增强型图元文件，与以前设置的句柄[SetEnhMetafile](#setenhmetafile)，也就是说，与关联`CStatic`。  
  
```  
HENHMETAFILE GetEnhMetaFile() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的增强型元文件的句柄或**NULL**如果未不设置任何增强型图元文件。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic #&5;](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="a-namegeticona--cstaticgeticon"></a><a name="geticon"></a>CStatic::GetIcon  
 获取与以前设置的图标的句柄[SetIcon](#seticon)，也就是说，与关联`CStatic`。  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前图标的句柄或**NULL**如果尚未设置无图标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic #&6;](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
##  <a name="a-namesetbitmapa--cstaticsetbitmap"></a><a name="setbitmap"></a>CStatic::SetBitmap  
 将新位图与静态控件相关联。  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>参数  
 `hBitmap`  
 要在静态控件中绘制的位图的句柄。  
  
### <a name="return-value"></a>返回值  
 以前与静态控件相关联的位图的句柄或`NULL`如果不使用位图与静态控件相关联。  
  
### <a name="remarks"></a>备注  
 将静态控件中自动绘制位图。 默认情况下，它将在窗口左上角中绘制和静态控件的大小将调整为位图的大小。  
  
 您可以使用各种窗口和静态控制样式，其中包括︰  
  
-   SS_BITMAP 针对位图始终使用此样式。  
  
-   SS_CENTERIMAGE 用于 center 静态控件中的图像。 如果图像大于静态控件，则将剪辑元素。 如果该值小于静态控件，将位图左上角的像素颜色数据填充在图像周围的空白区域。  
  
-   MFC 提供一种类`CBitmap`，您可以在您需要执行更多与位图图像不是只需调用 Win32 函数时使用`LoadBitmap`。 `CBitmap`其中包含一种类型的 GDI 对象中经常会用与合作`CStatic`，即`CWnd`用于为静态控件中显示图形对象的类。  
  
 `CImage`是一个 ATL/MFC 类，使您能够更轻松地使用设备无关位图 (DIB)。 有关详细信息，请参阅[CImage 类](../../atl-mfc-shared/reference/cimage-class.md)。  
  
-   典型的用法是为提供`CStatic::SetBitmap`的 HBITMAP 运算符返回的 GDI 对象`CBitmap`或`CImage`对象。 若要执行此操作的代码类似于下面的行。  
  
```  
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```  
下面的示例创建两个`CStatic`堆上的对象。 然后将加载另一个使用系统位图使用`CBitmap::LoadOEMBitmap`和其他文件中使用`CImage::Load`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic #&3;](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="a-namesetcursora--cstaticsetcursor"></a><a name="setcursor"></a>CStatic::SetCursor  
 将新的光标图像与静态控件相关联。  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>参数  
 `hCursor`  
 要在静态控件中绘制的光标的句柄。  
  
### <a name="return-value"></a>返回值  
 以前与静态控件中，光标的句柄或**NULL**如果无游标与静态控件相关联。  
  
### <a name="remarks"></a>备注  
 光标将自动绘制静态控件中。 默认情况下，它将在窗口左上角中绘制和静态控制将调整为光标的大小。  
  
 您可以使用各种窗口和静态控制样式，其中包括︰  
  
- **SS_ICON**光标和图标始终使用此样式。  
  
- **SS_CENTERIMAGE**使用静态控件中居中。 如果图像大于静态控件，则将剪辑元素。 如果它小于静态控件，将用静态控件的背景色填充在图像周围的空白区域。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic #&4;](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="a-namesetenhmetafilea--cstaticsetenhmetafile"></a><a name="setenhmetafile"></a>CStatic::SetEnhMetaFile  
 将新的增强型图元文件映像与静态控件相关联。  
  
```  
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```  
  
### <a name="parameters"></a>参数  
 `hMetaFile`  
 要在静态控件中绘制的增强型图元文件的句柄。  
  
### <a name="return-value"></a>返回值  
 以前与静态控件关联的增强型图元文件的句柄或**NULL**如果没有增强型图元文件与静态控件相关联。  
  
### <a name="remarks"></a>备注  
 增强型图元文件将自动绘制静态控件中。 增强型图元文件进行缩放以适合静态控件的大小。  
  
 您可以使用各种窗口和静态控制样式，其中包括︰  
  
- **SS_ENHMETAFILE**对增强型图元文件始终使用此样式。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic #&5;](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="a-nameseticona--cstaticseticon"></a><a name="seticon"></a>CStatic::SetIcon  
 将新的图标图像与静态控件相关联。  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>参数  
 `hIcon`  
 要在静态控件中绘制的图标的句柄。  
  
### <a name="return-value"></a>返回值  
 以前与静态控件关联的图标的句柄或**NULL**无图标是否与静态控件相关联。  
  
### <a name="remarks"></a>备注  
 该图标将自动绘制静态控件中。 默认情况下，它将在窗口左上角中绘制和静态控件的大小将调整为图标的大小。  
  
 您可以使用各种窗口和静态控制样式，其中包括︰  
  
- **SS_ICON**光标和图标始终使用此样式。  
  
- **SS_CENTERIMAGE**使用静态控件中居中。 如果图像大于静态控件，则将剪辑元素。 如果它小于静态控件，将用静态控件的背景色填充在图像周围的空白区域。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic #&6;](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CButton 类](../../mfc/reference/cbutton-class.md)   
 [CComboBox 类](../../mfc/reference/ccombobox-class.md)   
 [CEdit 类](../../mfc/reference/cedit-class.md)   
 [CListBox 类](../../mfc/reference/clistbox-class.md)   
 [CScrollBar 类](../../mfc/reference/cscrollbar-class.md)   
 [CDialog 类](../../mfc/reference/cdialog-class.md)

