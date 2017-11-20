---
title: "资源编译器警告 RW4004 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RW4004
dev_langs: C++
helpviewer_keywords: RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aedc73ddc2934cf44ae5ebf98cf0e4e50814feb9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="resource-compiler-warning-rw4004"></a>资源编译器警告 RW4004
ASCII 字符不等价于虚拟键代码  
  
 字符串文本已用于 VIRTKEY 类型快捷键中的虚拟键代码。  
  
 此警告允许你继续操作，但请注意，生成的快捷键可能与你指示的字符串不匹配。 （VIRTKEYs 与 ASCII 快捷键使用不同的键代码。）  
  
 当字符串文本在语法上有效时，你只能确保获取你想要使用的快捷键**VK_\* #define** WINDOWS.h 中的值。