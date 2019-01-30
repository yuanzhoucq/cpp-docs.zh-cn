---
title: 设置快捷键属性 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
- VIRTKEY
- Key property
- ID property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
ms.openlocfilehash: e1fac31635b7ccc09f9c184cf734fa4f7717cb97
ms.sourcegitcommit: 5beace7dcc6bf0e8b8cc96a930e7424f9daa05cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232131"
---
# <a name="setting-accelerator-properties"></a>设置快捷键属性

可以设置快捷键属性[属性窗口](/visualstudio/ide/reference/properties-window)在任何时间。 此外可以使用[快捷键编辑器](../windows/accelerator-editor.md)修改快捷键对应表中的快捷键属性。 使用所做更改**属性**窗口或**Accelerator**编辑器具有相同的结果： 在快捷键对应表中都即时反映编辑。

## <a name="id-property"></a>ID 属性

**ID**属性引用在程序代码中的每个快捷键对应表项。 此条目是当用户按下的加速键或键组合，程序将接收的命令值。 若要使快捷键与菜单项相同，使其 Id 相同 （只要快捷键对应表的 ID 是菜单资源的 ID 相同）。

有三个属性的每个快捷键 ID:**修饰符**属性，**密钥**属性，并且**类型**属性。

## <a name="modifier-property"></a>Modifier 属性

**修饰符**属性设置控件的快捷键的组合键。

> [!NOTE]
> 在中**属性**窗口中，此属性显示为三个单独**布尔**属性，所有这些可独立控制：**Alt**， **Ctrl**，和**Shift**。

以下是合法的条目**修饰符**快捷键对应表中的属性：

   |值|描述|
   |-----------|-----------------|
   |**无**|用户仅按**密钥**值。 使用此值是最有效地使用 ASCII/ANSI 值 001 026，通过它解释为 ^ A 到 ^ Z (**Ctrl + A**通过**Ctrl + Z**)。|
   |**Alt**|用户必须按**Alt**密钥之前**密钥**值。|
   |**Ctrl**|用户必须按**Ctrl**密钥之前**密钥**值。 与 ASCII 类型无效。|
   |**Shift**|用户必须按**Shift**密钥之前**密钥**值。|
   |**Ctrl+Alt**|用户必须按**Ctrl**密钥和**Alt**密钥之前**密钥**值。 与 ASCII 类型无效。|
   |**Ctrl+Shift**|用户必须按**Ctrl**密钥和**Shift**密钥之前**密钥**值。 与 ASCII 类型无效。|
   |**Alt+Shift**|用户必须按**Alt**密钥和**Shift**密钥之前**密钥**值。 与 ASCII 类型无效。|
   |**Ctrl+Alt+Shift**|用户必须按**Ctrl**， **Alt**，并**Shift**之前**密钥**值。 与 ASCII 类型无效。|

## <a name="key-property"></a>Key 属性

**密钥**属性设置实际用作快捷键的键。

以下是合法的条目**密钥**快捷键对应表中的属性：

   |“值”|描述|
   |-----------|-----------------|
   |0 到 255 以十进制格式之间的整数。|值确定是否值视为 ASCII 或 ANSI，如下所示：<br/><br/>-一位数字始终解释为相应的项，而不是作为 ASCII 或 ANSI 值。<br/>值从 1 到 26 的前面加零上, 时被解释为 ^ A 到 ^ Z，表示与按下时的字母表的字母的 ASCII 值**Ctrl**按下键。<br/>-27-32 中的值始终被解释为三位十进制值 027 到 032。<br/>-值从 033 到 255，0 的前面还是不被解释为 ANSI 值。|
   |单个键盘字符。|大写字母 A-Z 或数字 0-9 可以是 ASCII 或虚拟键值;任何其他字符仅为 ASCII。|
   |A-Z 范围内的单个键盘字符 （仅大写的）、 前面插入符号 (^) (例如，^ C)。|与按下时，此选项将进入键的 ASCII 值**Ctrl**按下键。|
   |任何有效的虚拟键标识符。|快捷键对应表中的下拉列表密钥框包含一组标准的虚拟键标识符。|

> [!NOTE]
> 当输入 ASCII 值，被限制修饰符属性选项。 唯一控件可用的密钥使用的是**Alt**密钥。

> [!TIP]
> 定义快捷键另一种方法是右键单击一项或多个快捷键对应表中的项，请选择**键入的下一个密钥**从快捷菜单，然后在键盘上按任何键或组合键。 **键入的下一步键**命令也会提供**编辑**菜单。

## <a name="type-property"></a>Type 属性

**类型**属性确定与快捷键 ID 相关联的快捷键组合被解释为 ASCII/ANSI 密钥值或虚拟键 (VIRTKEY) 组合。

- 如果**类型**属性是 ASCII**修饰符**属性只能`None`或`Alt`，也可以使用快捷键**Ctrl**密钥 （指定的前面使用的密钥`^`)。

- 如果**类型**属性是 VIRTKEY 的任意组合`Modifier`和`Key`值是否有效。

> [!NOTE]
> 如果希望快捷键对应表中输入一个值，并将值作为 ASCII/ANSI，只需单击处理**类型**表并从下拉列表中选择 ASCII 中的条目。 但是，如果您使用**键入的下一步键**命令 (**编辑**菜单) 来指定`Key`，则必须更改**类型**属性从 VIRTKEY 为 ASCII *之前*输入`Key`代码。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[在快捷键对应表中编辑](../windows/editing-in-an-accelerator-table.md)<br/>
[预定义快捷键](../windows/predefined-accelerator-keys.md)<br/>
[资源编辑器](../windows/resource-editors.md)<br/>
