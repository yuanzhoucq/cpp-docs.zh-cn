---
title: C.1 表示法
ms.date: 11/04/2016
ms.assetid: a23b2631-8096-4bf3-ac23-ba4f4bd7a52a
ms.openlocfilehash: 593450b6dd7dcb30adbf8546ad96ff716c6fbc1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473978"
---
# <a name="c1-notation"></a>C.1 表示法

语法规则包含非终端，该名称后接一个冒号，跟在单独的行替换替代项。

语法的表达式项<sub>选择</sub>指示该字词是替换中的可选。

语法的表达式*术语*<sub>optseq</sub>等效于*术语 seq*<sub>选择</sub>具有下列附加规则：

*术语 seq* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*术语*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*术语 seq* *术语*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*术语 seq* **，** *术语*