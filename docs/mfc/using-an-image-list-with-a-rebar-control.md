---
title: 对 Rebar 控件使用图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
ms.openlocfilehash: 3cf359a5d06396f9c2c31cbec511c04784053e53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641428"
---
# <a name="using-an-image-list-with-a-rebar-control"></a>对 Rebar 控件使用图像列表

每个 rebar 带区除了别的之外还可以包含关联图像列表的图像。 以下过程详述了在 rebar 带区显示图像的必需步骤。

### <a name="to-display-images-in-a-rebar-band"></a>在 rebar 带区显示图像

1. 通过调用将图像列表附加到 rebar 控件对象[SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist)，指针传递给现有图像列表。

1. 修改**REBARBANDINFO**结构，以向 rebar 带区分配图像：

   - 设置*fMask*成员添加到`RBBIM_IMAGE`，使用按位 OR 运算符根据需要包含其他标志。

   - 设置*iImage*要显示的图像的图像列表索引成员。

1. 使用必需信息初始化任何其余的数据成员，如包含子窗口的大小、文本和句柄。

1. 插入新的带区 （带图像），号召[crebarctrl:: Insertband](../mfc/reference/crebarctrl-class.md#insertband)，并传入**REBARBANDINFO**结构。

以下示例假定已将带两个图像的现有图像列表对象附加到 rebar 控件对象 (`m_wndReBar`)。 包含第一个图像的新的 rebar 带区（由 `rbi` 定义）是通过调用 `InsertBand` 添加的：

[!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]

## <a name="see-also"></a>请参阅

[使用 CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

