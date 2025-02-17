---
title: dotnet コマンド
description: dotnet コマンド (.NET Core CLI ツールの一般的なドライバー) とその使用法について説明します。
ms.date: 06/04/2018
ms.openlocfilehash: 2134bf8ed66157619499b027f01d39e03e84411f
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859547"
---
# <a name="dotnet-command"></a>dotnet コマンド

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet` - .NET のソース コードとバイナリを管理するためのツール。

## <a name="synopsis"></a>構文

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```

---

## <a name="description"></a>説明

`dotnet` は .NET のソース コードとバイナリを管理するためのツールです。 [`dotnet build`](dotnet-build.md) や [`dotnet run`](dotnet-run.md) のような特定のタスクを実行するコマンドを公開します。 各コマンドによって、それ自体の引数が定義されます。 各コマンドの後ろに `--help` と入力すると、短いヘルプ ドキュメントにアクセスできます。

`dotnet` は、`dotnet myapp.dll` など、アプリケーション DLL を指定することで、アプリケーションを実行するために使用できます。 展開オプションについては、「[.NET Core アプリケーションの展開](../deploying/index.md)」を参照してください。

## <a name="options"></a>オプション

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--additional-deps <PATH>`

追加の *deps.json* ファイルへのパスです。

`--additionalprobingpath <PATH>`

プローブ ポリシーとプローブするアセンブリを含むパスです。

`-d|--diagnostics`

診断出力を有効にします。

`--fx-version <VERSION>`

アプリケーションを実行するために使用する .NET Core ランタイムのバージョン。

`-h|--help`

`dotnet build --help` など、特定のコマンドのドキュメントを出力します。 `dotnet --help` では、使用できるコマンドの一覧が出力されます。

`--info`

現在のオペレーティング システムや .NET Core バージョンのコミット SHA など、.NET Core インストールとコンピューター環境に関する詳細を出力します。

`--list-runtimes`

インストールされている .NET Core ランタイムを表示します。

`--list-sdks`

インストールされている .NET Core SDK を表示します。

`--roll-forward-on-no-candidate-fx <N>`

必要な共有フレームワークが利用できない場合の動作を定義します。 `N` には以下があります。
* `0` - マイナー バージョンのロールフォワードでも無効にします。
* `1` - マイナー バージョンはロール フォワードしますが、メジャー バージョンはしません。 これが既定の動作です。
* `2` - マイナー バージョンとメジャー バージョンをロール フォワードします。

 詳細については、「[Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward)」(ロールフォワード) を参照してください。

`-v|--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。 一部のコマンドではサポートされていません。このオプションが使用可能かどうかを判断するには、対象のコマンドのページを参照してください。

`--version`

使用中の .NET Core SDK のバージョンを印刷します。

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--additional-deps <PATH>`

追加の *deps.json* ファイルへのパスです。

`--additionalprobingpath <PATH>`

プローブ ポリシーとプローブするアセンブリを含むパスです。

`-d|--diagnostics`

診断出力を有効にします。

`--fx-version <VERSION>`

アプリケーションを実行するために使用する .NET Core ランタイムのバージョン。

`-h|--help`

`dotnet build --help` など、特定のコマンドのドキュメントを出力します。 `dotnet --help` では、使用できるコマンドの一覧が出力されます。

`--info`

現在のオペレーティング システムや .NET Core バージョンのコミット SHA など、.NET Core インストールとコンピューター環境に関する詳細を出力します。

`--roll-forward-on-no-candidate-fx`

 `0` に設定されている場合、マイナー バージョンのロールフォワードを無効にします。 詳細については、「[Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward)」(ロールフォワード) を参照してください。

`-v|--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。 一部のコマンドではサポートされていません。このオプションが使用可能かどうかを判断するには、対象のコマンドのページを参照してください。

`--version`

使用中の .NET Core SDK のバージョンを印刷します。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

プローブ ポリシーとプローブするアセンブリを含むパスです。

`-d|--diagnostics`

診断出力を有効にします。

`--fx-version <VERSION>`

アプリケーションを実行するために使用する .NET Core ランタイムのバージョン。

`-h|--help`

`dotnet build --help` など、特定のコマンドのドキュメントを出力します。 `dotnet --help` では、使用できるコマンドの一覧が出力されます。

`--info`

現在のオペレーティング システムや .NET Core バージョンのコミット SHA など、.NET Core インストールとコンピューター環境に関する詳細を出力します。

`-v|--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。 一部のコマンドではサポートされていません。このオプションが使用可能かどうかを判断するには、対象のコマンドのページを参照してください。

`--version`

使用中の .NET Core SDK のバージョンを印刷します。

---

## <a name="dotnet-commands"></a>dotnet コマンド

### <a name="general"></a>全般

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

| コマンド                                       | 関数                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | .NET Core アプリケーションをビルドします。                                     |
| [dotnet build-server](dotnet-build-server.md) | ビルドによって起動されたサーバーとやり取りします。                          |
| [dotnet clean](dotnet-clean.md)               | クリーン ビルド出力です。                                                |
| [dotnet help](dotnet-help.md)                 | コマンドのより詳細なドキュメントをオンラインで表示します。           |
| [dotnet migrate](dotnet-migrate.md)           | 有効な Preview 2 プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。  |
| [dotnet msbuild](dotnet-msbuild.md)           | MSBuild コマンド ラインへのアクセスを提供します。                        |
| [dotnet new](dotnet-new.md)                   | 指定されたテンプレートの C# または F# プロジェクトを初期化します。                |
| [dotnet pack](dotnet-pack.md)                 | コードの NuGet パッケージを作成します。                               |
| [dotnet publish](dotnet-publish.md)           | .NET Framework に依存するアプリケーションまたは自己完結型アプリケーションを発行します。 |
| [dotnet restore](dotnet-restore.md)           | 指定されたアプリケーションの依存関係を復元します。                  |
| [dotnet run](dotnet-run.md)                   | ソースからアプリケーションを実行します。                                   |
| [dotnet sln](dotnet-sln.md)                   | ソリューション ファイルのプロジェクトを追加、削除、一覧表示するオプション。       |
| [dotnet store](dotnet-store.md)               | ランタイム パッケージ ストアにアセンブリを格納します。                     |
| [dotnet test](dotnet-test.md)                 | テスト ランナーを使用してテストを実行します。                                     |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

| コマンド                             | 関数                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | .NET Core アプリケーションをビルドします。                                     |
| [dotnet clean](dotnet-clean.md)     | クリーン ビルド出力です。                                              |
| [dotnet help](dotnet-help.md)       | コマンドのより詳細なドキュメントをオンラインで表示します。           |
| [dotnet migrate](dotnet-migrate.md) | 有効な Preview 2 プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。  |
| [dotnet msbuild](dotnet-msbuild.md) | MSBuild コマンド ラインへのアクセスを提供します。                        |
| [dotnet new](dotnet-new.md)         | 指定されたテンプレートの C# または F# プロジェクトを初期化します。                |
| [dotnet pack](dotnet-pack.md)       | コードの NuGet パッケージを作成します。                               |
| [dotnet publish](dotnet-publish.md) | .NET Framework に依存するアプリケーションまたは自己完結型アプリケーションを発行します。 |
| [dotnet restore](dotnet-restore.md) | 指定されたアプリケーションの依存関係を復元します。                  |
| [dotnet run](dotnet-run.md)         | ソースからアプリケーションを実行します。                                   |
| [dotnet sln](dotnet-sln.md)         | ソリューション ファイルのプロジェクトを追加、削除、一覧表示するオプション。       |
| [dotnet store](dotnet-store.md)     | ランタイム パッケージ ストアにアセンブリを格納します。                     |
| [dotnet test](dotnet-test.md)       | テスト ランナーを使用してテストを実行します。                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

| コマンド                             | 関数                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | .NET Core アプリケーションをビルドします。                                     |
| [dotnet clean](dotnet-clean.md)     | クリーン ビルド出力です。                                              |
| [dotnet migrate](dotnet-migrate.md) | 有効な Preview 2 プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。  |
| [dotnet msbuild](dotnet-msbuild.md) | MSBuild コマンド ラインへのアクセスを提供します。                        |
| [dotnet new](dotnet-new.md)         | 指定されたテンプレートの C# または F# プロジェクトを初期化します。                |
| [dotnet pack](dotnet-pack.md)       | コードの NuGet パッケージを作成します。                               |
| [dotnet publish](dotnet-publish.md) | .NET Framework に依存するアプリケーションまたは自己完結型アプリケーションを発行します。 |
| [dotnet restore](dotnet-restore.md) | 指定されたアプリケーションの依存関係を復元します。                  |
| [dotnet run](dotnet-run.md)         | ソースからアプリケーションを実行します。                                   |
| [dotnet sln](dotnet-sln.md)         | ソリューション ファイルのプロジェクトを追加、削除、一覧表示するオプション。       |
| [dotnet test](dotnet-test.md)       | テスト ランナーを使用してテストを実行します。                                     |

---

### <a name="project-references"></a>プロジェクト参照

コマンド | 関数
--- | ---
[dotnet add reference](dotnet-add-reference.md) | プロジェクト参照を追加します。
[dotnet list reference](dotnet-list-reference.md) | プロジェクト参照をリストします。
[dotnet remove reference](dotnet-remove-reference.md) | プロジェクト参照を削除します。

### <a name="nuget-packages"></a>NuGet パッケージ

コマンド | 関数
--- | ---
[dotnet add package](dotnet-add-package.md) | NuGet パッケージを追加します。
[dotnet remove package](dotnet-remove-package.md) | NuGet パッケージを削除します。

### <a name="nuget-commands"></a>NuGet コマンド

コマンド | 関数
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | サーバーからパッケージを削除または一覧から削除します。
[dotnet nuget locals](dotnet-nuget-locals.md) | HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。
[dotnet nuget push](dotnet-nuget-push.md) | パッケージをサーバーにプッシュして発行します。

### <a name="global-tools-commands"></a>グローバル ツール コマンド

[.NET Core グローバル ツール](global-tools.md)は .NET Core SDK 2.1.300 以降で使用できます。

コマンド | 関数
--- | ---
[dotnet tool install](dotnet-tool-install.md) | グローバル ツールをマシンにインストールします。
[dotnet tool list](dotnet-tool-list.md) | マシン上の既定のディレクトリまたは指定したパスに現在インストールされているすべてのグローバル ツールを一覧表示します。
[dotnet tool uninstall](dotnet-tool-uninstall.md) | グローバル ツールをマシンからアンインストールします。
[dotnet tool update](dotnet-tool-update.md) | マシン上のグローバル ツールを更新します。

### <a name="additional-tools"></a>その他のツール

.NET Core SDK 2.1.300 以降では、`DotnetCliToolReference` を使用してプロジェクト単位でのみ入手可能であった複数のツールを .NET Core SDK の一部として入手できるようになりました。 これらのツールを次の表に示します。

| ツール                                              | 関数                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | 開発証明書を作成および管理します。                |
| [ef](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core コマンドライン ツールです。                    |
| sql-cache                                         | SQL Server キャッシュ コマンドライン ツールです。                         |
| [user-secrets](/aspnet/core/security/app-secrets) | 開発ユーザーのシークレットを管理します。                            |
| [watch](/aspnet/core/tutorials/dotnet-watch)      | ファイルが変化するとコマンドを実行するファイル ウォッチャーを起動します。 |

各ツールの詳細については、`dotnet <tool-name> --help` と入力してください。

## <a name="examples"></a>使用例

新しい .NET Core コンソール アプリケーションを作成します。

`dotnet new console`

指定されたアプリケーションの依存関係を復元します。

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

指定されたディレクトリにプロジェクトとその依存関係をビルドします。

`dotnet build`

`myapp.dll` など、アプリケーション DLL を実行します。

`dotnet myapp.dll`

## <a name="environment-variables"></a>環境変数

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`DOTNET_PACKAGES`

グローバル パッケージ フォルダー。 設定されていない場合は、既定で `~/.nuget/packages` (Unix の場合) または `%userprofile%\.nuget\packages` (Windows の場合) になります。

`DOTNET_SERVICING`

ランタイムの読み込み時に共有ホストで使用するサービス インデックスの場所を指定します。

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core ツールの使用に関するデータを収集し、Microsoft に送信するかどうかを指定します。 `true` に設定するとテレメトリ機能が無効になります (指定できる値は `true`、`1`、または `yes` です)。 それ以外の場合は `false` に設定します。この場合、テレメトリ機能が有効になります (指定できる値は `false`、`0`、または `no` です)。 設定されていない場合、既定で `false` になり、テレメトリ機能はアクティブになります。

`DOTNET_MULTILEVEL_LOOKUP`

.NET Core ランタイム、共有フレームワーク、または SDK がグローバルな場所から解決されるかどうかを指定します。 設定されていない場合は、既定で `true` になります。 `false` に設定すると、グローバルな場所から解決されず、.NET Core インストールが分離されます (値 `0` または `false` が受け入れられます)。 複数レベルのルックアップの詳細については、「[Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md)」 (複数レベルの SharedFX ルックアップ) を参照してください。

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

`0` に設定されている場合、マイナー バージョンのロールフォワードを無効にします。 詳細については、「[Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward)」(ロールフォワード) を参照してください。

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`DOTNET_PACKAGES`

プライマリ パッケージのキャッシュです。 設定されていない場合は、既定で `$HOME/.nuget/packages` (Unix の場合) または `%userprofile%\.nuget\packages` (Windows の場合) になります。

`DOTNET_SERVICING`

ランタイムの読み込み時に共有ホストで使用するサービス インデックスの場所を指定します。

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core ツールの使用に関するデータを収集し、Microsoft に送信するかどうかを指定します。 `true` に設定するとテレメトリ機能が無効になります (指定できる値は `true`、`1`、または `yes` です)。 それ以外の場合は `false` に設定します。この場合、テレメトリ機能が有効になります (指定できる値は `false`、`0`、または `no` です)。 設定されていない場合、既定で `false` になり、テレメトリ機能はアクティブになります。

`DOTNET_MULTILEVEL_LOOKUP`

.NET Core ランタイム、共有フレームワーク、または SDK がグローバルな場所から解決されるかどうかを指定します。 設定されていない場合は、既定で `true` になります。 `false` に設定すると、グローバルな場所から解決されず、.NET Core インストールが分離されます (値 `0` または `false` が受け入れられます)。 複数レベルのルックアップの詳細については、「[Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md)」 (複数レベルの SharedFX ルックアップ) を参照してください。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`DOTNET_PACKAGES`

プライマリ パッケージのキャッシュです。 設定されていない場合は、既定で `$HOME/.nuget/packages` (Unix の場合) または `%userprofile%\.nuget\packages` (Windows の場合) になります。

`DOTNET_SERVICING`

ランタイムの読み込み時に共有ホストで使用するサービス インデックスの場所を指定します。

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core ツールの使用に関するデータを収集し、Microsoft に送信するかどうかを指定します。 `true` に設定するとテレメトリ機能が無効になります (指定できる値は `true`、`1`、または `yes` です)。 それ以外の場合は `false` に設定します。この場合、テレメトリ機能が有効になります (指定できる値は `false`、`0`、または `no` です)。 設定されていない場合、既定で `false` になり、テレメトリ機能はアクティブになります。

---
