---
title: CCreateContext 结构
ms.date: 11/04/2016
f1_keywords:
- CCreateContext
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
ms.openlocfilehash: 29fc6210b9888b6a5ba5aaf15b66242c29c15dc8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369379"
---
# <a name="ccreatecontext-structure"></a>CCreateContext 结构

框架在`CCreateContext`创建与文档关联的框架窗口和视图时使用结构。

## <a name="syntax"></a>语法

```
struct CCreateContext
```

## <a name="remarks"></a>备注

`CCreateContext`是一个结构，没有基类。

创建窗口时，此结构中的值提供用于将文档组件连接到其数据视图的信息。 仅当重写创建过程的某些部分`CCreateContext`时，才需要使用。

结构`CCreateContext`包含指向文档、框架窗口、视图和文档模板的指针。 它还包含指向`CRuntimeClass`标识要创建的视图类型的 指针。 运行时类信息和当前文档指针用于动态创建新视图。 下表说明了如何使用以及何时使用每个`CCreateContext`成员：

|成员|类型|它的目的是什么|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass`要创建的新视图。|
|`m_pCurrentDoc`|`CDocument*`|要与新视图关联的现有文档。|
|`m_pNewDocTemplate`|`CDocTemplate*`|与创建新 MDI 框架窗口关联的文档模板。|
|`m_pLastView`|`CView*`|对其他视图建模的原始视图，如创建拆分窗口视图或创建文档上的第二个视图。|
|`m_pCurrentFrame`|`CFrameWnd*`|对附加框架窗口建模的帧窗口，如在文档上创建第二个框架窗口。|

当文档模板创建文档及其关联的组件时，它会验证存储在结构中`CCreateContext`的信息。 例如，不应为不存在的文档创建视图。

> [!NOTE]
> 中的所有`CCreateContext`指针都是可选的，如果未指定或`NULL`未知，则可以。

`CCreateContext`由"另请参阅"下列出的成员函数使用。 如果您计划重写这些函数，请参阅这些函数的说明，了解它们的特定信息。

以下是一些一般准则：

- 当作为窗口创建参数传递时，如 在`CWnd::Create``CFrameWnd::Create`和`CFrameWnd::LoadFrame`中，创建上下文指定新窗口应连接到的内容。 对于大多数窗口，整个结构是可选的，可以传递`NULL`指针。

- 对于可重写的成员函数（如`CFrameWnd::OnCreateClient`，`CCreateContext`参数是可选的）。

- 对于视图创建中涉及的成员函数，必须提供足够的信息来创建视图。 例如，对于拆分器窗口中的第一个视图，必须提供视图类信息和当前文档。

通常，如果使用框架默认值，则可以忽略`CCreateContext`。 如果您尝试更高级的修改，Microsoft 基础类库源代码或示例程序（如 VIEWEX）将指导您。 如果您忘记了所需的参数，框架断言将告诉您忘记了什么。

有关 的详细信息`CCreateContext`，请参阅 MFC 示例[VIEWEX](../../overview/visual-cpp-samples.md)。

## <a name="requirements"></a>要求

**标题：** afxext.h

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CFramewnd：：创建](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFramewnd：：加载帧](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFramewnd：：打开创建客户端](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterwnd：：创建](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterwnd：：创建视图](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[CWnd::Create](../../mfc/reference/cwnd-class.md#create)
