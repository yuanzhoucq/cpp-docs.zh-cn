---
title: "CMFCRibbonMainPanel 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonMainPanel
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonMainPanel class
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 3fc37a953e62e6ea90de8402b7f2912b06967e13
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonmainpanel-class"></a>CMFCRibbonMainPanel 类
实现在单击时显示的功能区面板[而 CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonMainPanel : public CMFCRibbonPanel  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|默认构造函数。|  
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonMainPanel::Add](#add)|将功能区元素添加到应用程序按钮面板的左窗格中。 (重写[CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。)|  
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|将文本字符串添加到新的文件列表菜单。|  
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|将功能区元素添加到功能区应用程序面板的底部窗格中。|  
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|将功能区元素添加到应用程序按钮面板的右窗格中。|  
|`CMFCRibbonMainPanel::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|返回表示功能区的主面板的区域的矩形。|  
|`CMFCRibbonMainPanel::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
  
## <a name="remarks"></a>备注  
 框架显示`CMFCRibbonMainPanel`当打开应用程序面板。 它包含三个窗格︰  
  
-   左的窗格包含与命令相关联的文件，如**打开**，**保存**，**打印**，和**关闭**。 若要将命令添加到此窗格中，调用[CMFCRibbonMainPanel::Add](#add)。  
  
-   右窗格中包含修改的左窗格中单击该命令的选项。 例如，如果您单击**另存为**从左窗格中，右窗格中可以显示可用的文件类型。 若要将某项添加到此窗格中，调用[CMFCRibbonMainPanel::AddToRight](#addtoright)。  
  
-   底部窗格中包含允许您更改应用程序的设置并退出程序的按钮。 若要将某项添加到此窗格中，调用[CMFCRibbonMainPanel::AddToBottom](#addtobottom)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)  
  
 [CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxRibbonMainPanel.h  
  
##  <a name="a-nameadda--cmfcribbonmainpaneladd"></a><a name="add"></a>CMFCRibbonMainPanel::Add  
 将功能区元素添加到应用程序按钮面板的左窗格中。  
  
```  
virtual void Add(CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pElem`  
 指向要向主面板中添加的功能区元素的指针。  
  
### <a name="remarks"></a>备注  
 向面板中添加功能区元素。 使用此方法添加的元素将位于左侧列的主面板中。  
  
##  <a name="a-nameaddrecentfileslista--cmfcribbonmainpaneladdrecentfileslist"></a><a name="addrecentfileslist"></a>CMFCRibbonMainPanel::AddRecentFilesList  
 将文本字符串添加到新的文件列表菜单。  
  
```  
void AddRecentFilesList(
    LPCTSTR lpszLabel,  
    int nWidth = 300);
```  
  
### <a name="parameters"></a>参数  
 `lpszLabel`  
 指定要添加到最近的文件列表的字符串。  
  
 `nWidth`  
 指定以像素为单位的最新的文件列表面板的宽度。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddtobottoma--cmfcribbonmainpaneladdtobottom"></a><a name="addtobottom"></a>CMFCRibbonMainPanel::AddToBottom  
 将功能区元素添加到功能区应用程序面板的底部窗格中。  
  
```  
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pElem`  
 指向要添加到的主面板底部的功能区元素的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddtorighta--cmfcribbonmainpaneladdtoright"></a><a name="addtoright"></a>CMFCRibbonMainPanel::AddToRight  
 将功能区元素添加到应用程序按钮面板的右窗格中。  
  
```  
void AddToRight(
    CMFCRibbonBaseElement* pElem,  
    int nWidth = 300);
```  
  
### <a name="parameters"></a>参数  
 `pElem`  
 指向要添加到主面板右侧的功能区元素的指针。  
  
 `nWidth`  
 指定以像素为单位的右侧面板的宽度。  
  
### <a name="remarks"></a>备注  
 此函数用于将功能区元素添加到的右侧面板。 右侧面板中通常会显示最新的文件列表中，但您可以添加以下任何其他功能区元素。  
  
##  <a name="a-namegetcommandsframea--cmfcribbonmainpanelgetcommandsframe"></a><a name="getcommandsframe"></a>CMFCRibbonMainPanel::GetCommandsFrame  
 返回表示功能区的主面板的区域的矩形。  
  
```  
CRect GetCommandsFrame() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个表示功能区的主面板的区域的矩形。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel 类](../../mfc/reference/cmfcribbonpanel-class.md)

