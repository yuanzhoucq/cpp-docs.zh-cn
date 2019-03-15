---
title: 项目生成错误 PRJ0025
ms.date: 08/27/2018
f1_keywords:
- PRJ0025
helpviewer_keywords:
- PRJ0025
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
ms.openlocfilehash: 5f3699dce75a20b9cc6e1d712bc5702543ab7b6c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814561"
---
# <a name="project-build-error-prj0025"></a>项目生成错误 PRJ0025

> 批处理文件*文件*包含未能翻译成用户的 ANSI 代码页的 Unicode 内容。
>
> *UNICODE 文件的内容*

项目系统找到在自定义的 Unicode 内容生成规则或生成事件不能正确翻译成用户的当前 ANSI 代码页。

此错误的解决方法是更新生成规则的内容或生成事件以使用 ANSI 或在计算机上安装的代码页，并将其设置为系统默认值。

有关详细信息自定义生成步骤和生成事件，请参阅[了解自定义生成步骤和生成事件](../../build/understanding-custom-build-steps-and-build-events.md)。