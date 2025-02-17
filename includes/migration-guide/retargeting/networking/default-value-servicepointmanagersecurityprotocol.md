---
ms.openlocfilehash: 7b86365e841defb78558b10fa171a88031b4820e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859177"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>ServicePointManager.SecurityProtocol の既定値は SecurityProtocolType.System.Default

|   |   |
|---|---|
|説明|.NET Framework 4.7 を対象とするアプリから、<xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> プロパティの既定値が <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType> になります。 この変更により、SslStream をベースとする NET Framework ネットワーク API (FTP、HTTPS、SMTP など) は、.NET Framework によって定義されるハード コーディングされた値を使用する代わりに、オペレーティング システムから既定のセキュリティ プロトコルを継承できます。 既定値はオペレーティング システムと、システム管理者が実行するカスタム構成によって異なります。 Windows オペレーティング システムの各バージョンにおける既定の SChannel プロトコルについては、「[Protocols in TLS/SSL (Schannel SSP)](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-)」 (TLS/SSL のプロトコル (Schannel SSP)) を参照してください。</p>以前のバージョンの .NET Framework を対象とするアプリケーションの場合、<xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> プロパティの既定値は、対象となる .NET Framework のバージョンに依存します。 詳細については、「.NET Framework 4.5.2 から 4.6 への移行に関する変更の再ターゲット」の「[ネットワーキング](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking)」セクションを参照してください。|
|提案される解決策|この変更は、.NET Framework 4.7 以降のバージョンを対象とするアプリケーションに影響します。 </br>システム初期設定に依存せず、はっきり定められたプロトコルを使用する場合、<xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> プロパティの値を明示的に設定できます。</br>この変更が望ましくない場合、アプリケーション構成ファイルの [<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに構成設定を追加して、無効にすることができます。 次の例では、<code>&lt;runtime&gt;</code> セクションと無効に切り替える処理 <code>Switch.System.Net.DontEnableSystemDefaultTlsVersions</code> の両方を確認できます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSystemDefaultTlsVersions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|マイナー|
|Version|4.7|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType></li></ul>|

