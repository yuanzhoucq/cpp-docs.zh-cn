---
title: CStatic 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStatic
- AFXWIN/CStatic
- AFXWIN/CStatic::CStatic
- AFXWIN/CStatic::Create
- AFXWIN/CStatic::DrawItem
- AFXWIN/CStatic::GetBitmap
- AFXWIN/CStatic::GetCursor
- AFXWIN/CStatic::GetEnhMetaFile
- AFXWIN/CStatic::GetIcon
- AFXWIN/CStatic::SetBitmap
- AFXWIN/CStatic::SetCursor
- AFXWIN/CStatic::SetEnhMetaFile
- AFXWIN/CStatic::SetIcon
dev_langs:
- C++
helpviewer_keywords:
- CStatic [MFC], CStatic
- CStatic [MFC], Create
- CStatic [MFC], DrawItem
- CStatic [MFC], GetBitmap
- CStatic [MFC], GetCursor
- CStatic [MFC], GetEnhMetaFile
- CStatic [MFC], GetIcon
- CStatic [MFC], SetBitmap
- CStatic [MFC], SetCursor
- CStatic [MFC], SetEnhMetaFile
- CStatic [MFC], SetIcon
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d3b1a5dcfc8481727bffd8b80e0bb1b230d56ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374999"
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
  
|名称|描述|  
|----------|-----------------|  
|[CStatic::Create](#create)|创建 Windows 静态控件并将其附加到`CStatic`对象。|  
|[CStatic::DrawItem](#drawitem)|重写以绘制所有者描述的静态控件。|  
|[CStatic::GetBitmap](#getbitmap)|检索与以前设置的位图的句柄[SetBitmap](#setbitmap)。|  
|[CStatic::GetCursor](#getcursor)|检索与以前设置的光标图像句柄[SetCursor](#setcursor)。|  
|[CStatic::GetEnhMetaFile](#getenhmetafile)|检索与以前设置增强型图元文件的句柄[SetEnhMetaFile](#setenhmetafile)。|  
|[CStatic::GetIcon](#geticon)|检索与以前设置的图标的句柄[SetIcon](#seticon)。|  
|[CStatic::SetBitmap](#setbitmap)|指定静态控件中显示的位图。|  
|[CStatic::SetCursor](#setcursor)|指定要静态控件中显示的光标映像。|  
|[CStatic::SetEnhMetaFile](#setenhmetafile)|指定要显示静态控件中增强型图元文件。|  
|[CStatic::SetIcon](#seticon)|指定要静态控件中显示的图标。|  
  
## <a name="remarks"></a>备注  
 显示静态控件的文本字符串、 框、 矩形、 图标、 光标、 位图或增强型图元文件。 它可以用于框中，或单独的其他控件标志。 静态控件通常将使用没有输入，并提供没有输出;但是，它可以通知鼠标单击其父级，如果使用创建**SS_NOTIFY**样式。  
  
 在两个步骤中创建静态控件。 首先，调用的构造函数来构造`CStatic`对象，然后调用[创建](#create)成员函数以创建静态控件并将其附加到`CStatic`对象。  
  
 如果你创建`CStatic`（通过对话框资源） 对话框中的对象`CStatic`当用户关闭对话框中，将自动销毁对象。  
  
 如果你创建`CStatic`对象在窗口中，你可能还需要将其销毁。 A`CStatic`的时间段内堆栈上创建的对象将自动销毁。 如果你创建`CStatic`使用堆上的对象**新**函数，必须调用**删除**上要使用它完成后销毁它的对象。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatic`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="create"></a>  CStatic::Create  
 创建 Windows 静态控件并将其附加到`CStatic`对象。  
  
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
 指定要放置在控件中的文本。 如果**NULL**，任何文本将可见。  
  
 `dwStyle`  
 指定静态控件的窗口样式。 应用的任意组合[静态控件样式](../../mfc/reference/styles-used-by-mfc.md#static-styles)到控件。  
  
 `rect`  
 指定的位置和静态控件的大小。 它可以是`RECT`结构或`CRect`对象。  
  
 `pParentWnd`  
 指定`CStatic`父窗口，通常`CDialog`对象。 它不能**NULL**。  
  
 `nID`  
 指定静态控件的控件 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 构造`CStatic`两个步骤中的对象。 首先，调用的构造函数`CStatic`，然后调用**创建**，它创建 Windows 静态控件并将其附加到`CStatic`对象。  
  
 将应用以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)到静态控件：  
  
- **WS_CHILD**始终  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
 如果你要显示静态控件中的位图、 光标、 图标或图元文件，你将需要应用以下项之一[静态样式](../../mfc/reference/styles-used-by-mfc.md#static-styles):  
  
- **SS_BITMAP**针对位图使用此样式。  
  
- **SS_ICON**使用此样式的游标和图标。  
  
- **SS_ENHMETAFILE**对增强型图元文件中使用此样式。  
  
 游标、 位图或图标，你可能还想要使用的以下形式：  
  
- **SS_CENTERIMAGE**用于中心中的静态控件的图像。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]  
  
##  <a name="cstatic"></a>  CStatic::CStatic  
 构造 `CStatic` 对象。  
  
```  
CStatic();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]  
  
##  <a name="drawitem"></a>  CStatic::DrawItem  
 由框架调用以绘制所有者描述的静态控件。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDrawItemStruct`  
 指向的指针[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)结构。 结构包含有关要绘制的项和绘图所需的类型信息。  
  
### <a name="remarks"></a>备注  
 重写此函数可实现一个所有者绘制的绘图**CStatic**对象 (该控件具有样式**SS_OWNERDRAW**)。  
  
##  <a name="getbitmap"></a>  CStatic::GetBitmap  
 获取位图，并使用以前设置的句柄[SetBitmap](#setbitmap)，即与关联`CStatic`。  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前位图的句柄或**NULL**如果尚未设置任何位图。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="getcursor"></a>  CStatic::GetCursor  
 获取光标，与以前设置的句柄[SetCursor](#setcursor)，即与关联`CStatic`。  
  
```  
HCURSOR GetCursor();
```  
  
### <a name="return-value"></a>返回值  
 当前的光标的句柄或**NULL**如果尚未设置任何光标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="getenhmetafile"></a>  CStatic::GetEnhMetaFile  
 获取增强型图元文件以使用以前设置的句柄[SetEnhMetafile](#setenhmetafile)，即与关联`CStatic`。  
  
```  
HENHMETAFILE GetEnhMetaFile() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的增强型图元文件的句柄或**NULL**如果尚未设置任何增强型图元文件。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="geticon"></a>  CStatic::GetIcon  
 获取与以前设置的图标的句柄[SetIcon](#seticon)，即与关联`CStatic`。  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前图标的句柄或**NULL**如果已设置无图标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
##  <a name="setbitmap"></a>  CStatic::SetBitmap  
 将新的位图与静态控件相关联。  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>参数  
 `hBitmap`  
 要静态控件中绘制的位图的句柄。  
  
### <a name="return-value"></a>返回值  
 用于静态控件，与以前相关联的位图的句柄或`NULL`如果不使用位图已与静态控件相关联。  
  
### <a name="remarks"></a>备注  
 将静态控件中自动绘制位图。 默认情况下，它将在左上角绘制和静态控件的大小将调整到的位图的大小。  
  
 你可以使用各种窗口和静态控件样式，其中包括：  
  
-   SS_BITMAP 针对位图始终使用此样式。  
  
-   SS_CENTERIMAGE 用于中心中的静态控件的图像。 如果图像大于静态控件，则将剪辑元素。 如果该值小于静态控件，将位图左上角的像素颜色数据填充该图像的周围的空白区域。  
  
-   MFC 提供了类`CBitmap`，你可以在你需要执行更多与位图图像不是只需调用 Win32 函数时使用`LoadBitmap`。 `CBitmap`其中包含一种类型的 GDI 对象中经常会使用与协作`CStatic`，即`CWnd`用于为静态控件显示图形对象的类。  
  
 `CImage` 是一个可让你更轻松地使用设备独立位图 (DIB) 的 ATL/MFC 类。 有关详细信息，请参阅[CImage 类](../../atl-mfc-shared/reference/cimage-class.md)。  
  
-   典型用法就是能够在`CStatic::SetBitmap`的 HBITMAP 运算符返回的 GDI 对象`CBitmap`或`CImage`对象。 要执行此操作的代码类似于以下行。  
  
```  
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```  
下面的示例创建两个`CStatic`堆上的对象。 然后加载一个系统位图使用`CBitmap::LoadOEMBitmap`和从文件使用其他`CImage::Load`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="setcursor"></a>  CStatic::SetCursor  
 将新的光标图像与静态控件相关联。  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>参数  
 `hCursor`  
 要绘制静态控件中的光标句柄。  
  
### <a name="return-value"></a>返回值  
 以前与静态控件，光标的句柄或**NULL**如果没有游标与静态控件相关联。  
  
### <a name="remarks"></a>备注  
 将静态控件中自动绘制光标。 默认情况下，它将在左上角绘制，并将光标的大小调整静态控件的大小。  
  
 你可以使用各种窗口和静态控件样式，其中包括：  
  
- **SS_ICON**的游标和图标始终使用此样式。  
  
- **SS_CENTERIMAGE**使用静态控件中居中。 如果图像大于静态控件，则将剪辑元素。 如果该值小于静态控件，该图像的周围的空白区域将为静态控件的背景色填充。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="setenhmetafile"></a>  CStatic::SetEnhMetaFile  
 将新的增强型图元文件映像与静态控件相关联。  
  
```  
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```  
  
### <a name="parameters"></a>参数  
 `hMetaFile`  
 增强型图元文件绘制静态控件中的句柄。  
  
### <a name="return-value"></a>返回值  
 以前与静态控件，增强型图元文件的句柄或**NULL**如果没有增强型图元文件是与静态控件相关联。  
  
### <a name="remarks"></a>备注  
 将自动将增强型图元文件绘制静态控件中。 增强型图元文件进行缩放以适合静态控件的大小。  
  
 你可以使用各种窗口和静态控件样式，其中包括：  
  
- **SS_ENHMETAFILE**对增强型图元文件始终使用此样式。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="seticon"></a>  CStatic::SetIcon  
 将新的图标图像与静态控件相关联。  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>参数  
 `hIcon`  
 要绘制静态控件中的图标的句柄。  
  
### <a name="return-value"></a>返回值  
 以前与静态控件中，关联的图标的句柄或**NULL**没有图标是否与静态控件相关联。  
  
### <a name="remarks"></a>备注  
 图标将自动绘制静态控件中。 默认情况下，它将在左上角绘制和静态控件的大小将调整到的图标大小。  
  
 你可以使用各种窗口和静态控件样式，其中包括：  
  
- **SS_ICON**的游标和图标始终使用此样式。  
  
- **SS_CENTERIMAGE**使用静态控件中居中。 如果图像大于静态控件，则将剪辑元素。 如果该值小于静态控件，该图像的周围的空白区域将为静态控件的背景色填充。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CButton 类](../../mfc/reference/cbutton-class.md)   
 [CComboBox 类](../../mfc/reference/ccombobox-class.md)   
 [CEdit 类](../../mfc/reference/cedit-class.md)   
 [CListBox 类](../../mfc/reference/clistbox-class.md)   
 [CScrollBar 类](../../mfc/reference/cscrollbar-class.md)   
 [CDialog 类](../../mfc/reference/cdialog-class.md)
