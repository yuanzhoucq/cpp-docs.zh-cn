---
title: 将公共控件用作子窗口 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], using as child windows
- windows [MFC], common controls as
- child windows [MFC], common controls as
- common controls [MFC], child windows
- Windows common controls [MFC], child windows
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73ddb010aeb8190c063d2691806e3ebd89d0f744
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417964"
---
# <a name="using-a-common-control-as-a-child-window"></a>将公共控件用作子窗口

任何一个 Windows 公共控件均可用作任何其他窗口的子窗口。 以下过程介绍如何以动态方式创建公共控件然后使用它。

### <a name="to-use-a-common-control-as-a-child-window"></a>将公共控件用作子窗口

1. 在相关类或处理程序中定义控件。

1. 使用的控件的重写[cwnd:: Create](../mfc/reference/cwnd-class.md#create)方法来创建 Windows 控件。

1. 创建控件后（如果创建控件的子类，则是在执行 `OnCreate` 处理程序的时候），可使用其成员函数操作控件。 请参阅在各个控件的说明[控件](../mfc/controls-mfc.md)有关方法的详细信息。

1. 当完成与该控件，请使用[cwnd:: Destroywindow](../mfc/reference/cwnd-class.md#destroywindow)销毁控件。

## <a name="see-also"></a>请参阅

[创建和使用控件](../mfc/making-and-using-controls.md)<br/>
[控件](../mfc/controls-mfc.md)

