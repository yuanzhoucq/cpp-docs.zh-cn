---
title: "项目生成错误 PRJ0024 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0024
dev_langs:
- C++
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2cf9ad974856f132599932a32b954e50453adf56
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0024"></a>项目生成错误 PRJ0024
无法为用户的 ANSI 代码页转换 Unicode 路径 path。  
  
 ***路径***是原始的 Unicode 版本的路径字符串。 在情况下可能出现此错误不能直接转换为 ANSI 当前的系统代码页的 Unicode 路径的情况。  
  
 如果你正在使用已开发的项目使用不在你的计算机的代码页的系统上，可能出现此错误。  
  
 此错误的解决方法是更新以使用 ANSI 文本，或要在你的计算机上安装的代码页，并将其设置为系统默认值的路径。