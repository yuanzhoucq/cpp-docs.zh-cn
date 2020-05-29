---
title: 动态对象创建
ms.date: 03/27/2020
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 40a17d3ed458d0634fd5bf27b54d0a36a65e35b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364806"
---
# <a name="dynamic-object-creation"></a>动态对象创建

本文说明了如何在运行时动态地创建对象。 该过程使用运行时类信息，如[访问运行时类信息](../mfc/accessing-run-time-class-information.md)一文中所述。

#### <a name="dynamically-create-an-object-given-its-run-time-class"></a>在其运行时类中动态创建对象

1. 使用以下代码使用 的`CreateObject`函数动态创建对象。 `CRuntimeClass` 发生故障时，`CreateObject`返回**NULL**而不是引发异常：

   [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>另请参阅

[Destroying Window Objects](tn017-destroying-window-objects.md)
[使用 CObject](using-cobject.md)销毁窗口对象
