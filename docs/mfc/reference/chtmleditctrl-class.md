---
title: "CHtmlEditCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditCtrl class
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
caps.latest.revision: 22
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
ms.openlocfilehash: 4aca52508663e94ee9a1b55843ad05613aa40b0b
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="chtmleditctrl-class"></a>CHtmlEditCtrl 类
提供 MFC 窗口中的 WebBrowser ActiveX 控件功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CHtmlEditCtrl: public CWnd,   
    public CHtmlEditCtrlBase<CHtmlEditCtrl>  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|构造 `CHtmlEditCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CHtmlEditCtrl::Create](#create)|创建一个 WebBrowser ActiveX 控件并将其附加到`CHtmlEditCtrl`对象。 此函数会自动将置于编辑模式的 WebBrowser ActiveX 控件。|  
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|检索[IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx)所包含的 web 浏览器控件中当前加载的文档的接口。|  
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|检索默认文档的 URL 以加载所包含的 web 浏览器控件。|  
  
## <a name="remarks"></a>备注  
 将在创建后，托管的 WebBrowser 控件自动置于编辑模式。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHtmlEditCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxhtml.h  
  
##  <a name="chtmleditctrl"></a>CHtmlEditCtrl::CHtmlEditCtrl  
 构造 `CHtmlEditCtrl` 对象。  
  
```  
CHtmlEditCtrl();
```  
  
##  <a name="create"></a>CHtmlEditCtrl::Create  
 创建一个 WebBrowser ActiveX 控件并将其附加到`CHtmlEditCtrl`对象。 WebBrowser ActiveX 控件自动导航到默认文档，然后放在编辑模式，此函数。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszWindowName`  
 未使用此参数。  
  
 `dwStyle`  
 未使用此参数。  
  
 `rect`  
 指定控件的大小和位置。  
  
 `pParentWnd`  
 指定控件的父窗口。 它不能**NULL**。  
  
 `nID`  
 指定控件的 id。  
  
 `pContext`  
 未使用此参数。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
##  <a name="getdhtmldocument"></a>CHtmlEditCtrl::GetDHtmlDocument  
 检索[IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx)所包含的 web 浏览器控件中当前加载的文档的接口  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>参数  
 `ppDocument`  
 文档界面中。  
  
##  <a name="getstartdocument"></a>CHtmlEditCtrl::GetStartDocument  
 检索默认文档的 URL 以加载所包含的 web 浏览器控件。  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)


