---
title: -HIGHENTROPYVA |Microsoft Docs
ms.custom: ''
ms.date: 06/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /HIGHENTROPYVA
dev_langs:
- C++
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fec9314be9d69e2cb0af2a98884bd78de1ff679
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202073"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

指定可执行映像是否支持高熵 64 位地址空间布局随机化 (ASLR)。

## <a name="syntax"></a>语法

> **/HIGHENTROPYVA**[**： 否**]

## <a name="remarks"></a>备注

此选项修改的标头*可执行映像*，.dll 文件或.exe 文件，以指示是否支持 64 位地址的 ASLR。 当在可执行文件和所有依赖的模块上执行此选项时，支持 64 位 ASLR 的操作系统可在加载时通过使用 64 位虚拟地址空间来变基可执行映像。 更大的地址空间使攻击者更难猜到特定内存区域的位置。

默认情况下，链接器启用 **/HIGHENTROPYVA**为 64 位可执行映像。 此选项需要[/LARGEADDRESSAWARE](largeaddressaware.md)，其中还启用了默认情况下为 64 位映像。 **/HIGHENTROPYVA**不是适用于 32 位可执行映像，将忽略此选项。 若要显式禁用此选项，请使用 **/highentropyva: no**。 有关此选项将使某个效果，请[/DYNAMICBASE](dynamicbase.md)还必须设置选项。

## <a name="see-also"></a>请参阅

- [EDITBIN 选项](editbin-options.md)
- [/DYNAMICBASE](dynamicbase.md)
- [Windows ISV 软件安全防御措施](https://msdn.microsoft.com/library/bb430720.aspx)
