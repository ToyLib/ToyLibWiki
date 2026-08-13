# macOS環境のセットアップ

このページでは、macOS上でToyLibの開発環境を構築する手順を説明します。

## 必要なソフトウェア

以下のソフトウェアをインストールしてください。

| ソフトウェア | 用途 |
|--------------|------|
| Xcode | C++コンパイラ・SDK |
| Homebrew | パッケージ管理 |
| CMake | ビルドシステム |
| Git | ソースコード管理 |
| Visual Studio Code（任意） | 軽量エディタ |

---

# Xcode

Mac App StoreからXcodeをインストールします。

インストール後、以下のコマンドを実行してコマンドラインツールを有効にします。

```bash
xcode-select --install
```

ライセンスに同意していない場合は、以下を実行してください。

```bash
sudo xcodebuild -license accept
```

---

# Homebrew

Homebrewをインストールします。

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

インストール後、最新版へ更新します。

```bash
brew update
brew upgrade
```

---

# Git

通常はXcode Command Line Toolsと一緒にインストールされます。

確認するには以下を実行します。

```bash
git --version
```

---

# CMake

Homebrewからインストールします。

```bash
brew install cmake
```

確認

```bash
cmake --version
```

---

# 必要ライブラリのインストール

ToyLibで使用するライブラリをインストールします。

```bash
brew install \
    sdl3 \
    sdl3_image \
    sdl3_ttf \
    assimp \
    openal-soft \
    shaderc \
    vulkan-loader \
    vulkan-headers \
    molten-vk
```

> OpenGL.frameworkはmacOSに標準搭載されているため、追加インストールは不要です。

---

# Visual Studio Code（任意）

Visual Studio Codeを利用する場合は、以下からインストールしてください。

https://code.visualstudio.com/

C/C++拡張機能およびCMake Tools拡張機能をインストールすることを推奨します。

---

# インストール確認

以下のコマンドでライブラリがインストールされていることを確認できます。

```bash
brew list
```

また、CMakeから各ライブラリが認識されることを確認してください。

```bash
cmake --version
clang++ --version
```

---

# ビルド

ToyLibのルートディレクトリで以下を実行します。

```bash
mkdir build
cd build

cmake ..

cmake --build . -j
```


---

# 動作確認

ビルドが成功したら実行します。

```bash
./GameApp
```

（生成される実行ファイル名はプロジェクトによって異なります。）

---

# 次へ

環境構築が完了したら、最初のゲームを作成してToyLibの基本的な使い方を学びましょう。