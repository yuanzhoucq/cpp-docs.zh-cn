---
title: "编译器警告 （等级 1） C4819 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4819
dev_langs:
- C++
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b515a3f5e840bbc93f37420866023ee778b404ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4819"></a>编译器警告（等级 1）C4819
该文件包含不能在当前代码页（数字）中表示的字符。 以 Unicode 格式保存该文件防止数据丢失。  
  
 在具有不能表示文件中所有字符的代码页的系统上编译 ANSI 源文件时，出现 C4819。  
  
 若要解决 C4819，请以 Unicode 格式保存该文件。 在 Visual Studio 中，选择**文件**，**高级保存选项**。 在**高级保存选项**对话框框中，选择可以表示该文件中的所有字符编码-例如，utf-8-，然后选择**确定**。