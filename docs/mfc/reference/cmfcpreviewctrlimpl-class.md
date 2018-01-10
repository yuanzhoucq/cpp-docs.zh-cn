---
title: "CMFCPreviewCtrlImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::Create
- AFXWIN/CMFCPreviewCtrlImpl::Destroy
- AFXWIN/CMFCPreviewCtrlImpl::Focus
- AFXWIN/CMFCPreviewCtrlImpl::GetDocument
- AFXWIN/CMFCPreviewCtrlImpl::Redraw
- AFXWIN/CMFCPreviewCtrlImpl::SetDocument
- AFXWIN/CMFCPreviewCtrlImpl::SetHost
- AFXWIN/CMFCPreviewCtrlImpl::SetPreviewVisuals
- AFXWIN/CMFCPreviewCtrlImpl::SetRect
- AFXWIN/CMFCPreviewCtrlImpl::DoPaint
- AFXWIN/CMFCPreviewCtrlImpl::m_clrBackColor
- AFXWIN/CMFCPreviewCtrlImpl::m_clrTextColor
- AFXWIN/CMFCPreviewCtrlImpl::m_font
- AFXWIN/CMFCPreviewCtrlImpl::m_pDocument
dev_langs: C++
helpviewer_keywords:
- CMFCPreviewCtrlImpl [MFC], CMFCPreviewCtrlImpl
- CMFCPreviewCtrlImpl [MFC], Create
- CMFCPreviewCtrlImpl [MFC], Destroy
- CMFCPreviewCtrlImpl [MFC], Focus
- CMFCPreviewCtrlImpl [MFC], GetDocument
- CMFCPreviewCtrlImpl [MFC], Redraw
- CMFCPreviewCtrlImpl [MFC], SetDocument
- CMFCPreviewCtrlImpl [MFC], SetHost
- CMFCPreviewCtrlImpl [MFC], SetPreviewVisuals
- CMFCPreviewCtrlImpl [MFC], SetRect
- CMFCPreviewCtrlImpl [MFC], DoPaint
- CMFCPreviewCtrlImpl [MFC], m_clrBackColor
- CMFCPreviewCtrlImpl [MFC], m_clrTextColor
- CMFCPreviewCtrlImpl [MFC], m_font
- CMFCPreviewCtrlImpl [MFC], m_pDocument
ms.assetid: 06257fa0-54c9-478d-9d68-c9698c3f93ed
caps.latest.revision: "28"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8def8a8085bebdd09ce58cb6d9abd026fe713fe8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl 类
此类实现位于 Shell 提供用于丰富预览的宿主窗口的窗口。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCPreviewCtrlImpl : public CWnd;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl](#dtor)|Destructs 预览控件对象。|  
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|构造预览控件对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::Create](#create)|已重载。 由要创建 Windows 窗口的丰富预览处理程序调用。|  
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|在需要销毁该控件时，由丰富预览处理程序调用。|  
|[CMFCPreviewCtrlImpl::Focus](#focus)|设置输入到此控件的焦点。|  
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|返回连接到此预览版控件的文档。|  
|[CMFCPreviewCtrlImpl::Redraw](#redraw)|指示此控件重绘。|  
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|由要创建的文档实现和预览控件之间的关系的预览处理程序调用。|  
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|设置此控件的新父级。|  
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|由调用丰富预览处理程序需要设置的丰富预览的视觉对象时内容。|  
|[CMFCPreviewCtrlImpl::SetRect](#setrect)|设置此控件的新边框。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::DoPaint](#dopaint)|由框架调用以呈现预览。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::m_clrBackColor](#m_clrbackcolor)|预览窗口的背景色。|  
|[CMFCPreviewCtrlImpl::m_clrTextColor](#m_clrtextcolor)|预览窗口文本颜色。|  
|[CMFCPreviewCtrlImpl::m_font](#m_font)|用于在预览窗口中显示文本的字体。|  
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|指向其内容在控件中预览的文档的指针。|  
  
## <a name="requirements"></a>惠?  
 **标头:** afxwin.h    
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimpl"></a>CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
构造预览控件对象。

### <a name="syntax"></a>语法
CMFCPreviewCtrlImpl();  

## <a name="create"></a>CMFCPreviewCtrlImpl::Create
已重载。 由要创建 Windows 窗口的丰富预览处理程序调用。  
  
### <a name="syntax"></a>语法  
  
```  
virtual BOOL Create(  
   HWND hWndParent,  
   const RECT* prc  
);  
virtual BOOL Create(  
   HWND hWndParent,  
   const RECT* prc,  
   CCreateContext* pContext  
);  
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 Shell 提供用于丰富预览主机窗口的句柄。  
  
 `prc`  
 指定的初始大小和窗口的位置。  
  
 `pContext`  
 指向创建上下文的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果创建成功;否则为`FALSE`。  
  
## <a name="destroy"></a>CMFCPreviewCtrlImpl::Destroy
在需要销毁该控件时，由丰富预览处理程序调用。  
  
### <a name="syntax"></a>语法  
  
```  
virtual void Destroy();  
```  
  
## <a name="dopaint"></a>CMFCPreviewCtrlImpl::DoPaint  
由框架调用以呈现预览。  
  
### <a name="syntax"></a>语法  
  
```  
virtual void DoPaint(  
   CPaintDC* pDC  
);  
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向绘制的设备上下文的指针。  


## <a name="focus"></a>CMFCPreviewCtrlImpl::Focus  
设置输入到此控件的焦点。  
  
### <a name="syntax"></a>语法  
  
```  
virtual void Focus();  
```  
## <a name="getdocument"></a>CMFCPreviewCtrlImpl::GetDocument
返回连接到此预览版控件的文档。  
  
### <a name="syntax"></a>语法  
  
```  
ATL::IDocument* GetDocument();  
```  
  
### <a name="return-value"></a>返回值  
 指向一个文档，在控件中预览其内容的指针。

## <a name="m_clrbackcolor"></a>CMFCPreviewCtrlImpl::m_clrBackColor  
预览窗口的背景色。  
  
### <a name="syntax"></a>语法  
  
```  
COLORREF m_clrBackColor;  
```  

## <a name="m_clrtextcolor"></a>CMFCPreviewCtrlImpl::m_clrTextColor
预览窗口的文本颜色。  
  
### <a name="syntax"></a>语法  
  
```  
COLORREF m_clrTextColor;  
```  
## <a name="m_font"></a>用于在预览窗口中显示文本的 CMFCPreviewCtrlImpl::m_font 字体。  
  
### <a name="syntax"></a>语法  
  
```  
CFont m_font;  
```  
## <a name="m_pdocument"></a>CMFCPreviewCtrlImpl::m_pDocument  
指向其内容在控件中预览的文档的指针。  
  
### <a name="syntax"></a>语法  
  
```  
ATL::IDocument* m_pDocument;  
```  

## <a name="redraw"></a>CMFCPreviewCtrlImpl::Redraw  
指示此控件重绘。  
  
### <a name="syntax"></a>语法  
  
```  
virtual void Redraw();  
```  
## <a name="setdocument"></a>CMFCPreviewCtrlImpl::SetDocument 
由要创建的文档实现和预览控件之间的关系的预览处理程序调用。  
  
### <a name="syntax"></a>语法  
  
```  
void SetDocument(  
   IDocument* pDocument  
);  
```  
  
### <a name="parameters"></a>参数  
 `pDocument`  
 指向文档实现的指针。  

## <a name="sethost"></a>CMFCPreviewCtrlImpl::SetHost  
设置此控件的新父级。  
  
### <a name="syntax"></a>语法  
  
```  
virtual void SetHost(  
   HWND hWndParent  
);  
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 新的父窗口的句柄。  

## <a name="setpreviewvisuals"></a>CMFCPreviewCtrlImpl::SetPreviewVisuals  
由调用丰富预览处理程序需要设置的丰富预览的视觉对象时内容。  
  
### <a name="syntax"></a>语法  
  
```  
virtual void SetPreviewVisuals(  
   COLORREF clrBack,  
   COLORREF clrText,  
   const LOGFONTW *plf  
);  
```  
  
### <a name="parameters"></a>参数  
 `clrBack`  
 预览窗口的背景色。  
  
 `clrText`  
 预览窗口文本颜色。  
  
 `plf`  
 用于在预览窗口中显示文本的字体。 

##  <a name="setrect"></a>CMFCPreviewCtrlImpl::SetRect  
设置此控件的新边框。  
  
### <a name="syntax"></a>语法  
  
```  
virtual void SetRect(  
   const RECT* prc,  
   BOOL bRedraw  
);  
```  
  
### <a name="parameters"></a>参数  
 `prc`  
 指定新的大小和预览控件的位置。  
  
 `bRedraw`  
 指定是否应重绘控件。  
  
### <a name="remarks"></a>备注  
 通常时调整主机控件的设置新的绑定矩形。  

## <a name="dtor"></a>CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl  
Destructs 预览控件对象。  
  
### <a name="syntax"></a>语法  
  
```  
virtual ~CMFCPreviewCtrlImpl();  
```  
  
