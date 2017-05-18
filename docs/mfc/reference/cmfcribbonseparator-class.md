---
title: "CMFCRibbonSeparator 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::AddToListBox
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CopyFrom
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::GetRegularSize
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsTabStop
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDraw
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDrawOnList
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonSeparator class
- GetThisClass method
- CreateObject method
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 98a58d43b5e6299f26521d873caec06d4581f7b3
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonseparator-class"></a>CMFCRibbonSeparator 类
实现功能区分隔符。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonSeparator : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|||  
|-|-|  
|名称|描述|  
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|构造 `CMFCRibbonSeparator` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|添加到分隔符**命令**列入**自定义**对话框。 (重写[CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox)。)|  
|`CMFCRibbonSeparator::CreateObject`|由框架用于创建此类类型的动态实例。|  
|`CMFCRibbonSeparator::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|从另一个对象设置分隔符的成员变量的复制方法。|  
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|返回一个分隔符的大小。|  
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|指示这是否是一个分隔符。|  
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|指示这是否是一个制表位。|  
|[CMFCRibbonSeparator::OnDraw](#ondraw)|系统会在功能区或快速访问工具栏上绘制分隔符的调用。|  
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|由系统上绘制分隔符调用**命令**列表。|  
  
## <a name="remarks"></a>备注  
 功能区分隔符为垂直或水平行，在逻辑上将功能区元素。 可以在功能区控件、 主应用程序菜单、 功能区状态栏和快速访问工具栏上绘制一个分隔符。  
  
 若要在您的应用程序中使用分隔符，构造新的对象，并将其添加到的主应用程序菜单，如下所示︰  
  
```  
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...  
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```  
调用[CMFCRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator)来将分隔条添加到功能区面板。 分配和内部添加分隔符`AddSeparator`方法。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxbaseribbonelement.h  
  
##  <a name="addtolistbox"></a>CMFCRibbonSeparator::AddToListBox  
 添加到分隔符**命令**列入**自定义**对话框。  
  
```  
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,  
    BOOL bDeep);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndListBox`  
 一个指向**命令**分隔符将添加的列表。  
  
 [in] `bDeep`  
 已忽略。  
  
### <a name="return-value"></a>返回值  
 为指定的列表框中字符串的从零开始索引`pWndListBox`。  
  
##  <a name="cmfcribbonseparator"></a>CMFCRibbonSeparator::CMFCRibbonSeparator  
 构造 `CMFCRibbonSeparator` 对象。  
  
```  
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bIsHoriz`  
 如果`TRUE`，该分隔符是水平; 如果`FALSE`，分隔符是垂直的。  
  
### <a name="remarks"></a>备注  
 在应用程序菜单中使用水平分隔符。 在工具栏中使用垂直分隔符。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCRibbonSeparator`类。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&19;](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]  
  
##  <a name="copyfrom"></a>CMFCRibbonSeparator::CopyFrom  
 从另一个对象设置分隔符的成员变量的复制方法。  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>参数  
 [in] `Src`  
 要从复制的源功能区元素。  
  
##  <a name="getregularsize"></a>CMFCRibbonSeparator::GetRegularSize  
 返回一个分隔符的大小。  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备内容的指针。  
  
### <a name="return-value"></a>返回值  
 在给定的设备上下文的分隔符的大小。  
  
##  <a name="isseparator"></a>CMFCRibbonSeparator::IsSeparator  
 指示这是否是一个分隔符。  
  
```  
virtual BOOL IsSeparator() const;  
```  
  
### <a name="return-value"></a>返回值  
 始终`TRUE`此类。  
  
##  <a name="istabstop"></a>CMFCRibbonSeparator::IsTabStop  
 指示这是否是一个制表位。  
  
```  
virtual BOOL IsTabStop() const;  
```  
  
### <a name="return-value"></a>返回值  
 始终`FALSE`此类。  
  
### <a name="remarks"></a>备注  
 功能区分隔符不是一个制表位。  
  
##  <a name="ondraw"></a>CMFCRibbonSeparator::OnDraw  
 系统会在功能区或快速访问工具栏上绘制分隔符的调用。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
##  <a name="ondrawonlist"></a>CMFCRibbonSeparator::OnDrawOnList  
 由系统上绘制分隔符调用**命令**列表。  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `pDC`|一个指向设备上下文的指针。|  
|[in] `strText`|在列表中显示的文本。|  
|[in] `nTextOffset`|文本和边框的左侧之间的间距。|  
|[in] `rect`|指定的绑定矩形。|  
|[in] `bIsSelected`|已忽略。|  
|[in] `bHighlighted`|已忽略。|  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)

