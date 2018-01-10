---
title: "WSADATA 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WSADATA
dev_langs: C++
helpviewer_keywords: WSADATA structure [MFC]
ms.assetid: 80cc60e5-f9ae-4290-8ed5-07003136627d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 24cfbeb0e917914881587cb70fd345a903a08ecc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="wsadata-structure"></a>WSADATA 结构
`WSADATA` 结构用于存储通过调用 `AfxSocketInit` 全局函数返回的 Windows 套接字初始化信息。  
  
## <a name="syntax"></a>语法  
  
```  
struct WSAData {  
    WORD wVersion;  
    WORD wHighVersion;  
    char szDescription[WSADESCRIPTION_LEN+1];  
    char szSystemStatus[WSASYSSTATUS_LEN+1];  
    unsigned short iMaxSockets;  
    unsigned short iMaxUdpDg;  
    char FAR* lpVendorInfo;  
};  
```  
  
#### <a name="parameters"></a>参数  
 *wVersion*  
 Windows 套接字的动态链接库希望调用方使用的 Windows 套接字规范的版本。  
  
 *wHighVersion*  
 此 DLL 可支持的 Windows 套接字规范的最高版本（按如上编码）。 通常情况下，这是与相同**wVersion**。  
  
 *szDescription*  
 不以 null 结尾的 ASCII 字符串，Windows 套接字的动态链接库将 Windows 套接字实现的描述（包括供应商标识）复制到其中。 文本（最多 256 个字符长）可包含任何字符，但供应商应谨慎包含控制和格式设置字符：应用程序放置此类字符最有可能的用途是为了在状态消息中显示（可能截断）它。  
  
 *szSystemStatus*  
 不以 null 结尾的 ASCII 字符串，Windows 套接字的动态链接库会将相关状态或配置信息复制到其中。 Windows 套接字 DLL 应使用此字段，仅当信息可能对用户有用或支持人员;不应该将它作为的扩展**szDescription**字段。  
  
 *iMaxSockets*  
 一个进程潜在可打开的套接字的最大数量。 Windows 套接字实现可为要分配给任何进程的套接字提供一个全局池；也可以为套接字分配每进程资源。 数字可以很好地反映 Windows 套接字的动态链接库或联网软件的配置方式。 应用程序编写器可使用此数字作为 Windows 套接字实现是否可由应用程序使用的原始指示。 例如，X Windows 服务器可能会检查**iMaxSockets**首次启动时： 如果它是小于 8，应用程序将显示错误消息指示用户重新配置联网软件。 (这是在其中的情况下**szSystemStatus**可能会使用文本。)显然就会实际分配特定的应用程序不能保证**iMaxSockets**套接字，因为可能有其他 Windows 套接字应用程序正在使用。  
  
 *iMaxUdpDg*  
 Windows 套接字应用程序可发送或接收的最大用户数据报协议 (UDP) 大小（以字节为单位）。 如果实现未不施加任何限制， **iMaxUdpDg**为零。 在 Berkeley 套接字的许多实现中，UDP 数据报（如有必要，将其碎片化）上具有 8192 字节的隐式限制。 例如，Windows 套接字实现可以基于碎片重组缓冲区的分配施加限制。 最小值**iMaxUdpDg**合规 Windows 套接字实现为 512。 请注意，无论的值如何**iMaxUdpDg**，它是不宜尝试发送大于比最大传输单元 (MTU) 网络的广播数据报。 （Windows 套接字 API 未提供发现 MTU 的机制，但 MTU 必须小于 512 字节。）  
  
 *lpVendorInfo*  
 指向供应商特定数据结构的远指针。 此结构的定义（如果提供）将超出 Windows 套接字规范的范围。  
  
> [!NOTE]
>  在 MFC 中，`WSADATA` 结构将由 `AfxSocketInit` 函数返回，该函数是您在 `InitInstance` 函数中调用的。 如果您之后需要使用其中的信息，则可检索此结构并将其存储在程序中。  
  
## <a name="requirements"></a>惠?  
 **标头：** winsock2.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)

