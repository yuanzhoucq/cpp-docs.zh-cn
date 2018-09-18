---
title: 字符串，ATL 属性页向导 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.ppg.strings
dev_langs:
- C++
helpviewer_keywords:
- ATL Property Page Wizard, strings
ms.assetid: 00547db6-911f-49eb-92e1-2ba67079d4df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e63745a75b5aec644ae49931015e27b74eba91b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033532"
---
# <a name="strings-atl-property-page-wizard"></a>字符串，ATL 属性页向导

提供与属性页关联的文本。

- **标题**

   在属性页的选项卡上设置显示的文本。

- **文档字符串**

   设置描述页的文本字符串。 此字符串可以显示在属性表对话框。 属性框架可以使用在状态行或工具提示中的说明。 标准属性框架当前不使用此字符串。

- **帮助文件**

   设置描述如何使用属性页的帮助文件的名称。 此名称不应包含路径。 当用户按**帮助**，框架将在 HelpDir 密钥 CLSID 下的属性页注册表项中的值中指定的目录中打开帮助文件。

## <a name="see-also"></a>请参阅

[ATL 属性页向导](../../atl/reference/atl-property-page-wizard.md)<br/>
[选项，ATL 属性页向导](../../atl/reference/options-atl-property-page-wizard.md)

