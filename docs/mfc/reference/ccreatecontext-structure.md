---
title: CCreateContext 结构 |Microsoft Docs
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
ms.openlocfilehash: 320f84a8c423c16c4647108af0154fe7c07ce653
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447292"
---
# <a name="ccreatecontext-structure"></a>CCreateContext 结构

框架使用`CCreateContext`结构创建的框架窗口和与文档相关联的视图时。

## <a name="syntax"></a>语法

```
struct CCreateContext
```

## <a name="remarks"></a>备注

`CCreateContext` 是一种结构，而未一个基类。

当您创建一个窗口时，此结构中的值提供用来连接到其数据的视图的文档的组件的信息。 只需使用`CCreateContext`如果您要重写创建过程的部分。

一个`CCreateContext`结构包含文档、 框架窗口、 视图和文档模板的指针。 它还包含一个指向`CRuntimeClass`以标识要创建视图的类型。 运行时类信息和当前文档指针用于动态创建一个新的视图。 下表建议如何以及何时使用每个`CCreateContext`可能会使用成员：

|成员|类型|它是什么|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass` 若要创建的新视图。|
|`m_pCurrentDoc`|`CDocument*`|要与新视图相关联的现有文档。|
|`m_pNewDocTemplate`|`CDocTemplate*`|与创建新的 MDI 框架窗口关联的文档模板。|
|`m_pLastView`|`CView*`|原始视图在其的其他视图进行建模，如下所示创建拆分器窗口视图或文档的第二个视图的创建。|
|`m_pCurrentFrame`|`CFrameWnd*`|框架窗口的其他框架窗口进行建模，如下所示的第二个文档框架窗口创建。|

当文档模板创建一个文档和其关联的组件时，将验证中存储的信息`CCreateContext`结构。 例如，不应为不存在的文档创建一个视图。

> [!NOTE]
>  中的指针的所有`CCreateContext`是可选的可以是`NULL`如果未指定或未知。

`CCreateContext` 下列出的成员函数使用"另请参阅。" 如果你打算重写它们的特定信息，参阅这些函数的说明。

以下是一些通用准则：

- 为窗口创建的参数中传递时`CWnd::Create`， `CFrameWnd::Create`，和`CFrameWnd::LoadFrame`，创建上下文指定应连接的新窗口。 对于大多数 windows，整个结构是可选和`NULL`可以将指针传递。

- 对于可重写成员函数，如`CFrameWnd::OnCreateClient`，则`CCreateContext`参数是可选的。

- 所涉及的成员函数的视图中创建过程中，您必须提供足够的信息来创建视图。 例如，对于拆分器窗口中的第一个视图，必须提供视图类信息和当前文档。

一般情况下，如果您使用 framework 默认值，则可以忽略`CCreateContext`。 如果你尝试更高级的修改、 Microsoft 基础类库的源代码或示例程序，如 VIEWEX，将指导你。 如果忘记执行操作所需的参数，framework 断言将告诉您忘记了。

有关详细信息`CCreateContext`，请参阅 MFC 示例[VIEWEX](../../visual-cpp-samples.md)。

## <a name="requirements"></a>要求

**标头：** afxext.h

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterWnd::Create](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[Cwnd:: Create](../../mfc/reference/cwnd-class.md#create)

