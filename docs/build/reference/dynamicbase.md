---
title: -DYNAMICBASE |Microsoft Docs
ms.custom: ''
ms.date: 06/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /dynamicbase
dev_langs:
- C++
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 255123157da3f802eafaf26206598d54fea02335
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223450"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

指定是否生成可执行映像可以是随机重新设定基址在加载时使用了第一次 Windows Vista 中提供的 Windows 的地址空间布局随机化 (ASLR) 功能。

## <a name="syntax"></a>语法

> **/DYNAMICBASE**[**： 否**]

## <a name="remarks"></a>备注

**/DYNAMICBASE**选项修改的标头*可执行映像*，.dll 或.exe 文件，以指示是否应为随机重新设定基址在加载时，应用程序，并启用虚拟地址分配随机化，这会影响的虚拟内存位置的堆，堆栈和其他操作系统分配。 **/DYNAMICBASE**选项适用于 32 位和 64 位映像。 在 Windows Vista 和更高版本操作系统上支持 ASLR。 早期版本的操作系统忽略该选项。

默认情况下 **/DYNAMICBASE**已启用。 若要禁用此选项，请使用 **/dynamicbase: no**。 **/DYNAMICBASE**是所必需的选项[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)选项产生任何影响。

## <a name="see-also"></a>请参阅

- [EDITBIN 选项](../../build/reference/editbin-options.md)
- [Windows ISV 软件安全防御措施](https://msdn.microsoft.com/library/bb430720.aspx)