---
title: CMFCPropertyGridToolTipCtrl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 227c7d43334419326670dae5fabad28d18ec58a0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716161"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl 类
实现工具提示控件的[CMFCPropertyGridCtrl 类](../../mfc/reference/cmfcpropertygridctrl-class.md)用于显示工具提示。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCPropertyGridToolTipCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|||  
|-|-|  
|名称|描述|  
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|构造 `CMFCPropertyGridToolTipCtrl` 对象。|  
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|名称|描述|  
|[CMFCPropertyGridToolTipCtrl::Create](#create)|创建工具提示控件的窗口。|  
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|停用并隐藏工具提示控件。|  
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|返回工具提示控件的最后一个位置的坐标。|  
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|隐藏工具提示控件。|  
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|类使用[CWinApp](../../mfc/reference/cwinapp-class.md)窗口消息调度到之前转换[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)并[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函数。 （重写 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。）|  
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|设置工具提示文本和工具提示窗口的边框之间的间距。|  
|[CMFCPropertyGridToolTipCtrl::Track](#track)|显示工具提示控件。|  
  
## <a name="remarks"></a>备注  
 当指针停留在属性名称上时显示工具提示。 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)类显示工具提示，以便用户可以轻松地读取。 通常情况下，工具提示的位置是由指针的位置来确定。 通过使用此类，工具提示将出现在属性名称和类似于自然属性扩展中，从而使属性名称完全可见。  
  
 MFC 自动创建此控件，并使用它在[CMFCPropertyGridCtrl 类](../../mfc/reference/cmfcpropertygridctrl-class.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCPropertyGridToolTipCtrl`类，以及如何显示工具提示控件。  
  
 [!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxpropertygridtooltipctrl.h  
  
##  <a name="cmfcpropertygridtooltipctrl"></a>  CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl  
 构造 `CMFCPropertyGridToolTipCtrl` 对象。  
  
```  
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```  
  
##  <a name="create"></a>  CMFCPropertyGridToolTipCtrl::Create  
 创建工具提示控件的窗口。  
  
```  
BOOL Create(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>参数  
*pWndParent*<br/>
[in]指向父窗口的指针。  
  
### <a name="return-value"></a>返回值  
 如果已成功创建窗口; 则为 TRUE否则为 FALSE。  
  
##  <a name="deactivate"></a>  CMFCPropertyGridToolTipCtrl::Deactivate  
 停用并隐藏工具提示控件。  
  
```  
void Deactivate();
```  
  
### <a name="remarks"></a>备注  
 此方法设置的最后一个位置和文本为空值，以便以后调用[CMFCPropertyGridToolTipCtrl::Track](#track)显示工具提示。  
  
##  <a name="getlastrect"></a>  CMFCPropertyGridToolTipCtrl::GetLastRect  
 返回工具提示控件的最后一个位置的坐标。  
  
```  
void GetLastRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>参数  
*rect*<br/>
[out]包含工具提示控件的最后一个位置。  
  
##  <a name="hide"></a>  CMFCPropertyGridToolTipCtrl::Hide  
 隐藏工具提示控件。  
  
```  
void Hide();
```  
  
##  <a name="settextmargin"></a>  CMFCPropertyGridToolTipCtrl::SetTextMargin  
 设置工具提示文本和工具提示窗口的边框之间的间距。  
  
```  
void SetTextMargin(int nTextMargin);
```  
  
### <a name="parameters"></a>参数  
*nTextMargin*<br/>
[in]指定工具提示控件文本和工具提示窗口的边框之间的间距。 默认值为 10 个像素。  
  
##  <a name="track"></a>  CMFCPropertyGridToolTipCtrl::Track  
 显示工具提示控件。  
  
```  
void Track(
    CRect rect,  
    const CString& strText);
```  
  
### <a name="parameters"></a>参数  
*rect*<br/>
[in]指定的位置和大小的工具提示控件。  
  
*strText*<br/>
[in]指定要在工具提示中显示的文本。  
  
### <a name="remarks"></a>备注  
 此方法显示工具提示控件的位置和大小由指定*rect*。 如果自上次调用此方法未更改位置、 大小和文本，则此方法无效。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)
