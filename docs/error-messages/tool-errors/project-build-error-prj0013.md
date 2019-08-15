---
title: 项目生成错误 PRJ0013
ms.date: 11/04/2016
f1_keywords:
- PRJ0013
helpviewer_keywords:
- PRJ0013
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
ms.openlocfilehash: c78f029a3fb0e89913ce9b5ce221569e67d8faf6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509928"
---
# <a name="project-build-error-prj0013"></a>项目生成错误 PRJ0013

系统资源可能严重不足。 无法创建启动生成所需的管道。

该错误指示系统资源不足。 若要解决该错误，请减少其他进程/应用程序使用的系统资源。

如果没有足够的安全级别来创建管道, 也会发生此错误 (请参阅[CreatePipe](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe))。