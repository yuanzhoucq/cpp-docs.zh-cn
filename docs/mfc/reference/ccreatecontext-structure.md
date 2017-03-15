---
title: "CCreateContext 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCreateContext
dev_langs:
- C++
helpviewer_keywords:
- CCreateContext structure
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 231f2e44e085d27a2b2cbf289adf7b0521471b0e
ms.lasthandoff: 02/24/2017

---
# <a name="ccreatecontext-structure"></a>CCreateContext 结构
框架将使用`CCreateContext`结构，在创建框架窗口以及与文档相关联的视图时。  
  
## <a name="syntax"></a>语法  
  
```  
struct CCreateContext  
```  
  
## <a name="remarks"></a>备注  
 `CCreateContext`是一种结构，并且没有基类的类。  
  
 创建一个窗口时，此结构中的值提供用来将文档的组件连接到其数据的视图的信息。 只需使用`CCreateContext`如果您要重写创建过程的部分。  
  
 一个`CCreateContext`结构包含文档、 框架窗口、 视图和文档模板的指针。 它还包含一个指向`CRuntimeClass`，它标识要创建的视图类型。 运行时类信息和当前文档指针用于动态创建一个新的视图。 下表建议如何以及何时每个`CCreateContext`可能使用成员︰  
  
|成员|类型|它是什么|  
|------------|----------|--------------------|  
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass`要创建的新视图。|  
|`m_pCurrentDoc`|`CDocument*`|要与新视图相关联的现有文档。|  
|`m_pNewDocTemplate`|`CDocTemplate*`|文档模板创建新的 MDI 框架窗口相关联。|  
|`m_pLastView`|`CView*`|原始视图在其的其他视图进行建模，如下所示的拆分器的窗口视图创建或上一个文档的第二个视图的创建。|  
|`m_pCurrentFrame`|`CFrameWnd*`|框架窗口在其其他框架窗口进行建模，如下所示对文档的第二个框架窗口的创建。|  
  
 当文档模板创建文档和其相关的组件时，它验证中存储的信息`CCreateContext`结构。 例如，不应为不存在的文档创建一个视图。  
  
> [!NOTE]
>  中的指针的所有`CCreateContext`是可选的可以是`NULL`如果未指定或未知。  
  
 `CCreateContext`下面列出的成员函数使用"另请参阅。" 如果您打算对其进行覆盖，请查阅这些函数的说明的特定信息。  
  
 下面是几个一般原则︰  
  
-   如下所示为窗口创建的参数传递时`CWnd::Create`， `CFrameWnd::Create`，和`CFrameWnd::LoadFrame`，创建上下文指定应连接新的窗口。 对于大多数 windows，整个结构都是可选和`NULL`可以将指针传递。  
  
-   对于可重写成员函数，如`CFrameWnd::OnCreateClient`、`CCreateContext`参数是可选的。  
  
-   对于所涉及的成员函数在视图创建过程中，您必须提供足够的信息来创建视图。 例如，对于拆分器窗口中的第一个视图，您必须提供视图类信息和当前文档。  
  
 一般情况下，如果您使用 framework 默认值，则可以忽略`CCreateContext`。 如果你尝试更高级的修改，Microsoft 基础类库的源代码或示例程序，如 VIEWEX，将指导您。 不要忘记了所需的参数，如果框架断言将告诉您忘记了。  
  
 有关详细信息`CCreateContext`，请参阅 MFC 示例[VIEWEX](../../visual-cpp-samples.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** afxext.h  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)   
 [CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)   
 [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)   
 [CSplitterWnd::Create](../../mfc/reference/csplitterwnd-class.md#create)   
 [CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)   
 [Cwnd:: Create](../../mfc/reference/cwnd-class.md#create)


