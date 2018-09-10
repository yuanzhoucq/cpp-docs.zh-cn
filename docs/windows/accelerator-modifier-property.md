---
title: 快捷键 Modifier 属性 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 793e02b4ac083d6fe84ba2cc76ee340bcf2484e9
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316050"
---
# <a name="accelerator-modifier-property-c"></a>快捷键 Modifier 属性 （c + +）

以下是合法的快捷键对应表中的修饰符属性条目。

|“值”|描述|
|-----------|-----------------|
|**无**|用户仅按**密钥**值。 这最有效地与使用 ASCII/ANSI 值 001 到 026，它解释为 ^ A 到 ^ Z (CTRL-A 到 Z CTRL)。|
|**Alt**|用户必须按**Alt**密钥之前**密钥**值。|
|**Ctrl**|用户必须按**Ctrl**密钥之前**密钥**值。 与 ASCII 类型无效。|
|**Shift**|用户必须按**Shift**密钥之前**密钥**值。|
|**Ctrl + Alt**|用户必须按**Ctrl**密钥和**Alt**密钥之前**密钥**值。 与 ASCII 类型无效。|
|**Ctrl + Shift**|用户必须按**Ctrl**密钥和**Shift**密钥之前**密钥**值。 与 ASCII 类型无效。|
|**Alt + Shift**|用户必须按**Alt**密钥和**Shift**密钥之前**密钥**值。 与 ASCII 类型无效。|
|**Ctrl + Alt + Shift**|用户必须按**Ctrl**， **Alt**，并**Shift**之前**密钥**值。 与 ASCII 类型无效。|

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[设置快捷键属性](../windows/setting-accelerator-properties.md)  
[快捷键编辑器](../windows/accelerator-editor.md)