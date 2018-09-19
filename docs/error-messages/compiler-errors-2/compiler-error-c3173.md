---
title: 编译器错误 C3173 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3173
dev_langs:
- C++
helpviewer_keywords:
- C3173
ms.assetid: edf79e10-e8cf-4f76-8d33-ab9d05e974e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21a02ae1fcf4aff9636445979a81ef0a02ab5cb1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053019"
---
# <a name="compiler-error-c3173"></a>编译器错误 C3173

idl 合并中的版本不匹配

当对象文件包含嵌入的 idl 与以前版本的编译器生成时，将发生此错误。 编译器将编码以确保相同的编译器用于生成在.obj 文件中嵌入的 idl 内容也是用于嵌入的 idl 合并相同的编译器的版本号。

更新您的 Visual c + + 安装，以便所有工具都均来自最新的发行版本。