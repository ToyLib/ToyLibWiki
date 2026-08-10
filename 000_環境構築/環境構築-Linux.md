# Linux環境のセットアップ


このページでは、Linux上でToyLibの開発環境を構築する手順を説明します。

現在は **Ubuntu系ディストリビューション（Ubuntu / Pop!_OS / Linux Mint など）** で動作確認を行っています。

---

# 必要なソフトウェア

以下のソフトウェアをインストールしてください。

| ソフトウェア | 用途 |
|--------------|------|
| GCC / G++ | C++コンパイラ |
| GDB | デバッガ |
| CMake | ビルドシステム |
| Git | ソースコード管理 |
| Visual Studio Code（任意） | エディタ |

---

# パッケージの更新

まず、システムを最新の状態に更新します。

```bash
sudo apt update
sudo apt upgrade
```

---

# 開発ツールのインストール

必要な開発ツールをインストールします。

```bash
sudo apt install \
    build-essential \
    cmake \
    git \
    gdb \
    pkg-config
```

インストール確認

```bash
g++ --version
cmake --version
```

---

# 必要ライブラリのインストール

ToyLibで使用するライブラリをインストールします。

```bash
sudo apt install \
    libsdl3-dev \
    libsdl3-image-dev \
    libsdl3-ttf-dev \
    libassimp-dev \
    libopenal-dev \
    libgl1-dev \
    libvulkan-dev
```

各ライブラリは `pkg-config` または `find_package()` により自動的に検出されます。

---

# Visual Studio Code（任意）

Visual Studio Codeを利用する場合は、Microsoft公式サイトまたはSnapからインストールできます。

```bash
sudo snap install code --classic
```

以下の拡張機能をインストールすることを推奨します。

- C/C++
- CMake Tools
- GitLens（任意）

---

# ビルド

ToyLibのルートディレクトリで以下を実行します。

```bash
mkdir build
cd build

cmake ..

cmake --build . -j
```

または

```bash
cmake -S . -B build

cmake --build build -j
```

---

# 実行

ビルドが完了したら実行します。

```bash
./GameApp
```

（生成される実行ファイル名はプロジェクトによって異なります。）

---

# 動作確認

以下のコマンドでライブラリが認識されていることを確認できます。

```bash
pkg-config --modversion sdl3
pkg-config --modversion assimp
pkg-config --modversion fmt
```

Vulkanの動作確認

```bash
vulkaninfo
```

OpenGLの確認

```bash
glxinfo | grep "OpenGL"
```

> `vulkaninfo` および `glxinfo` がインストールされていない場合は、それぞれ `vulkan-tools`、`mesa-utils` パッケージをインストールしてください。

---

# 対応ディストリビューション

動作確認済み

- Ubuntu
- Pop!_OS
- Linux Mint

動作実績あり（要ビルド確認）

- Debian
- openSUSE
- Fedora
- Arch Linux
- Manjaro

CMakeを採用しているため、必要なライブラリがインストールされていれば、多くのLinuxディストリビューションでビルドできます。

---

# 次へ

環境構築が完了したら、最初のゲームを作成してToyLibの基本的な使い方を学びましょう。