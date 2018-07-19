---
title: CMFCPreviewCtrlImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ab9cd717d8e035d9cfc75e0f856af792c392cf7
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848990"
---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl 类
此类实现位于 shell 提供用于丰富预览的宿主窗口的窗口。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCPreviewCtrlImpl : public CWnd;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl](#dtor)|Destructs 预览控件对象。|  
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|构造一个预览控件对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::Create](#create)|已重载。 由丰富的预览处理程序创建 Windows 窗口调用。|  
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|需要销毁此控件时，由丰富的预览处理程序调用。|  
|[CMFCPreviewCtrlImpl::Focus](#focus)|设置输入焦点设置到此控件。|  
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|返回连接到此预览控件的文档。|  
|[CMFCPreviewCtrlImpl::Redraw](#redraw)|指示此控件重绘。|  
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|由要创建的文档实现和预览控件之间的关系的预览处理程序调用。|  
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|设置此控件的新父级。|  
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|由丰富的预览处理程序时调用它需要设置视觉对象的丰富的预览内容。|  
|[CMFCPreviewCtrlImpl::SetRect](#setrect)|设置此控件的新边框。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::DoPaint](#dopaint)|由框架调用以呈现预览。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::m_clrBackColor](#m_clrbackcolor)|预览窗口的背景色。|  
|[CMFCPreviewCtrlImpl::m_clrTextColor](#m_clrtextcolor)|预览窗口的文本颜色。|  
|[CMFCPreviewCtrlImpl::m_font](#m_font)|用于在预览窗口中显示文本的字体。|  
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|一个指向其内容预览控件中的文档。|  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h    
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimpl"></a> CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
构造一个预览控件对象。

### <a name="syntax"></a>语法
CMFCPreviewCtrlImpl();  

## <a name="create"></a> CMFCPreviewCtrlImpl::Create
已重载。 由丰富的预览处理程序创建 Windows 窗口调用。  
  
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
 *hWndParent*  
 用于丰富预览提供 shell 主机窗口的句柄。  
  
 *中华人民共和国*  
 指定的初始大小和窗口的位置。  
  
 *pContext*  
 指向创建上下文的指针。  
  
### <a name="return-value"></a>返回值  
 如果创建成功，则为 TRUE；否则为 FALSE。  
  
## <a name="destroy"></a> CMFCPreviewCtrlImpl::Destroy
需要销毁此控件时，由丰富的预览处理程序调用。  
  
### <a name="syntax"></a>语法  
  
```  
virtual void Destroy();  
```  
  
## <a name="dopaint"></a> CMFCPreviewCtrlImpl::DoPaint  
由框架调用以呈现预览。  
  
### <a name="syntax"></a>语法  
  
```  
virtual void DoPaint(  
   CPaintDC* pDC  
);  
```  
  
### <a name="parameters"></a>参数  
 *pDC*  
 指向用于绘制的设备上下文的指针。  


## <a name="focus"></a> CMFCPreviewCtrlImpl::Focus  
设置输入焦点设置到此控件。  
  
### <a name="syntax"></a>语法  
  
```  
virtual void Focus();  
```  
## <a name="getdocument"></a> CMFCPreviewCtrlImpl::GetDocument
返回连接到此预览控件的文档。  
  
### <a name="syntax"></a>语法  
  
```  
ATL::IDocument* GetDocument();  
```  
  
### <a name="return-value"></a>返回值  
 指向一个文档，其内容预览控件中的指针。

## <a name="m_clrbackcolor"></a> CMFCPreviewCtrlImpl::m_clrBackColor  
预览窗口的背景色。  
  
### <a name="syntax"></a>语法  
  
```  
COLORREF m_clrBackColor;  
```  

## <a name="m_clrtextcolor"></a> CMFCPreviewCtrlImpl::m_clrTextColor
预览窗口的文本颜色。  
  
### <a name="syntax"></a>语法  
  
```  
COLORREF m_clrTextColor;  
```  
## <a name="m_font"></a> CMFCPreviewCtrlImpl::m_font 用来在预览窗口中显示的文本字体。  
  
### <a name="syntax"></a>语法  
  
```  
CFont m_font;  
```  
## <a name="m_pdocument"></a> CMFCPreviewCtrlImpl::m_pDocument  
一个指向其内容预览控件中的文档。  
  
### <a name="syntax"></a>语法  
  
```  
ATL::IDocument* m_pDocument;  
```  

## <a name="redraw"></a> CMFCPreviewCtrlImpl::Redraw  
指示此控件重绘。  
  
### <a name="syntax"></a>语法  
  
```  
virtual void Redraw();  
```  
## <a name="setdocument"></a> CMFCPreviewCtrlImpl::SetDocument 
由要创建的文档实现和预览控件之间的关系的预览处理程序调用。  
  
### <a name="syntax"></a>语法  
  
```  
void SetDocument(  
   IDocument* pDocument  
);  
```  
  
### <a name="parameters"></a>参数  
 *pDocument*  
 指向文档实现的指针。  

## <a name="sethost"></a> CMFCPreviewCtrlImpl::SetHost  
设置此控件的新父级。  
  
### <a name="syntax"></a>语法  
  
```  
virtual void SetHost(  
   HWND hWndParent  
);  
```  
  
### <a name="parameters"></a>参数  
 *hWndParent*  
 新的父窗口的句柄。  

## <a name="setpreviewvisuals"></a> CMFCPreviewCtrlImpl::SetPreviewVisuals  
由丰富的预览处理程序时调用它需要设置视觉对象的丰富的预览内容。  
  
### <a name="syntax"></a>语法  
  
```  
virtual void SetPreviewVisuals(  
   COLORREF clrBack,  
   COLORREF clrText,  
   const LOGFONTW *plf  
);  
```  
  
### <a name="parameters"></a>参数  
 *clrBack*  
 预览窗口的背景色。  
  
 *clrText*  
 预览窗口的文本颜色。  
  
 *plf*  
 用于在预览窗口中显示文本的字体。 

##  <a name="setrect"></a> CMFCPreviewCtrlImpl::SetRect  
设置此控件的新边框。  
  
### <a name="syntax"></a>语法  
  
```  
virtual void SetRect(  
   const RECT* prc,  
   BOOL bRedraw  
);  
```  
  
### <a name="parameters"></a>参数  
 *中华人民共和国*  
 指定新的大小和预览控件的位置。  
  
 *bRedraw*  
 指定是否需要重新绘制控件。  
  
### <a name="remarks"></a>备注  
 通常宿主控件在调整大小时设置新边框。  

## <a name="dtor"></a> CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl  
Destructs 预览控件对象。  
  
### <a name="syntax"></a>语法  
  
```  
virtual ~CMFCPreviewCtrlImpl();  
```  
  
