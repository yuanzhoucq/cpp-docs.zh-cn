---
title: "错误 C1047 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1047
dev_langs:
- C++
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: b848f874f382e3d4f944a7eb372db9dcc5011f59
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1047"></a>错误 C1047
对象或库文件“file”是使用比创建其他对象所用编译器旧的编译器创建的；请重新生成旧的对象和库  
  
 当使用 **/LTCG** 生成的对象文件或库链接在一起，而这些对象文件或库是用不同版本的 Visual C++ 工具集生成的，则会导致 C1047。  
  
 当你开始使用新版本的编译器，而不完全重新生成现有对象文件或库时，可能出现这种情况。  
  
 若要解决 C1047，请重新生成所有对象文件或库。
