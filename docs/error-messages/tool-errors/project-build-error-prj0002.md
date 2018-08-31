---
title: 项目生成错误 PRJ0002 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0002
dev_langs:
- C++
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc0e48130c17e04c2671395161452c9e66000047
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195710"
---
# <a name="project-build-error-prj0002"></a>项目生成错误 PRJ0002

> 从返回的错误结果*命令行*。

命令，*命令行*，其中的从中的用户输入正确**属性页**对话框中，返回错误代码，但没有信息将出现在**输出**窗口.

对此错误的解决方法取决于哪种工具生成该错误。 MIDL，您将获得了解发生的问题，如果定义 /o （重定向输出）。

批处理文件，如自定义生成步骤或生成事件，不是故障条件有关的信息性也可能是导致此错误的原因。