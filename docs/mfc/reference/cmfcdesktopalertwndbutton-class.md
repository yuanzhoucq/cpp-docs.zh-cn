---
title: CMFCDesktopAlertWndButton 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: efabaabdcc3f08a58cb7dc0a7845a56e5238548d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370329"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFCDesktopAlertWndButton 类
允许按钮添加到桌面通知对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCDesktopAlertWndButton : public CMFCButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|||  
|-|-|  
|名称|描述|  
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|默认构造函数。|  
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|名称|描述|  
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|确定是否在警报对话框的标题区域中会显示该按钮。|  
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|确定是否按钮可以关闭警报对话框。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|名称|描述|  
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|一个布尔值，指定是否在警报对话框的标题区域中会显示该按钮。|  
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|一个布尔值，指定是否按钮关闭警报的对话框。|  
  
### <a name="remarks"></a>备注  
 默认情况下，构造函数将设置`m_bIsCaptionButton`和`m_bIsCloseButton`到的数据成员`FALSE`。 父`CMFCDesktopAlertDialog`对象集`m_bIsCaptionButton`到`TRUE`如果按钮位于警报对话框的标题区域中。 `CMFCDesktopAlertDialog`类创建`CMFCDesktopAlertWndButton`对象，用作的按钮，关闭警报对话框框中，并设置`m_bIsCloseButton`到`TRUE`。  
  
 添加`CMFCDesktopAlertWndButton`对象添加到`CMFCDesktopAlertDialog`对象，如要添加任何按钮。 有关详细信息`CMFCDesktopAlertDialog`，请参阅[CMFCDesktopAlertDialog 类](../../mfc/reference/cmfcdesktopalertdialog-class.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`SetImage`中的方法`CMFCDesktopAlertWndButton`类。 此代码片段属于[桌面警报演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxdesktopalertwnd.h  
  
##  <a name="iscaptionbutton"></a>  CMFCDesktopAlertWndButton::IsCaptionButton  
 确定是否在警报对话框的标题区域中会显示该按钮。  
  
```  
BOOL IsCaptionButton() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果按钮显示在标题区域的警报对话框; 则为非 0否则为为 0。  
  
##  <a name="isclosebutton"></a>  CMFCDesktopAlertWndButton::IsCloseButton  
 确定是否按钮可以关闭警报对话框。  
  
```  
BOOL IsCloseButton() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果按钮可以关闭警报的对话框; 则为非 0否则为为 0。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertDialog 类](../../mfc/reference/cmfcdesktopalertdialog-class.md)
