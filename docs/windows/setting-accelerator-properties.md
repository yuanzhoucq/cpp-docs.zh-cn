---
title: 设置快捷键属性 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
ms.openlocfilehash: 47ebd54fdaff099e3a8ce828581a66b0ec871915
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647013"
---
# <a name="setting-accelerator-properties"></a>设置快捷键属性

可以设置快捷键属性[属性窗口](/visualstudio/ide/reference/properties-window)在任何时间。 此外可以使用**Accelerator**编辑器修改快捷键对应表中的快捷键属性。 使用所做更改**属性**窗口或**Accelerator**编辑器具有相同的结果： 在快捷键对应表中都即时反映编辑。

有三个属性的每个快捷键 ID:

- [Modifier 属性](../windows/accelerator-modifier-property.md)设置快捷键的组合键的控件。

   > [!NOTE]
   > 在中**属性**窗口中，此属性显示为三个单独的布尔属性，所有这些可独立控制： **Alt**， **Ctrl**，以及**Shift**。

- [键属性](../windows/accelerator-key-property.md)设置实际用作快捷键的键。

- [类型属性](../windows/accelerator-type-property.md)确定键被解释为虚拟 (VIRTKEY) 或 ASCII/ANSI。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[预定义快捷键](../windows/predefined-accelerator-keys.md)<br/>
[资源编辑器](../windows/resource-editors.md)<br/>
[快捷键编辑器](../windows/accelerator-editor.md)