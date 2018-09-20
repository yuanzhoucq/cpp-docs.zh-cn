---
title: 快捷键的 Key 属性 （c + +） |Microsoft Docs
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
ms.openlocfilehash: e0594e5b9e2d092330664546cbd05ccfb0060c42
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428962"
---
# <a name="accelerator-key-property-c"></a>快捷键的 Key 属性 （c + +）

快捷键对应表中的键属性的合法项如下：

- 0 到 255 以十进制格式之间的整数。 值确定是否值视为 ASCII 或 ANSI，如下所示：

   - 一位数字始终解释为相应的项，而不是作为 ASCII 或 ANSI 值。

   - 从 1 到 26 的前面加零上, 时的值被解释为 ^ A 到 ^ Z，表示与按下时的字母表的字母的 ASCII 值**Ctrl**按下键。

   - 27-32 中的值始终被解释为三位十进制值 027 到 032。

   - 0 的前面还是不被解释为 ANSI 值从 033 到 255 的值。

- 单个键盘字符。 大写字母 A-Z 或数字 0-9 可以是 ASCII 或虚拟键值;任何其他字符仅为 ASCII。

- A-Z 范围内的单个键盘字符 （仅大写的）、 前面插入符号 (^) (例如，^ C)。 这与按下时输入的键的 ASCII 值**Ctrl**按下键。

   > [!NOTE]
   > 当输入 ASCII 值，被限制修饰符属性选项。 唯一控件可用的密钥使用的是**Alt**密钥。

- 任何有效的虚拟键标识符。 快捷键对应表中的下拉列表密钥框包含一组标准的虚拟键标识符。

   > [!TIP]
   > 定义快捷键另一种方法是右键单击一项或多个快捷键对应表中的项，请选择**键入的下一个密钥**从快捷菜单，然后在键盘上按任何键或组合键。 **键入的下一步键**命令也会提供**编辑**菜单。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[设置快捷键属性](../windows/setting-accelerator-properties.md)<br/>
[在快捷键对应表中编辑](../windows/editing-in-an-accelerator-table.md)<br/>
[快捷键编辑器](../windows/accelerator-editor.md)