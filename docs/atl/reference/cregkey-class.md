---
title: "CRegKey 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRegKey
- ATLBASE/ATL::CRegKey
- ATLBASE/ATL::CRegKey::CRegKey
- ATLBASE/ATL::CRegKey::Attach
- ATLBASE/ATL::CRegKey::Close
- ATLBASE/ATL::CRegKey::Create
- ATLBASE/ATL::CRegKey::DeleteSubKey
- ATLBASE/ATL::CRegKey::DeleteValue
- ATLBASE/ATL::CRegKey::Detach
- ATLBASE/ATL::CRegKey::EnumKey
- ATLBASE/ATL::CRegKey::Flush
- ATLBASE/ATL::CRegKey::GetKeySecurity
- ATLBASE/ATL::CRegKey::NotifyChangeKeyValue
- ATLBASE/ATL::CRegKey::Open
- ATLBASE/ATL::CRegKey::QueryBinaryValue
- ATLBASE/ATL::CRegKey::QueryDWORDValue
- ATLBASE/ATL::CRegKey::QueryGUIDValue
- ATLBASE/ATL::CRegKey::QueryMultiStringValue
- ATLBASE/ATL::CRegKey::QueryQWORDValue
- ATLBASE/ATL::CRegKey::QueryStringValue
- ATLBASE/ATL::CRegKey::QueryValue
- ATLBASE/ATL::CRegKey::RecurseDeleteKey
- ATLBASE/ATL::CRegKey::SetBinaryValue
- ATLBASE/ATL::CRegKey::SetDWORDValue
- ATLBASE/ATL::CRegKey::SetGUIDValue
- ATLBASE/ATL::CRegKey::SetKeySecurity
- ATLBASE/ATL::CRegKey::SetKeyValue
- ATLBASE/ATL::CRegKey::SetMultiStringValue
- ATLBASE/ATL::CRegKey::SetQWORDValue
- ATLBASE/ATL::CRegKey::SetStringValue
- ATLBASE/ATL::CRegKey::SetValue
- ATLBASE/ATL::CRegKey::m_hKey
- ATLBASE/ATL::CRegKey::m_pTM
dev_langs:
- C++
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dffc650c54c4a50fb4b3b1fe2c22ac82501b8b45
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cregkey-class"></a>CRegKey 类
此类提供用于操作系统注册表中的条目的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CRegKey
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CRegKey::CRegKey](#cregkey)|构造函数。|  
|[CRegKey:: ~ CRegKey](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRegKey::Attach](#attach)|调用此方法以将附加到 HKEY`CRegKey`对象通过设置[m_hKey](#m_hkey)成员句柄`hKey`。|  
|[CRegKey::Close](#close)|调用此方法以释放[m_hKey](#m_hkey)成员处理，并将其设置为 NULL。|  
|[CRegKey::Create](#create)|调用此方法创建指定的键，如果不存在作为项的子项`hKeyParent`。|  
|[CRegKey::DeleteSubKey](#deletesubkey)|调用此方法以从注册表中删除指定的键。|  
|[CRegKey::DeleteValue](#deletevalue)|调用此方法来删除从值字段[m_hKey](#m_hkey)。|  
|[CRegKey::Detach](#detach)|调用此方法以分离[m_hKey](#m_hkey)从成员句柄`CRegKey`对象，并将`m_hKey`为 NULL。|  
|[CRegKey::EnumKey](#enumkey)|调用此方法以枚举打开注册表项的子项。|  
|[CRegKey::Flush](#flush)|调用此方法以向注册表写入的所有打开的注册表项的属性。|  
|[CRegKey::GetKeySecurity](#getkeysecurity)|调用此方法用于检索保护打开注册表项的安全描述符的副本。|  
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|此方法通知调用方对属性或打开注册表项的内容进行的更改。|  
|[CRegKey::Open](#open)|调用此方法以打开指定的键，并设置[m_hKey](#m_hkey)到该项的句柄。|  
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|调用此方法以检索指定的值名称的二进制数据。|  
|[CRegKey::QueryDWORDValue](#querydwordvalue)|调用此方法以检索指定的值名称的 DWORD 数据。|  
|[CRegKey::QueryGUIDValue](#queryguidvalue)|调用此方法以检索指定的值名称的 GUID 数据。|  
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|调用此方法以检索指定的值名称的名数据。|  
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|调用此方法以检索指定的值名称的 QWORD 数据。|  
|[CRegKey::QueryStringValue](#querystringvalue)|调用此方法以检索指定的值名称的字符串数据。|  
|[CRegKey::QueryValue](#queryvalue)|调用此方法以检索指定的值字段的数据[m_hKey](#m_hkey)。 此方法的早期版本不再受支持，标记为**ATL_DEPRECATED**。|  
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|调用此方法以从注册表中删除指定的键并删除任何子项中显式删除。|  
|[CRegKey::SetBinaryValue](#setbinaryvalue)|调用此方法以设置注册表项的二进制值。|  
|[CRegKey::SetDWORDValue](#setdwordvalue)|调用此方法以设置注册表项 DWORD 值。|  
|[CRegKey::SetGUIDValue](#setguidvalue)|调用此方法以设置注册表项的 GUID 值。|  
|[CRegKey::SetKeySecurity](#setkeysecurity)|调用此方法以设置注册表项的安全性。|  
|[CRegKey::SetKeyValue](#setkeyvalue)|调用此方法以在指定键指定的值字段中存储数据。|  
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|调用此方法以设置的注册表项名的值。|  
|[CRegKey::SetQWORDValue](#setqwordvalue)|调用此方法以设置注册表项的 QWORD 值。|  
|[CRegKey::SetStringValue](#setstringvalue)|调用此方法以设置注册表项的字符串值。|  
|[CRegKey::SetValue](#setvalue)|调用此方法以将数据存储在指定的值字段[m_hKey](#m_hkey)。 此方法的早期版本不再受支持，标记为**ATL_DEPRECATED**。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CRegKey::operator HKEY](#operator_hkey)|将转换`CRegKey`HKEY 到的对象。|  
|[CRegKey::operator =](#operator_eq)|赋值运算符。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CRegKey::m_hKey](#m_hkey)|包含与关联的注册表项的句柄`CRegKey`对象。|  
|[CRegKey::m_pTM](#m_ptm)|指向`CAtlTransactionManager`对象|  
  
## <a name="remarks"></a>备注  
 `CRegKey`提供用于创建和删除系统注册表中键和值的方法。 注册表包含安装特定组的系统组件，如软件版本号、 安装的硬件和 COM 对象的逻辑物理映射定义。  
  
 `CRegKey`为给定机提供一个编程接口，对系统注册表。 例如，若要打开特定的注册表项，请调用`CRegKey::Open`。 若要检索或修改数据值，调用`CRegKey::QueryValue`或`CRegKey::SetValue`分别。 若要关闭一个密钥，调用`CRegKey::Close`。  
  
 当关闭某个键时，其注册表数据将写入 （刷新） 硬盘。 此过程可能需要几秒钟时间。 如果你的应用程序必须显式将注册表数据写入到硬盘，则可以调用[RegFlushKey](http://msdn.microsoft.com/library/windows/desktop/ms724867) Win32 函数。 但是， **RegFlushKey**使用多系统资源，仅当绝对必要时才应调用。  
  
> [!IMPORTANT]
>  允许调用方指定的注册表位置的任何方法也可能会读取不能为受信任的数据。 方法，能利用[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)应考虑到此函数不显式处理字符串，它们是 NULL 终止的考虑。 有关中，调用代码应检查这两个条件。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlbase.h  
  
##  <a name="attach"></a>CRegKey::Attach  
 调用此方法以将附加到 HKEY`CRegKey`对象通过设置[m_hKey](#m_hkey)成员句柄`hKey`。  
  
```
void Attach(HKEY hKey) throw();
```  
  
### <a name="parameters"></a>参数  
 `hKey`  
 注册表项的句柄。  
  
### <a name="remarks"></a>备注  
 **附加**将断言如果`m_hKey`为非 NULL。  
  
##  <a name="close"></a>CRegKey::Close  
 调用此方法以释放[m_hKey](#m_hkey)成员处理，并将其设置为 NULL。  
  
```
LONG Close() throw();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，返回 ERROR_SUCCESS;否则返回一个错误值。  
  
##  <a name="create"></a>CRegKey::Create  
 调用此方法创建指定的键，如果不存在作为项的子项`hKeyParent`。  
  
```
LONG Create(  
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPTSTR lpszClass = REG_NONE,
    DWORD dwOptions = REG_OPTION_NON_VOLATILE,
    REGSAM samDesired = KEY_READ | KEY_WRITE,
    LPSECURITY_ATTRIBUTES lpSecAttr = NULL,
    LPDWORD lpdwDisposition = NULL) throw();
```  
  
### <a name="parameters"></a>参数  
 `hKeyParent`  
 开放式密钥句柄。  
  
 `lpszKeyName`  
 指定要创建或打开的密钥的名称。 此名称必须是项的子项`hKeyParent`。  
  
 `lpszClass`  
 指定要创建或打开的键的类。 默认值为 REG_NONE。  
  
 `dwOptions`  
 键的选项。 默认值为 REG_OPTION_NON_VOLATILE。 有关可能的值和说明的列表，请参阅[RegCreateKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724844) Windows SDK 中。  
  
 `samDesired`  
 安全的访问键。 默认值是 KEY_READ &#124;KEY_WRITE。 有关可能的值和说明的列表，请参阅**RegCreateKeyEx**。  
  
 *lpSecAttr*  
 指向的指针[SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)结构，指示是否可以由子进程继承的密钥句柄。 默认情况下，此参数为 NULL （即不能继承句柄）。  
  
 *lpdwDisposition*  
 [out]如果非 NULL，检索 REG_CREATED_NEW_KEY （如果键不存在，并且已创建） 或 REG_OPENED_EXISTING_KEY （如果键存在并已打开）。  
  
### <a name="return-value"></a>返回值  
 如果成功，返回 ERROR_SUCCESS 并打开密钥。 如果此方法失败，返回值是在 WINERROR 中定义一个非零错误代码。H。  
  
### <a name="remarks"></a>备注  
 **创建**设置[m_hKey](#m_hkey)到该项的句柄的成员。  
  
##  <a name="cregkey"></a>CRegKey::CRegKey  
 构造函数。  
  
```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```  
  
### <a name="parameters"></a>参数  
 `key`  
 对 `CRegKey` 对象的引用。  
  
 `hKey`  
 注册表项句柄。  
  
 `pTM`  
 指向 CAtlTransactionManager 对象的指针  
  
### <a name="remarks"></a>备注  
 创建一个新的 `CRegKey` 对象。 可以从现有创建该对象`CRegKey`对象，或从注册表项的句柄。  
  
##  <a name="dtor"></a>CRegKey:: ~ CRegKey  
 析构函数。  
  
```
~CRegKey() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数版本`m_hKey`。  
  
##  <a name="deletesubkey"></a>CRegKey::DeleteSubKey  
 调用此方法以从注册表中删除指定的键。  
  
```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```  
  
### <a name="parameters"></a>参数  
 `lpszSubKey`  
 指定要删除的键的名称。 此名称必须是项的子项[m_hKey](#m_hkey)。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 ERROR_SUCCESS。 如果此方法失败，返回值是在 WINERROR 中定义一个非零错误代码。H。  
  
### <a name="remarks"></a>备注  
 `DeleteSubKey`只能删除一个不具有任何子项项。 如果项具有子项，调用[RecurseDeleteKey](#recursedeletekey)相反。  
  
##  <a name="deletevalue"></a>CRegKey::DeleteValue  
 调用此方法来删除从值字段[m_hKey](#m_hkey)。  
  
```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```  
  
### <a name="parameters"></a>参数  
 `lpszValue`  
 指定要删除的值字段。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 ERROR_SUCCESS。 如果此方法失败，返回值是在 WINERROR 中定义一个非零错误代码。H。  
  
##  <a name="detach"></a>CRegKey::Detach  
 调用此方法以分离[m_hKey](#m_hkey)从成员句柄`CRegKey`对象，并将`m_hKey`为 NULL。  
  
```
HKEY Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 与关联 HKEY`CRegKey`对象。  
  
##  <a name="enumkey"></a>CRegKey::EnumKey  
 调用此方法以枚举打开注册表项的子项。  
  
```
LONG EnumKey(  
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```  
  
### <a name="parameters"></a>参数  
 `iIndex`  
 子项的索引。 此参数应为零的第一次调用，以便后续调用然后递增  
  
 `pszName`  
 为接收该子项，包括终止 null 字符的名称的缓冲区的指针。 仅的子项的名称将复制到的缓冲区，不是完整密钥层次结构。  
  
 *pnNameLength*  
 为指定的大小，以 TCHARs，由指定的缓冲区的变量的指针`pszName`参数。 此大小应包括终止 null 字符。 方法返回时，通过指向的变量*pnNameLength*包含存储缓冲区中的字符数。 返回的计数不包括终止 null 字符。  
  
 *pftLastWriteTime*  
 指向一个变量来接收时间枚举的子项上次写入。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回值是 ERROR_SUCCESS。 如果此方法失败，返回值是在 WINERROR 中定义一个非零错误代码。H。  
  
### <a name="remarks"></a>备注  
 若要枚举子项，调用`CRegKey::EnumKey`索引为零。 递增的索引值和重复，直到该方法返回 ERROR_NO_MORE_ITEMS。 有关详细信息，请参阅[RegEnumKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724862) Windows SDK 中。  
  
##  <a name="flush"></a>CRegKey::Flush  
 调用此方法以向注册表写入的所有打开的注册表项的属性。  
  
```
LONG Flush() throw();
```  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回值是 ERROR_SUCCESS。 如果此方法失败，返回值是在 WINERROR 中定义一个非零错误代码。H。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[RegEnumFlush](http://msdn.microsoft.com/library/windows/desktop/ms724867) Windows SDK 中。  
  
##  <a name="getkeysecurity"></a>CRegKey::GetKeySecurity  
 调用此方法用于检索保护打开注册表项的安全描述符的副本。  
  
```
LONG GetKeySecurity(  
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 `si`  
 [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573)值，该值指示请求的安全信息。  
  
 `psd`  
 指向接收的请求的安全描述符的副本的缓冲区的指针。  
  
 `pnBytes`  
 大小 （字节），指向缓冲区`psd`。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回值是 ERROR_SUCCESS。 如果此方法失败，返回值是在 WINERROR 中定义一个非零错误代码。H。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[RegGetKeySecurity](http://msdn.microsoft.com/library/windows/desktop/aa379313)。  
  
##  <a name="m_hkey"></a>CRegKey::m_hKey  
 包含与关联的注册表项的句柄`CRegKey`对象。  
  
```
HKEY m_hKey;
```  
  
##  <a name="m_ptm"></a>CRegKey::m_pTM  
 指向 `CAtlTransactionManager` 对象的指针。  
  
```
CAtlTransactionManager* m_pTM;
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="notifychangekeyvalue"></a>CRegKey::NotifyChangeKeyValue  
 此方法通知调用方对属性或打开注册表项的内容进行的更改。  
  
```
LONG NotifyChangeKeyValue(  
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```  
  
### <a name="parameters"></a>参数  
 *bWatchSubtree*  
 指定一个标志，指示是否报告中指定的键和及其所有子项或仅在指定的键中的更改。 如果此参数为 TRUE，该方法将报告项及其子项中的更改。 如果参数为 FALSE，该方法将报告仅在密钥中的更改。  
  
 *dwNotifyFilter*  
 指定应报告一组控制哪些更改的标志。 此参数可以是以下值的组合：  
  
|“值”|含义|  
|-----------|-------------|  
|REG_NOTIFY_CHANGE_NAME|如果添加或删除一个子项，则通知调用方。|  
|REG_NOTIFY_CHANGE_ATTRIBUTES|通知的密钥，如安全描述符信息的属性的更改的调用方。|  
|REG_NOTIFY_CHANGE_LAST_SET|通知调用方对密钥的值的更改。 这可能包括添加或删除一个值，或更改现有值。|  
|REG_NOTIFY_CHANGE_SECURITY|通知调用方对密钥的安全描述符的更改。|  
  
 `hEvent`  
 事件的句柄。 如果*bAsync*参数为 TRUE，该方法将立即返回，更改报告的信号此事件。 如果`bAsync`为 FALSE 时，`hEvent`将被忽略。  
  
 `bAsync`  
 指定一个标志，指示该方法将如何报告更改。 如果此参数为 TRUE，该方法将立即返回，并通过发送信号的指定公共事件报告更改。 当此参数为 FALSE 时，该方法不返回之前发生了更改。 如果`hEvent`未指定有效的事件，`bAsync`参数不能为 TRUE。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回值是 ERROR_SUCCESS。 如果此方法失败，返回值是在 WINERROR 中定义一个非零错误代码。H。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  如果删除指定的键，此方法不会通知调用方。  
  
 有关更多详细信息和示例程序，请参阅[RegNotifyChangeKeyValue](http://msdn.microsoft.com/library/windows/desktop/ms724892)。  
  
##  <a name="open"></a>CRegKey::Open  
 调用此方法以打开指定的键，并设置[m_hKey](#m_hkey)到该项的句柄。  
  
```
LONG Open(  
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```  
  
### <a name="parameters"></a>参数  
 `hKeyParent`  
 开放式密钥句柄。  
  
 `lpszKeyName`  
 指定要创建或打开的密钥的名称。 此名称必须是项的子项`hKeyParent`。  
  
 `samDesired`  
 安全的访问键。 默认值为 KEY_ALL_ACCESS。 有关可能的值和说明的列表，请参阅[RegCreateKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724844) Windows SDK 中。  
  
### <a name="return-value"></a>返回值  
 如果成功，返回 ERROR_SUCCESS;否则，在 WINERROR 中定义了非零错误值。H。  
  
### <a name="remarks"></a>备注  
 如果`lpszKeyName`参数为 NULL 或点为空字符串，**打开**打开由标识的键的新句柄`hKeyParent`，但不会关闭任何先前已打开的句柄。  
  
 与不同[CRegKey::Create](#create)，**打开**不会创建指定的键不存在。  
  
##  <a name="operator_hkey"></a>CRegKey::operator HKEY  
 将转换`CRegKey`HKEY 到的对象。  
  
```  
operator HKEY() const throw();
```  
  
##  <a name="operator_eq"></a>CRegKey::operator =  
 赋值运算符。  
  
```
CRegKey& operator= (CRegKey& key) throw();
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要复制的键。  
  
### <a name="return-value"></a>返回值  
 返回对新的密钥的引用。  
  
### <a name="remarks"></a>备注  
 此运算符分离`key`从其当前的对象并将它分配给`CRegKey`对象。  
  
##  <a name="querybinaryvalue"></a>CRegKey::QueryBinaryValue  
 调用此方法以检索指定的值名称的二进制数据。  
  
```
LONG QueryBinaryValue(  
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszValueName`  
 指向以 null 结尾的字符串，包含要查询的值的名称。  
  
 `pValue`  
 指向接收值的数据缓冲区的指针。  
  
 `pnBytes`  
 指向的变量，以字节为单位，缓冲区的指定的大小，指针指向的`pValue`参数。 方法返回时，此变量包含数据复制到缓冲区的大小。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 ERROR_SUCCESS。 如果该方法无法读取一个值，它返回 WINERROR 中定义的非零错误代码。H。 如果引用的数据不是 REG_BINARY 类型，则返回 ERROR_INVALID_DATA。  
  
### <a name="remarks"></a>备注  
 此方法使用**RegQueryValueEx** ，并确认返回正确的数据类型。 请参阅[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)有关详细信息。  
  
> [!IMPORTANT]
>  此方法允许调用方指定可能读取数据不能为受信任的任何注册表位置。 此外， [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)函数使用此方法不显式处理作为 NULL 结尾的字符串。 有关中，调用代码应检查这两个条件。  
  
##  <a name="querydwordvalue"></a>CRegKey::QueryDWORDValue  
 调用此方法以检索指定的值名称的 DWORD 数据。  
  
```
LONG QueryDWORDValue(  
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszValueName`  
 指向以 null 结尾的字符串，包含要查询的值的名称。  
  
 `dwValue`  
 指向接收 DWORD 缓冲区的指针。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 ERROR_SUCCESS。 如果该方法无法读取一个值，它返回 WINERROR 中定义的非零错误代码。H。 如果引用的数据不是类型 REG_DWORD，则返回 ERROR_INVALID_DATA。  
  
### <a name="remarks"></a>备注  
 此方法使用**RegQueryValueEx** ，并确认返回正确的数据类型。 请参阅[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)有关详细信息。  
  
> [!IMPORTANT]
>  此方法允许调用方指定可能读取数据不能为受信任的任何注册表位置。 此外， [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)函数使用此方法不显式处理作为 NULL 结尾的字符串。 有关中，调用代码应检查这两个条件。  
  
##  <a name="queryguidvalue"></a>CRegKey::QueryGUIDValue  
 调用此方法以检索指定的值名称的 GUID 数据。  
  
```
LONG QueryGUIDValue(  
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszValueName`  
 指向以 null 结尾的字符串，包含要查询的值的名称。  
  
 `guidValue`  
 指向接收 GUID 的变量的指针。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 ERROR_SUCCESS。 如果该方法无法读取一个值，它返回 WINERROR 中定义的非零错误代码。H。 如果引用的数据不是有效的 GUID，则返回 ERROR_INVALID_DATA。  
  
### <a name="remarks"></a>备注  
 此方法使用`CRegKey::QueryStringValue`并将字符串转换为 GUID 使用[CLSIDFromString](http://msdn.microsoft.com/library/windows/desktop/ms680589)。  
  
> [!IMPORTANT]
>  此方法允许调用方指定可能读取数据不能为受信任的任何注册表位置。  
  
##  <a name="querymultistringvalue"></a>CRegKey::QueryMultiStringValue  
 调用此方法以检索指定的值名称的名数据。  
  
```
LONG QueryMultiStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszValueName`  
 指向以 null 结尾的字符串，包含要查询的值的名称。  
  
 `pszValue`  
 指向接收名数据缓冲区的指针。 Multistring 上是以 null 结尾的字符串，由两个 null 字符终止的数组。  
  
 `pnChars`  
 大小，以 TCHARs，指向缓冲区的`pszValue`。 方法返回时，`pnChars`包含的大小，以 TCHARs，包括终止 null 字符检索，multistring 上。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 ERROR_SUCCESS。 如果该方法无法读取一个值，它返回 WINERROR 中定义的非零错误代码。H。 如果不属于类型 REG_MULTI_SZ 引用的数据，则返回 ERROR_INVALID_DATA。  
  
### <a name="remarks"></a>备注  
 此方法使用**RegQueryValueEx** ，并确认返回正确的数据类型。 请参阅[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)有关详细信息。  
  
> [!IMPORTANT]
>  此方法允许调用方指定可能读取数据不能为受信任的任何注册表位置。 此外， [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)函数使用此方法不显式处理作为 NULL 结尾的字符串。 有关中，调用代码应检查这两个条件。  
  
##  <a name="queryqwordvalue"></a>CRegKey::QueryQWORDValue  
 调用此方法以检索指定的值名称的 QWORD 数据。  
  
```
LONG QueryQWORDValue(  
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszValueName`  
 指向以 null 结尾的字符串，包含要查询的值的名称。  
  
 `qwValue`  
 指向接收 QWORD 缓冲区的指针。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 ERROR_SUCCESS。 如果该方法无法读取一个值，它返回 WINERROR 中定义的非零错误代码。H。 如果不属于类型 REG_QWORD 引用的数据，则返回 ERROR_INVALID_DATA。  
  
### <a name="remarks"></a>备注  
 此方法使用**RegQueryValueEx** ，并确认返回正确的数据类型。 请参阅[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)有关详细信息。  
  
> [!IMPORTANT]
>  此方法允许调用方指定可能读取数据不能为受信任的任何注册表位置。 此外， [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)函数使用此方法不显式处理作为 NULL 结尾的字符串。 有关中，调用代码应检查这两个条件。  
  
##  <a name="querystringvalue"></a>CRegKey::QueryStringValue  
 调用此方法以检索指定的值名称的字符串数据。  
  
```
LONG QueryStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszValueName`  
 指向以 null 结尾的字符串，包含要查询的值的名称。  
  
 `pszValue`  
 为接收字符串数据的缓冲区的指针。  
  
 `pnChars`  
 大小，以 TCHARs，指向缓冲区的`pszValue`。 方法返回时，`pnChars`包含的大小，以 TCHARs 的检索，包括终止 null 字符的字符串。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 ERROR_SUCCESS。 如果该方法无法读取一个值，它返回 WINERROR 中定义的非零错误代码。H。 如果引用的数据不是类型为 REG_SZ，则返回 ERROR_INVALID_DATA。 如果该方法返回 ERROR_MORE_DATA，`pnChars`等于零，不是以字节为单位的所需的缓冲区大小。  
  
### <a name="remarks"></a>备注  
 此方法使用**RegQueryValueEx** ，并确认返回正确的数据类型。 请参阅[RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)有关详细信息。  
  
> [!IMPORTANT]
>  此方法允许调用方指定可能读取数据不能为受信任的任何注册表位置。 此外， [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911)函数使用此方法不显式处理作为 NULL 结尾的字符串。 有关中，调用代码应检查这两个条件。  
  
##  <a name="queryvalue"></a>CRegKey::QueryValue  
 调用此方法以检索指定的值字段的数据[m_hKey](#m_hkey)。 此方法的早期版本不再受支持，标记为**ATL_DEPRECATED**。  
  
```
LONG QueryValue(  
    LPCTSTR pszValueName,
    DWORD* pdwType,
    void* pData,
    ULONG* pnBytes) throw();

ATL_DEPRECATED LONG QueryValue(
    DWORD& dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG QueryValue(
    LPTSTR szValue,
    LPCTSTR lpszValueName,
    DWORD* pdwCount);
```  
  
### <a name="parameters"></a>参数  
 `pszValueName`  
 指向以 null 结尾的字符串，包含要查询的值的名称。 如果`pszValueName`为 NULL 或空字符串，""、 方法检索的类型和键的数据的未命名或默认值，如果有的话。  
  
 `pdwType`  
 指向接收，该值指示指定的值中存储的数据类型的代码的变量的指针。 `pdwType`参数可以为 NULL，如果不需要的类型代码。  
  
 `pData`  
 指向接收值的数据缓冲区的指针。 如果不需要数据，此参数可以为 NULL。  
  
 `pnBytes`  
 指向的变量，以字节为单位，缓冲区的指定的大小，指针指向的`pData`参数。 方法返回时，此变量包含复制到的数据的大小*pData。*  
  
 `dwValue`  
 值字段的数值数据。  
  
 `lpszValueName`  
 指定要查询的值字段。  
  
 `szValue`  
 值字段的字符串数据。  
  
 `pdwCount`  
 将字符串数据的大小。 其值最初设置为的大小`szValue`缓冲区。  
  
### <a name="return-value"></a>返回值  
 如果成功，返回 ERROR_SUCCESS;否则，则为非零错误代码在 WINERROR 中定义。H。  
  
### <a name="remarks"></a>备注  
 两个原始版本`QueryValue`不再受支持，标记为**ATL_DEPRECATED**。 如果使用这些窗体，则编译器将发出警告。  
  
 剩余的方法调用 RegQueryValueEx 中。  
  
> [!IMPORTANT]
>  此方法允许调用方指定可能读取数据不能为受信任的任何注册表位置。 此外，此方法使用的 RegQueryValueEx 函数不显式处理字符串，它们是`NULL`终止。 有关中，调用代码应检查这两个条件。  
  
##  <a name="recursedeletekey"></a>CRegKey::RecurseDeleteKey  
 调用此方法以从注册表中删除指定的键并删除任何子项中显式删除。  
  
```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```  
  
### <a name="parameters"></a>参数  
 *lpszKey*  
 指定要删除的键的名称。 此名称必须是项的子项[m_hKey](#m_hkey)。  
  
### <a name="return-value"></a>返回值  
 如果成功，返回 ERROR_SUCCESS;否则，在 WINERROR 中定义了非零错误值。H。  
  
### <a name="remarks"></a>备注  
 如果项具有子项，则必须调用此方法来删除密钥。  
  
##  <a name="setbinaryvalue"></a>CRegKey::SetBinaryValue  
 调用此方法以设置注册表项的二进制值。  
  
```
LONG SetBinaryValue(  
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszValueName`  
 指向包含要设置的值的名称的字符串的指针。 如果具有此名称的值已不存在，则该方法会将它添加密钥。  
  
 `pValue`  
 指向包含要与指定的值名称一起存储的数据缓冲区的指针。  
  
 `nBytes`  
 指定的大小，以字节为单位的信息指向`pValue`参数。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回值是 ERROR_SUCCESS。 如果此方法失败，返回值是在 WINERROR 中定义一个非零错误代码。H。  
  
### <a name="remarks"></a>备注  
 此方法使用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923)值写入注册表。  
  
##  <a name="setdwordvalue"></a>CRegKey::SetDWORDValue  
 调用此方法以设置注册表项 DWORD 值。  
  
```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszValueName`  
 指向包含要设置的值的名称的字符串的指针。 如果具有此名称的值已不存在，则该方法会将它添加密钥。  
  
 `dwValue`  
 将指定的值名称与存储了 DWORD 数据。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回值是 ERROR_SUCCESS。 如果此方法失败，返回值是在 WINERROR 中定义一个非零错误代码。H。  
  
### <a name="remarks"></a>备注  
 此方法使用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923)值写入注册表。  
  
##  <a name="setguidvalue"></a>CRegKey::SetGUIDValue  
 调用此方法以设置注册表项的 GUID 值。  
  
```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszValueName`  
 指向包含要设置的值的名称的字符串的指针。 如果具有此名称的值已不存在，则该方法会将它添加密钥。  
  
 `guidValue`  
 为 GUID 将与指定的值名称存储的引用。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回值是 ERROR_SUCCESS。 如果此方法失败，返回值是在 WINERROR 中定义一个非零错误代码。H。  
  
### <a name="remarks"></a>备注  
 此方法使用`CRegKey::SetStringValue`并将 GUID 转换为字符串使用[StringFromGUID2](http://msdn.microsoft.com/library/windows/desktop/ms683893)。  
  
##  <a name="setkeyvalue"></a>CRegKey::SetKeyValue  
 调用此方法以在指定键指定的值字段中存储数据。  
  
```
LONG SetKeyValue(  
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```  
  
### <a name="parameters"></a>参数  
 `lpszKeyName`  
 指定要创建或打开的键的名称。 此名称必须是项的子项[m_hKey](#m_hkey)。  
  
 `lpszValue`  
 指定要存储的数据。 此参数必须为非 NULL。  
  
 `lpszValueName`  
 指定要设置的值字段。 如果键中不存在具有此名称的值字段，将其添加。  
  
### <a name="return-value"></a>返回值  
 如果成功，返回 ERROR_SUCCESS;否则，则为非零错误代码在 WINERROR 中定义。H。  
  
### <a name="remarks"></a>备注  
 调用此方法以创建或打开`lpszKeyName`密钥并将存储`lpszValue`中的数据`lpszValueName`值字段。  
  
##  <a name="setkeysecurity"></a>CRegKey::SetKeySecurity  
 调用此方法以设置注册表项的安全性。  
  
```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```  
  
### <a name="parameters"></a>参数  
 `si`  
 指定要设置的安全描述符的组件。 该值可以为以下值的组合：  
  
|“值”|含义|  
|-----------|-------------|  
|DACL_SECURITY_INFORMATION|设置密钥的自由访问控制列表 (DACL)。 密钥必须具有 WRITE_DAC 访问权限，或调用进程必须是对象的所有者。|  
|GROUP_SECURITY_INFORMATION|设置密钥的主要组安全标识符 (SID)。 密钥必须具有 WRITE_OWNER 访问权限，或调用进程必须是对象的所有者。|  
|OWNER_SECURITY_INFORMATION|设置密钥的所有者 SID。 密钥必须具有 WRITE_OWNER 访问权限，或者调用进程必须是对象的所有者或具有启用了 SE_TAKE_OWNERSHIP_NAME 特权。|  
|SACL_SECURITY_INFORMATION|设置密钥的系统访问控制列表 (SACL)。 密钥必须 ACCESS_SYSTEM_SECURITY 访问。 获取此访问权限的正确方法是能够进行 SE_SECURITY_NAME[特权](http://msdn.microsoft.com/library/windows/desktop/aa379306)在调用方的当前访问令牌中，打开 ACCESS_SYSTEM_SECURITY 访问的句柄，然后又禁用特权。|  
  
 `psd`  
 指向[SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)结构，它指定要将设置为指定的键的安全属性。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回值是 ERROR_SUCCESS。 如果此方法失败，返回值是在 WINERROR 中定义一个非零错误代码。H。  
  
### <a name="remarks"></a>备注  
 设置密钥的安全属性。 请参阅[RegSetKeySecurity](http://msdn.microsoft.com/library/windows/desktop/aa379314)有关详细信息。  
  
##  <a name="setmultistringvalue"></a>CRegKey::SetMultiStringValue  
 调用此方法以设置的注册表项名的值。  
  
```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszValueName`  
 指向包含要设置的值的名称的字符串的指针。 如果具有此名称的值已不存在，则该方法会将它添加密钥。  
  
 `pszValue`  
 指向名的数据将与指定的值名称存储的指针。 Multistring 上是以 null 结尾的字符串，由两个 null 字符终止的数组。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回值是 ERROR_SUCCESS。 如果此方法失败，返回值是在 WINERROR 中定义一个非零错误代码。H。  
  
### <a name="remarks"></a>备注  
 此方法使用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923)值写入注册表。  
  
##  <a name="setqwordvalue"></a>CRegKey::SetQWORDValue  
 调用此方法以设置注册表项的 QWORD 值。  
  
```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszValueName`  
 指向包含要设置的值的名称的字符串的指针。 如果具有此名称的值已不存在，则该方法会将它添加密钥。  
  
 `qwValue`  
 将指定的值名称与存储 QWORD 数据。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回值是 ERROR_SUCCESS。 如果此方法失败，返回值是在 WINERROR 中定义一个非零错误代码。H。  
  
### <a name="remarks"></a>备注  
 此方法使用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923)值写入注册表。  
  
##  <a name="setstringvalue"></a>CRegKey::SetStringValue  
 调用此方法以设置注册表项的字符串值。  
  
```
LONG SetStringValue(  
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszValueName`  
 指向包含要设置的值的名称的字符串的指针。 如果具有此名称的值已不存在，则该方法会将它添加密钥。  
  
 `pszValue`  
 指向将与指定的值名称存储的字符串数据的指针。  
  
 `dwType`  
 要写入注册表的字符串的类型： REG_SZ （默认值） 或 （对于 multistrings) REG_EXPAND_SZ。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回值是 ERROR_SUCCESS。 如果此方法失败，返回值是在 WINERROR 中定义一个非零错误代码。H。  
  
### <a name="remarks"></a>备注  
 此方法使用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923\(v=vs.85\).aspx)值写入注册表。  
  
##  <a name="setvalue"></a>CRegKey::SetValue  
 调用此方法以将数据存储在指定的值字段[m_hKey](#m_hkey)。 此方法的早期版本不再受支持，标记为**ATL_DEPRECATED**。  
  
```
LONG SetValue(  
    LPCTSTR pszValueName,
    DWORD dwType,
    const void* pValue,
    ULONG nBytes) throw();
    
static LONG WINAPI SetValue(  
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL);

ATL_DEPRECATED LONG SetValue(  
    DWORD dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG SetValue(  
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL,
    bool bMulti = false,
    int nValueLen = -1);
```  
  
### <a name="parameters"></a>参数  
 `pszValueName`  
 指向包含要设置的值的名称的字符串的指针。 如果具有此名称的值已不存在的项，则该方法会将它添加密钥。 如果`pszValueName`为 NULL 或空字符串，""，该方法设置的类型和键的数据的未命名或默认值。  
  
 `dwType`  
 指定指示的数据的指向类型的代码`pValue`参数。  
  
 `pValue`  
 指向包含要与指定的值名称一起存储的数据缓冲区的指针。  
  
 `nBytes`  
 指定的大小，以字节为单位的信息指向`pValue`参数。 如果数据的类型是 REG_SZ、 REG_EXPAND_SZ 或 REG_MULTI_SZ，`nBytes`必须包括终止 null 字符的大小。  
  
 `hKeyParent`  
 开放式密钥句柄。  
  
 `lpszKeyName`  
 指定要创建或打开的密钥的名称。 此名称必须是项的子项`hKeyParent`。  
  
 `lpszValue`  
 指定要存储的数据。 此参数必须为非 NULL。  
  
 `lpszValueName`  
 指定要设置的值字段。 如果键中不存在具有此名称的值字段，将其添加。  
  
 `dwValue`  
 指定要存储的数据。  
  
 `bMulti`  
 如果为 false，指示该字符串采用类型为 REG_SZ。 如果为 true，指示该字符串是类型 REG_MULTI_SZ multistring。  
  
 `nValueLen`  
 如果`bMulti`为 true，`nValueLen`的长度是*lpszValue*以字符为单位的字符串。 如果`bMulti`为 false，值为-1 指示该方法将自动计算长度。  
  
### <a name="return-value"></a>返回值  
 如果成功，返回 ERROR_SUCCESS;否则，则为非零错误代码在 WINERROR 中定义。H。  
  
### <a name="remarks"></a>备注  
 两个原始版本`SetValue`标记为**ATL_DEPRECATED**和应不再使用。 如果使用这些窗体，则编译器将发出警告。  
  
 第三个方法调用[RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923)。  
  
## <a name="see-also"></a>请参阅  
 [DCOM 示例](../../visual-cpp-samples.md)   
 [类概述](../../atl/atl-class-overview.md)
