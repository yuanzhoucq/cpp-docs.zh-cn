---
title: 项目生成错误 PRJ0002
ms.date: 08/27/2018
f1_keywords:
- PRJ0002
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
ms.openlocfilehash: d8e13bcc03a02fd9dbc739566a92025a7b97d598
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516267"
---
# <a name="project-build-error-prj0002"></a>项目生成错误 PRJ0002

> 从返回的错误结果*命令行*。

命令，*命令行*，其中的从中的用户输入正确**属性页**对话框中，返回错误代码，但没有信息将出现在**输出**窗口.

对此错误的解决方法取决于哪种工具生成该错误。 MIDL，您将获得了解发生的问题，如果定义 /o （重定向输出）。

批处理文件，如自定义生成步骤或生成事件，不是故障条件有关的信息性也可能是导致此错误的原因。