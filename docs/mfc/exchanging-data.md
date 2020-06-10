---
title: 交换数据
ms.date: 11/04/2016
helpviewer_keywords:
- property sheets [MFC], data exchange
- exchanging data with property sheets [MFC]
- DDX (dialog data exchange) [MFC], property sheets
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
ms.openlocfilehash: 5be82567e02fd5e935d42f9eff5bdee20fa0d5a8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622708"
---
# <a name="exchanging-data"></a>交换数据

与大多数对话框一样，属性表和应用程序之间的数据的交换是属性表的最重要的函数之一。 本主题介绍如何完成此任务。

与属性表交换数据实际上是与属性表的各个属性页交换数据。 与属性页交换数据的过程与使用对话框交换数据相同，因为[CPropertyPage](reference/cpropertypage-class.md)对象只是一个专用的[CDialog](reference/cdialog-class.md)对象。 该过程利用了框架的对话框数据交换 (DDX) 工具，它在对话框中的控件和对话框对象的成员变量之间交换数据。

与属性表交换数据以及与常见对话框交换数据的重要区别在于属性表有多个页，因此您必须与属性表中的所有页交换数据。 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](dialog-data-exchange-and-validation.md)。

以下示例演示在一个视图和属性表的两个页之间交换数据：

[!code-cpp[NVC_MFCDocView#4](codesnippet/cpp/exchanging-data_1.cpp)]

## <a name="see-also"></a>另请参阅

[属性表](property-sheets-mfc.md)
