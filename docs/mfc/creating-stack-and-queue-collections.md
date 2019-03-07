---
title: 创建堆栈和队列集合
ms.date: 11/04/2016
helpviewer_keywords:
- MFC collection classes [MFC], stack collections
- collections, stack
- stack
- collection classes [MFC], creating
- queue collections
- MFC collection classes [MFC], queue collections
- stack collections
- collections, queue
ms.assetid: 3c7bc198-35f0-4fc3-aaed-6005a0f22638
ms.openlocfilehash: ed0ad9b98a69e56df4e66b25bc6ca08cdaaad413
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301462"
---
# <a name="creating-stack-and-queue-collections"></a>创建堆栈和队列集合

此文章介绍了如何创建其他数据结构，如[堆栈](#_core_stacks)并[队列](#_core_queues)，MFC 类列表中。 示例使用从 `CList` 派生的类，但可以直接使用 `CList`，除非您需要添加功能。

##  <a name="_core_stacks"></a> Stacks

由于标准列表集合具有头和尾，因此很容易创建一个模仿后进先出堆栈的行为的派生列表集合。 堆栈就像自助餐厅中的一堆盘子。 新添的盘子将会放在现有的盘子的上面。 最后添加的盘子将会首先被取用。 列表集合成员函数 `AddHead` 和 `RemoveHead` 可用于专门从列表头中添加和移除元素；因此，最新添加的元素将是第一个被移除的。

#### <a name="to-create-a-stack-collection"></a>创建堆栈集合

1. 从现有的一个 MFC 列表类派生一个新的列表类，然后添加更多成员函数来支持堆栈操作的功能。

   以下示例显示如何添加成员函数以将元素推送到堆栈，查看堆栈的顶部元素并弹出堆栈中的顶部元素：

   [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_1.h)]

请注意，此方法将公开基础的 `CObList` 类。 用户可以调用任何 `CObList` 成员函数，无论它对堆栈是否有意义。

##  <a name="_core_queues"></a> 队列

由于标准列表集合具有头和尾，因此很容易创建一个模仿先进先出队列的行为的派生列表集合。 队列就像是自助餐厅中的一队排列等候的人。 队伍中的第一个人是最先得到服务的。 随着更多人的来到，他们会排在队伍的末尾等待轮到他们。 列表集合成员函数 `AddTail` 和 `RemoveHead` 可用于专门从列表的头或尾中添加和移除元素；因此，最新添加的元素始终是最后一个被移除的。

#### <a name="to-create-a-queue-collection"></a>创建队列集合

1. 从 Microsoft 基础类库提供的一个预定义列表类派生一个新的列表类，并添加更多成员函数来支持队列操作的语义。

   以下示例显示可如何追加成员函数以将元素添加到队列的结尾以及从队列的前面获取元素。

   [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_2.h)]

## <a name="see-also"></a>请参阅

[集合](../mfc/collections.md)
