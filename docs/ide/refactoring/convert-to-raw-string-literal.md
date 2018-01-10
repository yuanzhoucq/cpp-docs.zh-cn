---
title: "将转换为原始字符串文本 |Microsoft 文档"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 12aa512270ecce4564561634f99be9cbf155448a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="convert-to-raw-string-literal"></a>转换为原始字符串文本
**新增功能：**可以将任何字符串转换为 c + + 的原始字符串文本。

**何时：**必须转义的字符不应处理为转义字符的字符串。

**原因：**无法双转义字符，但这往往会导致令人迷惑且不可读的字符串。  使用原始字符串文本使得更易于读取字符串。

**如何：**

1. 将文本或鼠标光标悬停要转换的转义字符串。

   ![突出显示的代码](images/stringliteral_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**将转换为原始字符串文本**从上下文菜单。
   * **鼠标**
     * 右键单击代码中，选择**快速操作和重构**菜单，然后选择**将转换为原始字符串文本**从上下文菜单。
     * 单击![Lightbulb](images/bulb.png)图标显示在左边的距和选择**将转换为原始字符串文本**从上下文菜单。

1. 该字符串将立即转换为原始字符串文本。  

   ![原始字符串文本的结果](images/stringliteral_result.png)