---
title: /DYNAMICBASE
ms.date: 06/12/2018
f1_keywords:
- /dynamicbase
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
ms.openlocfilehash: 54644d9df546299be3b688f9745a121592938df6
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373614"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

指定是否生成可在加载时随机变基的可执行映像，该映像使用 windows Vista 中首次提供的 Windows 的地址空间布局随机化（ASLR）功能。

## <a name="syntax"></a>语法

> **/DYNAMICBASE**[**： NO**]

## <a name="remarks"></a>备注

**/DYNAMICBASE**选项修改*可执行映像*（.dll 或 .exe 文件）的标头，以指示应用程序是否应在加载时随机变基，并启用虚拟地址分配随机化，这会影响堆、堆栈和其他操作系统分配的虚拟内存位置。 **/DYNAMICBASE**选项适用于32位和64位映像。 Windows Vista 和更高版本的操作系统支持 ASLR。 早期的操作系统将忽略此选项。

默认情况下， **/DYNAMICBASE**处于启用状态。 若要禁用此选项，请使用 **/DYNAMICBASE： NO**。 若要使[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)选项生效， **/DYNAMICBASE**选项是必需的。

## <a name="see-also"></a>另请参阅

- [EDITBIN 选项](editbin-options.md)
- [Windows ISV 软件安全防御](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
