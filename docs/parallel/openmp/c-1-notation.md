---
title: C.1 表示法 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a23b2631-8096-4bf3-ac23-ba4f4bd7a52a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4bbb3190dd5aa32315cd8f402f92fd94893b4b27
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411867"
---
# <a name="c1-notation"></a>C.1 表示法

语法规则包含非终端，该名称后接一个冒号，跟在单独的行替换替代项。

语法的表达式项<sub>选择</sub>指示该字词是替换中的可选。

语法的表达式*术语*<sub>optseq</sub>等效于*术语 seq*<sub>选择</sub>具有下列附加规则：

*术语 seq* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*术语*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*术语 seq* *术语*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*术语 seq* **，** *术语*