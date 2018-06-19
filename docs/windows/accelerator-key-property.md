---
title: 快捷键的 Key 属性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Key property
ms.assetid: d1570cd9-b414-4cd6-96bd-47c38281eaca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e4fc56384d666026f4cc7e21f9d8af9347046fd1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857202"
---
# <a name="accelerator-key-property"></a>快捷键的 Key 属性
以下是用于快捷键对应表中的键属性的合法条目：  
  
-   介于 0 和 255 以十进制格式之间的整数。 值确定是否值被视为 ASCII 或 ANSI，如下所示：  
  
    -   一位数字始终解释为对应的键，而不是 ASCII 或 ANSI 值。  
  
    -   从 1 到 26 时前面带有零，, 值都会被解释为 ^ A 到 ^ Z，它表示与按住 CTRL 键一起按下时字母表的字母的 ASCII 值。  
  
    -   从 27-32 的值始终解释为三个数字的十进制值 027 到 032。  
  
    -   跟在 0 的还是未解释为 ANSI 值 033 到 255 中的值。  
  
-   单个键盘字符。 大写字母 A-Z 或数字 0-9 可以是 ASCII 或虚拟键值;任何其他字符仅 ASCII。  
  
-   A-Z 范围中的单个键盘字符 （仅为大写），前面的脱字号 (^) (例如，^ C)。 它与按住 CTRL 键一起按下时，这将会进入键的 ASCII 值。  
  
    > [!NOTE]
    >  当输入 ASCII 值，则修饰符属性选项被限制。 可供使用的是使用 ALT 键唯一的控制密钥。  
  
-   任何有效的虚拟键标识符。 快捷键对应表中的下拉列表密钥框包含标准虚拟键标识符列表。  
  
    > [!TIP]
    >  定义快捷键另一种方法是右键单击一项或多个项的快捷键对应表中，选择**键入的下一个密钥**从快捷菜单，然后在键盘上按任何键或键组合。 **键入的下一个密钥**命令也是可从**编辑**菜单。  
  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [设置快捷键属性](../windows/setting-accelerator-properties.md)   
 [编辑快捷键对应表中](../windows/editing-in-an-accelerator-table.md)   
 [快捷键编辑器](../windows/accelerator-editor.md)