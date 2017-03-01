---
title: "CSplitterWndEx 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSplitterWndEx
dev_langs:
- C++
helpviewer_keywords:
- CSplitterWndEx
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
caps.latest.revision: 24
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
ms.sourcegitcommit: 73410ae17465880f455e5b15026f6cc010803c19
ms.openlocfilehash: 08b26bc2321485181941dbaaa9a903de9a401ef8
ms.lasthandoff: 02/24/2017

---
# <a name="csplitterwndex-class"></a>CSplitterWndEx 类



表示自定义拆分窗口。  
  
## <a name="syntax"></a>语法  
  
```  
class CSplitterWndEx : public CSplitterWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|`CSplitterWndEx::CSplitterWndEx`|默认构造函数。|  
|`CSplitterWndEx::~CSplitterWndEx`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|由框架用于绘制拆分器窗口中调用。 (重写[CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter)。)|  
  
## <a name="remarks"></a>备注  
 重写`OnDrawSplitter`方法以自定义拆分窗口将图形组件的外观。  
  
 `CSplitterWndEx`类一起配合使用[OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder)， [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox)，和[OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground)由的可视管理器实现的方法。 若要使视觉管理器中，若要绘制您的应用程序中的拆分窗口，替换的声明`CSplitterWnd`类`CSplitterWndEx`类。 为应用程序框架窗口，在 mainfrm.h 中位于 CMainFrame 类中声明拆分器窗口类。 有关示例，请参阅`OutlookDemo`示例在示例目录中。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 [CSplitterWnd](csplitterwnd-class.md)  
   
## <a name="requirements"></a>要求  
 **标头︰** afxsplitterwndex.h  
  
##  <a name="a-nameondrawsplittera--csplitterwndexondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterWndEx::OnDrawSplitter  
 由框架用于绘制拆分器窗口中调用。  
  
```  
virtual void OnDrawSplitter(  
   CDC* pDC,  
   ESplitType nType,  
   const CRect& rect   
);  
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的指针。 如果此参数为`NULL`，框架将重新绘制活动窗口中。  
  
 [in] `nType`  
 其中一个`CSplitterWnd::ESplitType`枚举值，该值指定要绘制的拆分器窗口元素。 有效值为 `splitBox`、`splitBar`、`splitIntersection` 和 `splitBorder`。  
  
 [in] `rect`  
 指定的尺寸和位置绘制指定的拆分器窗口元素边框。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../hierarchy-chart.md)   
 [类](mfc-classes.md)   
 [CSplitterWnd 类](csplitterwnd-class.md)   
 [CMFCVisualManager 类](cmfcvisualmanager-class.md)
