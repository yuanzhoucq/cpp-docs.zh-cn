---
title: 资源编译器错误 RC2144 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2144
dev_langs:
- C++
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b6f83f937e881cdee16c22120e6ac1839f7ad76
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-error-rc2144"></a>资源编译器错误 RC2144
主语言 ID 不是数字  
  
 主语言 ID 必须是十六进制语言 ID。 请参阅[语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)中*运行时库参考*有关有效的语言 Id 的列表。  
  
 如果已使用工具添加资源并将其从 .RC 文件中删除，也可能发生此错误。 若要解决此问题，请在文本编辑器中打开 .RC 文件并手动清理任何未使用的资源。