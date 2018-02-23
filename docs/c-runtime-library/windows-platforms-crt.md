---
title: "Windows 平台 (CRT) | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- CRT, compatibility
- backward compatibility [C++], C run-time libraries
- compatibility [C++], C run-time libraries
- MBCS [C++], Win32 platforms
- operating systems [C++]
- Unicode [C++], Win32 platforms
ms.assetid: 0aacaf45-6dc4-4908-bd52-57abac7b39f6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c1a5e7898cad7120333bd0549a44931d9e23640c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="windows-platforms-crt"></a>Windows 平台 (CRT)

用于 Visual Studio 的 C 运行时库支持当前版本的 Windows 和 Windows Server、[!INCLUDE[win8](../build/reference/includes/win8_md.md)]、[!INCLUDE[winserver8](../build/reference/includes/winserver8_md.md)]、[!INCLUDE[win7](../build/includes/win7_md.md)]、[!INCLUDE[winsvr08](../build/reference/includes/winsvr08_md.md)] 和 Windows Vista ，并选择性地支持适用于 x86 的 [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 3 (SP3)、适用于 x64 的 [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 2 (SP2) 和同时适用于 x86 和 x64 的 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] Service Pack 2 (SP2)。 所有这些操作系统都支持 Windows 桌面 API (Win32) 并提供 Unicode 支持。 此外，所有 Win32 应用程序都能使用多字节字符集 (MBCS)。

> [!NOTE]
> Visual Studio 2017 中的**使用 C++ 的桌面开发**工作负载的默认安装不包括 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 支持和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 开发。 必须安装可选组件**针对 C++ 的 Windows XP 支持**，用于启用 Windows XP 平台工具集。

## <a name="see-also"></a>请参阅

[兼容性](../c-runtime-library/compatibility.md)  
