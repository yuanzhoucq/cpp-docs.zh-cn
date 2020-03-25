---
title: 转换为原始字符串文本
ms.date: 11/16/2016
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
ms.openlocfilehash: 5636e00bfe8655d84fb2e4b64e0391324ab35d7d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171809"
---
# <a name="convert-to-raw-string-literal"></a>转换为原始字符串文本

功能：可以将任何字符串转换为 C++ 原始字符串文本。

时间：具有的某个字符串带有转义字符，但其不应处理为转义字符时使用该功能。

原因：可对字符进行双转义，这通常会导致混淆和不可读的字符串。  使用原始字符串文本会使字符串更易读取。

**方式：**

1. 将文本或鼠标光标置于要转移的转义字符串上。

   ![突出显示的代码](images/stringliteral_highlight.png)

1. 接下来，执行以下操作之一：
   * **键盘**
     * 按“Ctrl+.” 触发“快速操作和重构”菜单，然后从上下文菜单选择“转换为原始字符串文本”。
   * **鼠标**
     * 右键单击代码，选择“快速操作和重构”菜单，然后从上下文菜单选择“转换为原始字符串文本”。
     * 单击左侧空白处显示的![灯泡](images/bulb.png)图标，然后从上下文菜单选择“转换为原始字符串文本”。

1. 该字符串将立即转换为原始字符串文本。

   ![原始字符串文本结果](images/stringliteral_result.png)
