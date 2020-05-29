---
title: 错误 C1092
ms.date: 11/04/2016
f1_keywords:
- C1092
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
ms.openlocfilehash: af43ddb83e872762f720b156644e0d466957a8a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203874"
---
# <a name="fatal-error-c1092"></a>错误 C1092

“编辑并继续”不支持对数据类型的更改；需要生成

自上次成功生成后更改或添加了数据类型。

- "编辑并继续" 不支持对现有数据类型的更改，包括类、结构或枚举定义。 必须停止调试并生成应用程序。

- 如果程序数据库文件（如 vc*x*0 .pdb （其中*x*是正在使用的视觉对象C++的主要版本）是只读的，则 "编辑并继续" 不支持添加新的数据类型。 若要添加数据类型，编译器必须以写入模式打开 .pdb 文件。

### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>若要在不结束当前调试会话的情况下删除此错误

1. 将数据类型改回其在发生错误前的状态。

1. 在“调试” 菜单中选择“应用代码更改”。

### <a name="to-remove-this-error-without-changing-your-source-code"></a>若要在不更改源代码的情况下删除此错误

1. 在“调试” 菜单上，选择“停止调试”。

1. 在“生成” 菜单上，选择“生成”。

有关详细信息，请参阅 [受支持的代码更改](/visualstudio/debugger/supported-code-changes-cpp)。
