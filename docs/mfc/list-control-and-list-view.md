---
title: 列表控件和列表视图
ms.date: 11/04/2016
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
ms.openlocfilehash: d308cfe83f02dcfe3687790c6638d268cc69fc24
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621431"
---
# <a name="list-control-and-list-view"></a>列表控件和列表视图

为方便起见，MFC 将通过两种方式封装列表控件。 您可使用列表控件：

- 直接通过将[CListCtrl](reference/clistctrl-class.md)对象嵌入对话框类中。

- 使用类[CListView](reference/clistview-class.md)进行间接。

`CListView`使用 MFC 文档/视图体系结构，可以轻松地将列表控件与 MFC 文档/视图体系结构相集成，并将控件封装为[CEditView](reference/ceditview-class.md)封装编辑控件：控件填充 MFC 视图的整个表面区域。 （视图*是*控件，转换为 `CListView` 。）

`CListView`对象从[CCtrlView](reference/cctrlview-class.md)及其基类继承，并添加成员函数以检索基础列表控件。 使用视图成员以将此视图作为视图使用。 使用[GetListCtrl](reference/clistview-class.md#getlistctrl)成员函数获取对列表控件的成员函数的访问权限。 使用这些成员

- 添加、删除或操作列表中的“项”。

- 设置或获取列表控件特性。

若要获取对作为 `CListCtrl` 的基础的 `CListView` 的引用，请通过列表视图类调用 `GetListCtrl`：

[!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]

本主题介绍了使用列表控件的两种方式。

## <a name="see-also"></a>另请参阅

[使用 CListCtrl](using-clistctrl.md)<br/>
[控件](controls-mfc.md)
