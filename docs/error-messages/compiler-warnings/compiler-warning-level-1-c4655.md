---
title: 编译器警告（等级 1）C4655
ms.date: 08/27/2018
f1_keywords:
- C4655
helpviewer_keywords:
- C4655
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
ms.openlocfilehash: d4c409c2d69099853a872142e05ef0fcda5a7655
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199526"
---
# <a name="compiler-warning-level-1-c4655"></a>编译器警告（等级 1）C4655

> "*symbol*"：自上次生成以来，变量类型是新的，或在其他地方以不同的方式定义

## <a name="remarks"></a>备注

自上次成功生成后你更改或添加了新的数据类型。 “编辑并继续”不支持对现有数据类型的更改。

此警告后跟 [错误 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)。 有关详细信息，请参阅 [受支持的代码更改](/visualstudio/debugger/supported-code-changes-cpp)。

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>若要在不结束当前调试会话的情况下删除此警告

1. 将数据类型改回其在发生错误前的状态。

2. 在“调试” 菜单中选择“应用代码更改”。

### <a name="to-remove-this-warning-without-changing-your-source-code"></a>若要在不更改源代码的情况下删除此警告

1. 在“调试” 菜单上，选择“停止调试”。

2. 在“生成” 菜单上，选择“生成”。
