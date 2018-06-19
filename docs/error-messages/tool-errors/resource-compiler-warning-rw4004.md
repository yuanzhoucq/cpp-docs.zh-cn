---
title: 资源编译器警告 RW4004 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW4004
dev_langs:
- C++
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94bd1c043ac5660c5cb8fc8b2bfa1dd2f6968b55
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337101"
---
# <a name="resource-compiler-warning-rw4004"></a>资源编译器警告 RW4004
ASCII 字符不等价于虚拟键代码  
  
 字符串文本已用于 VIRTKEY 类型快捷键中的虚拟键代码。  
  
 此警告允许你继续操作，但请注意，生成的快捷键可能与你指示的字符串不匹配。 （VIRTKEYs 与 ASCII 快捷键使用不同的键代码。）  
  
 当字符串文本在语法上有效时，你只能确保获取你想要使用的快捷键**VK_\* #define** WINDOWS.h 中的值。