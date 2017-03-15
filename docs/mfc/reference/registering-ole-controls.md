---
title: "注册 OLE 控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- registering OLE controls
- OLE controls, registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
caps.latest.revision: 15
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 9c54fb7dc3802e78c8dc68df02ff55ef4732a36b
ms.lasthandoff: 02/24/2017

---
# <a name="registering-ole-controls"></a>注册 OLE 控件
与其他 OLE 服务器对象一样，OLE 控件可由其他 OLE 感知应用程序访问。 这是通过注册控件的类型库和类来实现的。  
  
 利用下列函数，您可在 Windows 注册数据库中添加和删除控件的类、属性页和类型库：  
  
### <a name="registering-ole-controls"></a>注册 OLE 控件  
  
|||  
|-|-|  
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|将控件的类添加到注册数据库。|  
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|将控件属性页添加到注册数据库。|  
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|将控件的类型库添加到注册数据库。|  
|[AfxOleUnregisterClass](#afxoleunregisterclass)|从注册数据库中删除控件类或属性页类。|  
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|从注册数据库中删除控件的类型库。|  
  
 一般在控件 DLL 的 `AfxOleRegisterTypeLib` 实现中调用 `DllRegisterServer`。 同样，`AfxOleUnregisterTypeLib` 由 `DllUnregisterServer` 调用。 `AfxOleRegisterControlClass`、`AfxOleRegisterPropertyPageClass` 和 `AfxOleUnregisterClass` 一般由控件的类工厂或属性页的 `UpdateRegistry` 成员函数调用。  
  
##  <a name="a-nameafxoleregistercontrolclassa--afxoleregistercontrolclass"></a><a name="afxoleregistercontrolclass"></a>AfxOleRegisterControlClass  
 向 Windows 注册数据库注册控件类。  
  
```   
BOOL AFXAPI AfxOleRegisterControlClass(
    HINSTANCE hInstance,  
    REFCLSID clsid,  
    LPCTSTR pszProgID,  
    UINT idTypeName,  
    UINT idBitmap,  
    int nRegFlags,  
    DWORD dwMiscStatus,  
    REFGUID tlid,  
    WORD wVerMajor,  
    WORD wVerMinor); 
```  
  
### <a name="parameters"></a>参数  
 `hInstance`  
 与控件类相关联的模块的实例句柄。  
  
 `clsid`  
 控件的唯一类 ID。  
  
 `pszProgID`  
 控件的唯一程序 ID。  
  
 `idTypeName`  
 包含控件的用户可读类型名称的字符串资源 ID。  
  
 *idBitmap*  
 用于表示 OLE 控件在工具栏上或调色板中的位图资源 ID。  
  
 `nRegFlags`  
 包含一个或多个以下标志︰  
  
- `afxRegInsertable`使控件才会出现在插入对象对话框中的 OLE 对象。  
  
- `afxRegApartmentThreading`ThreadingModel 注册表中设置线程模型 = 单元。  
  
- `afxRegFreeThreading`ThreadingModel 注册表中设置线程模型 = 免费。  
  
     您可以组合使用两个标记`afxRegApartmentThreading`和`afxRegFreeThreading`设置 ThreadingModel = Both。 请参阅[InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关线程处理模型注册的详细信息。  
  
> [!NOTE]
>  在 MFC 4.2 版之前的 MFC 版本中`int``nRegFlags`参数**BOOL**参数， *bInsertable*，，允许或禁止要从插入对象对话框中插入的控件。  
  
 *dwMiscStatus*  
 包含一个或多个以下的状态标志 (标志的说明，请参阅**OLEMISC**中的枚举[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]):  
  
-   OLEMISC_RECOMPOSEONRESIZE  
  
-   OLEMISC_ONLYICONIC  
  
-   OLEMISC_INSERTNOTREPLACE  
  
-   OLEMISC_STATIC  
  
-   OLEMISC_CANTLINKINSIDE  
  
-   OLEMISC_CANLINKBYOLE1  
  
-   OLEMISC_ISLINKOBJECT  
  
-   OLEMISC_INSIDEOUT  
  
-   OLEMISC_ACTIVATEWHENVISIBLE  
  
-   OLEMISC_RENDERINGISDEVICEINDEPENDENT  
  
-   OLEMISC_INVISIBLEATRUNTIME  
  
-   OLEMISC_ALWAYSRUN  
  
-   OLEMISC_ACTSLIKEBUTTON  
  
-   OLEMISC_ACTSLIKELABEL  
  
-   OLEMISC_NOUIACTIVATE  
  
-   OLEMISC_ALIGNABLE  
  
-   OLEMISC_IMEMODE  
  
-   OLEMISC_SIMPLEFRAME  
  
-   OLEMISC_SETCLIENTSITEFIRST  
  
 *tlid*  
 控件类的唯一 ID。  
  
 `wVerMajor`  
 控件类的主版本号。  
  
 `wVerMinor`  
 控件类的次版本号。  
  
### <a name="return-value"></a>返回值  
 非零，如果已注册的控件类;否则为 0。  
  
### <a name="remarks"></a>备注  
 这样，要由 OLE 控件可识别的容器使用的控件。 `AfxOleRegisterControlClass`使用控件的名称和位置在系统上的更新注册表，并设置该控件支持在注册表中的线程模型。 有关详细信息，请参阅[技术注意 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md)，"单元模型线程处理中 OLE 控件"和[有关进程和线程](http://msdn.microsoft.com/library/windows/desktop/ms681917)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAxCtl #&11;](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]  
  
 上面的示例演示如何`AfxOleRegisterControlClass`被调用，该标志可插入和标志的单元模型用 or 连在一起以创建第六个参数︰  
  
 [!code-cpp[NVC_MFCAxCtl #&12;](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]  
  
 该控件将显示在已启用容器插入对象对话框中，它将模型感知的单元。 单元模型识别控件必须确保该锁，就会保护数据的静态类，这样，一个单元中的控件在访问静态数据，而它未被禁用的计划程序完成后，并使用相同的静态数据的同一个类的另一个实例启动之前。 对静态数据的任何访问权限将由关键部分代码括起来。  
  
### <a name="requirements"></a>要求  
  **标头**afxctl.h  
  
##  <a name="a-nameafxoleregisterpropertypageclassa--afxoleregisterpropertypageclass"></a><a name="afxoleregisterpropertypageclass"></a>AfxOleRegisterPropertyPageClass  
 向 Windows 注册数据库注册属性页类。  
  
```  
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,  
   REFCLSID  clsid,  
   UINT idTypeName,  
   int nRegFlags); 
```  
  
### <a name="parameters"></a>参数  
 `hInstance`  
 与属性页类相关联的模块的实例句柄。  
  
 `clsid`  
 属性页上唯一类 ID。  
  
 `idTypeName`  
 包含属性页上的用户可读名称的字符串资源 ID。  
  
 `nRegFlags`  
 可能包含标志︰  
  
- `afxRegApartmentThreading`ThreadingModel 注册表中设置线程模型 = 单元。  
  
> [!NOTE]
>  在 MFC 4.2 版之前的 MFC 版本`int``nRegFlags`参数不可用。 另请注意，`afxRegInsertable`标志不是属性页的有效选项，如果将其设置将导致在 MFC 中的断言  
  
### <a name="return-value"></a>返回值  
 非零，如果已注册的控件类;否则为 0。  
  
### <a name="remarks"></a>备注  
 这允许使用由 OLE 控件可识别的容器的属性页。 `AfxOleRegisterPropertyPageClass`使用属性页名称和其位置在系统上的更新注册表，并设置该控件支持在注册表中的线程模型。 有关详细信息，请参阅[技术注意 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md)，"单元模型线程处理中 OLE 控件"和[有关进程和线程](http://msdn.microsoft.com/library/windows/desktop/ms681917)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="requirements"></a>要求  
  **标头**afxctl.h  
  
##  <a name="a-nameafxoleregistertypeliba--afxoleregistertypelib"></a><a name="afxoleregistertypelib"></a>AfxOleRegisterTypeLib  
 将类型库注册到 Windows 数据库并允许类型库由 OLE 控件可识别的其他容器使用。  
  
```   
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,  
    REFGUID tlid,  
    LPCTSTR pszFileName = NULL,  
    LPCTSTR pszHelpDir  = NULL); 
```  
  
### <a name="parameters"></a>参数  
 `hInstance`  
 与类型库关联的应用程序的实例句柄。  
  
 *tlid*  
 类型库的唯一 ID。  
  
 *pszFileName*  
 指向控件的本地化类型库 (.TLB) 文件的可选文件名的指针。  
  
 *pszHelpDir*  
 可从中找到类型库的帮助文件的名称的目录。 如果**NULL**，则假定帮助文件可与类型库本身位于同一目录中。  
  
### <a name="return-value"></a>返回值  
 如果已注册类型库，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数将在注册表中更新类型库名称及其在系统中的位置。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAutomation #&7;](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation #&8;](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxdisp.h  
  
##  <a name="a-nameafxoleunregisterclassa--afxoleunregisterclass"></a><a name="afxoleunregisterclass"></a>AfxOleUnregisterClass  
 从 Windows 注册数据库中删除控件或属性页类项。  
  
```   
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID); 
```  
  
### <a name="parameters"></a>参数  
 *clsID*  
 控件或属性页唯一类 ID。  
  
 `pszProgID`  
 控件或属性页的唯一程序 ID。  
  
### <a name="return-value"></a>返回值  
 如果控件或属性页类已成功注销; 则为非否则为 0。  
  
### <a name="requirements"></a>要求  
  **标头**afxctl.h  
  
##  <a name="a-nameafxoleunregistertypeliba--afxoleunregistertypelib"></a><a name="afxoleunregistertypelib"></a>AfxOleUnregisterTypeLib  
 调用此函数可从 Windows 注册数据库中删除的类型库项。  
  
```   
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID); 
```  
  
### <a name="parameters"></a>参数  
 `tlID`  
 类型库的唯一 ID。  
  
### <a name="return-value"></a>返回值  
 非零，如果类型库已成功注销;否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCAxCtl #&13;](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]  

### <a name="requirements"></a>要求  
  **标头**afxdisp.h  

## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

