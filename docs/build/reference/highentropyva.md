---
title: /HIGHENTROPYVA
ms.date: 06/12/2018
f1_keywords:
- /HIGHENTROPYVA
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
ms.openlocfilehash: b2ff9929de74d99fbc45e4f4ff38fd6b939697bc
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373822"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

指定可执行映像是否支持高熵 64 位地址空间布局随机化 (ASLR)。

## <a name="syntax"></a>语法

> **/HIGHENTROPYVA**[**： NO**]

## <a name="remarks"></a>备注

此选项修改*可执行映像*（.dll 文件或 .exe 文件）的标头，以指示是否支持与64位地址的 ASLR。 当在可执行文件和所有依赖的模块上执行此选项时，支持 64 位 ASLR 的操作系统可在加载时通过使用 64 位虚拟地址空间来重新设定可执行映像段。 更大的地址空间使攻击者更难猜到特定内存区域的位置。

默认情况下，链接器将为64位可执行文件映像启用 **/HIGHENTROPYVA** 。 此选项需要[/LARGEADDRESSAWARE](largeaddressaware.md)，此功能在默认情况下也可用于64位映像。 **/HIGHENTROPYVA**不适用于32位可执行文件映像，其中的选项会被忽略。 若要显式禁用此选项，请使用 **/HIGHENTROPYVA： NO**。 若要使此选项生效，还必须设置[/DYNAMICBASE](dynamicbase.md)选项。

## <a name="see-also"></a>请参阅

- [EDITBIN 选项](editbin-options.md)
- [/DYNAMICBASE](dynamicbase.md)
- [Windows ISV 软件安全防御](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
