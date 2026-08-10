# Windows環境のセットアップ

このページでは、Windows上でToyLibの開発環境を構築する手順を説明します。

## 必要なソフトウェア

以下のソフトウェアをインストールしてください。

| ソフトウェア | 用途 |
|--------------|------|
| Visual Studio 2026 | C++コンパイラ・デバッガ |
| CMake | ビルドシステム |
| Git | ソースコード管理 |
| vcpkg | ライブラリ管理 |
| Visual Studio Code（任意） | 軽量エディタ |

---

# Visual Studio 2026

Microsoft公式サイトからインストールします。

https://visualstudio.microsoft.com/ja/downloads/

インストール時は以下のワークロードのみ選択すれば十分です。

- **C++によるデスクトップ開発**

---

# CMake

公式サイトから最新版をインストールします。

https://cmake.org/download/

---

# Git

公式サイトからGit for Windowsをインストールします。

https://gitforwindows.org/

---

# vcpkg

任意の場所へインストールできますが、**`C:\tools`** に配置することを推奨します。

```powershell
cd C:\
mkdir tools
cd tools

git clone https://github.com/microsoft/vcpkg

cd vcpkg

.\bootstrap-vcpkg.bat
```

## vcpkgの更新

```powershell
cd C:\tools\vcpkg

git pull

.\vcpkg.exe upgrade --no-dry-run
```

---

# Visual Studio Code（任意）

Visual Studio Codeを利用する場合は、以下からインストールしてください。

https://code.visualstudio.com/

---

# 必要ライブラリのインストール

ToyLibではvcpkgを利用してライブラリをインストールします。

```powershell
cd C:\tools\vcpkg

.\vcpkg.exe install ^
    sdl3 [vulkan]^
    sdl3-image[jpeg,png] ^
    sdl3-ttf ^
    assimp ^
    openal-soft ^
    vulkan
```

> OpenGLはWindows SDKに含まれているため、追加インストールは不要です。

---

# インストール確認

以下のコマンドでライブラリが正常にインストールされていることを確認できます。

```powershell
.\vcpkg.exe list
```

---

# 次へ

環境構築が完了したら、ToyLibのソースコードを取得し、CMakeでプロジェクトを生成します。