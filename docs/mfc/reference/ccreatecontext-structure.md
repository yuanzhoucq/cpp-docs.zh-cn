---
title: CCreateContext 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCreateContext
dev_langs:
- C++
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af6e81b9215aa6e7bc9e5f294a1d95aee4b51321
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352039"
---
# <a name="ccreatecontext-structure"></a>CCreateContext 结构
框架将使用`CCreateContext`结构创建的框架窗口和与文档相关联的视图时。  
  
## <a name="syntax"></a>语法  
  
```  
struct CCreateContext  
```  
  
## <a name="remarks"></a>备注  
 `CCreateContext` 是一种结构，并且没有基类。  
  
 当你创建一个窗口时，此结构中的值将提供用于连接到其数据的视图的文档的组件的信息。 只需使用`CCreateContext`如果您要重写的创建过程部分。  
  
 A`CCreateContext`结构包含指向文档、 框架窗口、 视图和文档模板。 它还包含指向的指针`CRuntimeClass`，它标识要创建的视图类型。 运行时类信息和当前文档指针用于动态创建的新视图。 下表提供的建议方式和时间每个`CCreateContext`可能使用成员：  
  
|成员|类型|它是什么|  
|------------|----------|--------------------|  
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass` 要创建的新视图。|  
|`m_pCurrentDoc`|`CDocument*`|要与新视图关联的现有文档。|  
|`m_pNewDocTemplate`|`CDocTemplate*`|与新的 MDI 框架窗口的创建关联的文档模板。|  
|`m_pLastView`|`CView*`|在其附加视图进行建模，如下所示的拆分器窗口视图创建或在文档上的第二个视图创建的原始视图。|  
|`m_pCurrentFrame`|`CFrameWnd*`|在其其他框架窗口进行建模，如下所示在文档上的第二个框架窗口创建框架窗口。|  
  
 当文档模板创建文档和其关联的组件时，它会验证中存储的信息`CCreateContext`结构。 例如，不应为不存在的文档创建视图。  
  
> [!NOTE]
>  中的指针的所有`CCreateContext`是可选的可以是`NULL`如果未指定或未知。  
  
 `CCreateContext` 下面列出的成员函数使用"另请参阅。" 如果你打算重写它们的特定信息，参阅这些函数的说明。  
  
 以下是一些通用准则：  
  
-   当传入为窗口创建的自变量作为`CWnd::Create`， `CFrameWnd::Create`，和`CFrameWnd::LoadFrame`，创建上下文指定应连接的新窗口。 对于大多数 windows，整个结构都是可选和`NULL`可以传递指针。  
  
-   对于可重写成员函数，如`CFrameWnd::OnCreateClient`、`CCreateContext`参数是可选的。  
  
-   对于所涉及的成员函数在视图创建过程中，你必须提供足够的信息来创建视图。 例如，对于在拆分窗口中的第一个视图，必须提供查看类信息和当前文档。  
  
 一般情况下，如果你使用 framework 默认值，则可以忽略`CCreateContext`。 如果你尝试更高级的修改、 Microsoft 基础类库源代码或示例程序，如 VIEWEX，将指导你。 如果你忘记了必需的参数，framework 断言将告诉您忘记了。  
  
 有关详细信息`CCreateContext`，请参阅 MFC 示例[VIEWEX](../../visual-cpp-samples.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** afxext.h  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)   
 [CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)   
 [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)   
 [CSplitterWnd::Create](../../mfc/reference/csplitterwnd-class.md#create)   
 [CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)   
 [Cwnd:: Create](../../mfc/reference/cwnd-class.md#create)

