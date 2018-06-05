---
title: 提取函数 | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: e31d1249-9705-4511-acbd-9f6fe73bdf2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fc4d48c972bca9352f326085574e4cf4df83aea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333152"
---
# <a name="extract-function"></a>提取函数
功能：将代码片段转换为独立的函数。

时间：需要从其他函数调用某些函数中现有的代码片段时。  

原因：可以复制/粘贴该代码，但这样会导致重复。  更好的解决方案是将此片段重构为独立的且可供任何其他函数自行调用的函数。

方法：

1. 突出显示要提取的代码：

   ![突出显示的代码](images/extractfunction_highlight.png)

1. 接下来，执行以下操作之一：
   * **键盘**
     * 按“Ctrl+R”，然后按“Ctrl+M”。  （请注意，键盘快捷方式可能因所选的配置文件而有所不同。）
     * 按“Ctrl+.” 触发“快速操作和重构”菜单，然后从快捷菜单选择“提取函数(实验)”。
   * **鼠标**
     * 选择“编辑”>“重构”>“提取函数(实验)”。
     * 右键单击该代码，并选择“快速操作和重构”菜单，然后从快捷菜单选择“提取函数(实验)”。
     * 单击左侧空白处显示的![灯泡](images/bulb.png)图标，然后从快捷菜单中选择“提取函数(实验)”。

1. 在“提取函数/方法(实验)”窗口中，输入新函数名称，选择要放置代码的位置，然后单击“确定”按钮。  

   ![提取函数函数](images/extractfunction_dialog.png)

1. 将在指定的位置创建新函数，在相应的头文件中创建函数原型，并更改原始代码以调用该函数。

   ![提取函数结果](images/extractfunction_result.png)