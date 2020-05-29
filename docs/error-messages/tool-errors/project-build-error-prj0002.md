---
title: 项目生成错误 PRJ0002
ms.date: 08/27/2018
f1_keywords:
- PRJ0002
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
ms.openlocfilehash: 30680f5b26f3be5e7f9b48d18e82fca42ed65493
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192934"
---
# <a name="project-build-error-prj0002"></a>项目生成错误 PRJ0002

> 从 "*命令行*" 返回的错误结果。

"**属性页**" 对话框中的 "用户输入" 生成的命令*行*返回了错误代码，但 "**输出**" 窗口中不会显示任何信息。

此错误的解决方法取决于生成错误的工具。 对于 MIDL，如果定义了/o （重定向输出），就会了解发生了什么错误。

诸如自定义生成步骤或生成事件这样的批处理文件并不是有关失败情况的信息，也可能是导致此错误的原因。
