---
title: "CSplitterWndEx 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
dev_langs: C++
helpviewer_keywords: CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e45a136941ccaf34108085a14ddefb64bcdb3fa4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="csplitterwndex-class"></a>CSplitterWndEx 类



表示自定义拆分窗口。  
  
## <a name="syntax"></a>语法  
  
```  
class CSplitterWndEx : public CSplitterWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CSplitterWndEx::CSplitterWndEx`|默认构造函数。|  
|`CSplitterWndEx::~CSplitterWndEx`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|由框架调用以绘制拆分窗口。 (重写[CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter)。)|  
  
## <a name="remarks"></a>备注  
 重写`OnDrawSplitter`方法以自定义拆分窗口的图形组件的外观。  
  
 `CSplitterWndEx`类一起配合使用[OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder)， [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox)，和[OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground)方法，它是由视觉管理器实现。 若要使视觉管理器中，若要绘制你的应用程序中的拆分窗口，声明替换`CSplitterWnd`类，该类具有`CSplitterWndEx`类。 为应用程序框架窗口，拆分器窗口类位于 mainfrm.h CMainFrame 类中声明。 有关示例，请参阅`OutlookDemo`示例示例目录中。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 [CSplitterWnd](csplitterwnd-class.md)  
   
## <a name="requirements"></a>要求  
 **标头：** afxsplitterwndex.h  
  
##  <a name="ondrawsplitter"></a>CSplitterWndEx::OnDrawSplitter  
 由框架调用以绘制拆分窗口。  
  
```  
virtual void OnDrawSplitter(  
   CDC* pDC,  
   ESplitType nType,  
   const CRect& rect   
);  
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的指针。 如果此参数为`NULL`，框架将重新绘制活动窗口。  
  
 [in] `nType`  
 之一`CSplitterWnd::ESplitType`指定要绘制的拆分器窗口元素的枚举值。 有效值为 `splitBox`、`splitBar`、`splitIntersection` 和 `splitBorder`。  
  
 [in] `rect`  
 指定的维数和位置绘制指定的拆分器窗口元素边框。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../hierarchy-chart.md)   
 [类](mfc-classes.md)   
 [CSplitterWnd 类](csplitterwnd-class.md)   
 [CMFCVisualManager 类](cmfcvisualmanager-class.md)