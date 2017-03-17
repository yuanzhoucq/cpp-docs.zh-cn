---
title: "COleTemplateServer 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
dev_langs:
- C++
helpviewer_keywords:
- Automation servers [C++], implementing
- servers, OLE
- OLE server applications, managing server documents
- link containers [C++]
- visual editing, servers
- OLE link containers
- COleTemplateServer class
- OLE server applications, COleTemplateServer class
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ea82939cd0e8a8ba5612c65d238be8ae9996ef08
ms.lasthandoff: 02/24/2017

---
# <a name="coletemplateserver-class"></a>COleTemplateServer 类
用于 OLE 可视编辑服务器、自动化服务器和链接容器（支持链接到嵌入的应用程序）。  
  
## <a name="syntax"></a>语法  
  
```  
class COleTemplateServer : public COleObjectFactory  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|构造 `COleTemplateServer` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|连接到基础文档模板`COleObjectFactory`对象。|  
|[COleTemplateServer::Unregister](#unregister)|取消注册关联的文档模板。|  
|[COleTemplateServer::UpdateRegistry](#updateregistry)|向 OLE 系统注册表中注册的文档类型。|  
  
## <a name="remarks"></a>备注  
 此类派生自类[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); 通常情况下，您可以使用`COleTemplateServer`而不是派生您自己的类。 `COleTemplateServer`使用[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)对象来管理服务器文档。 使用`COleTemplateServer`实现整个服务器，也就是说，可以作为独立的应用程序运行的服务器时。 完全服务器通常是多文档界面 (MDI) 应用程序，虽然支持单文档界面 (SDI) 应用程序。 一个`COleTemplateServer`对象需要为应用程序支持的服务器文档的每个类型; 也就是说，如果服务器应用程序支持工作表和图表，您必须有两个`COleTemplateServer`对象。  
  
 `COleTemplateServer`重写`OnCreateInstance`所定义的成员函数`COleObjectFactory`。 此成员函数是由框架调用以创建正确类型的 c + + 对象。  
  
 有关服务器的详细信息，请参阅文章[服务器︰ 实现服务器](../../mfc/servers-implementing-a-server.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)  
  
 `COleTemplateServer`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdisp.h  
  
##  <a name="coletemplateserver"></a>COleTemplateServer::COleTemplateServer  
 构造 `COleTemplateServer` 对象。  
  
```  
COleTemplateServer();
```  
  
### <a name="remarks"></a>备注  
 有关使用的简要说明`COleTemplateServer`类，请参阅[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)类的概述。  
  
##  <a name="connecttemplate"></a>COleTemplateServer::ConnectTemplate  
 将文档模板由指向连接`pDocTemplate`对基础[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)对象。  
  
```  
void ConnectTemplate(
    REFCLSID clsid,  
    CDocTemplate* pDocTemplate,  
    BOOL bMultiInstance);
```  
  
### <a name="parameters"></a>参数  
 `clsid`  
 对该模板请求的 OLE 类 ID 的引用。  
  
 `pDocTemplate`  
 文档模板的指针。  
  
 `bMultiInstance`  
 指示应用程序的单个实例是否可以支持多个实例化。 如果**TRUE**，为每个请求创建的对象启动该应用程序的多个实例。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[CLSID 项](http://msdn.microsoft.com/library/windows/desktop/ms691424)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="unregister"></a>COleTemplateServer::Unregister  
 取消注册关联的文档模板。  
  
```  
BOOL Unregister();
```  
  
### <a name="return-value"></a>返回值  
 若成功，则为 TRUE；否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 EnterRemarks  
  
##  <a name="updateregistry"></a>COleTemplateServer::UpdateRegistry  
 从文档模板字符串中加载的文件类型信息，并将该信息放入 OLE 系统注册表。  
  
```  
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,  
    LPCTSTR* rglpszRegister = NULL,  
    LPCTSTR* rglpszOverwrite = NULL,  
    BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nAppType`  
 取值范围为**OLE_APPTYPE** AFXDISP 中定义的枚举。H。 它可以具有下列值之一︰  
  
- `OAT_INPLACE_SERVER`服务器有完整服务器用户界面。  
  
- `OAT_SERVER`服务器支持只嵌入。  
  
- `OAT_CONTAINER`容器支持链接到嵌入对象。  
  
- `OAT_DISPATCH_OBJECT`对象是`IDispatch`的支持。  
  
- **OAT_DOC_OBJECT_SERVER**服务器同时支持嵌入和文档对象组件模型。  
  
 `rglpszRegister`  
 仅当不存在的项写入到注册表项的列表。  
  
 `rglpszOverwrite`  
 写入而不考虑任何上述项是否存在注册表项的列表。  
  
 `bRegister`  
 确定是否要注册类。 如果`bRegister`是**TRUE**，与系统注册表中注册的类。 否则，取消注册类。  
  
### <a name="remarks"></a>备注  
 通过调用加载的注册信息[CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 检索子字符串是按索引标识的那些**regFileTypeId**， **regFileTypeName**，和**fileNewName**，如中所述`GetDocString`参考页。  
  
 如果**regFileTypeId**子字符串为空或者调用`GetDocString`失败的任何其他原因，此函数将失败并且不能在注册表中输入的文件信息。  
  
 在参数中的信息`rglpszRegister`和`rglpszOverwrite`写入到通过调用注册表[AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass)。 默认信息，当两个参数是注册**NULL**，适用于大多数应用程序。 这些参数中的信息的结构的信息，请参阅`AfxOleRegisterServerClass`。  
  
 有关详细信息，请参阅[实现 IDispatch 接口](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 HIERSVR](../../visual-cpp-samples.md)   
 [COleObjectFactory 类](../../mfc/reference/coleobjectfactory-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)   
 [COleServerItem 类](../../mfc/reference/coleserveritem-class.md)

