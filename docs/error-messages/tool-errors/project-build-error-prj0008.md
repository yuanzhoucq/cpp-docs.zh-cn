---
title: 项目生成错误 PRJ0008 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0008
dev_langs:
- C++
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4011a27b7e6707f9c9b4e3ed386306b00f2792cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0008"></a>项目生成错误 PRJ0008
无法删除文件 file。  
  
 **请确保文件未被另一个进程打开，并且未被写保护。**  
  
 重新生成或清理期间，Visual c + + 删除所有已知中间文件和输出文件的生成，以及满足中的通配符规范的任何文件**删除的扩展**中的属性[常规配置设置属性页](../../ide/general-property-page-project.md)。  
  
 如果 Visual c + + 不能删除文件，你将看到此错误。 若要解决此错误，使该文件，并且其目录可写执行生成的用户。