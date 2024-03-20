# stable-diffusionセットアップ

## stable-diffusion-webui Githubドキュメントページ  

<https://github.com/AUTOMATIC1111/stable-diffusion-webui>

```bash
# ホスト環境セットアップ
sudo apt install wget git python3 python3-venv
```

# stable-diffusion-webuiセットアップ
``` bash
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
cd stable-diffusion-webui
./webui.sh
```

## ウェブUI実行

``` bash
./webui.sh
```

すると次のような実行結果になる。  

```bash
Python 3.10.6 (main, Mar 10 2023, 10:55:28) [GCC 11.3.0]
Commit hash: 22bcc7be428c94e9408f589966c2040187245d81
Installing requirements for Web UI
Launching Web UI with arguments: 
No module 'xformers'. Proceeding without it.
Loading weights [6ce0161689] from /home/ken/stable-diffusion-webui/models/Stable-diffusion/v1-5-pruned-emaonly.safetensors
Creating model from config: /home/ken/stable-diffusion-webui/configs/v1-inference.yaml
LatentDiffusion: Running in eps-prediction mode
DiffusionWrapper has 859.52 M params.
Applying cross attention optimization (Doggettx).
Textual inversion embeddings loaded(0): 
Model loaded in 3.4s (load weights from disk: 0.2s, create model: 0.6s, apply weights to model: 0.6s, apply half(): 0.5s, load VAE: 1.1s, move model to device: 0.3s).
Running on local URL:  http://127.0.0.1:7860
```

ローカルでWebUIサーバーを立てているのなら、そのまま<http://127.0.0.1:7860>をクリックすれば良い。  
もし別のマシンでサーバーが立ち上がっているなら。

```bash
# ウェブUI実行
./webui.sh --listen
```

--listenオプションにより違うマシンから応答を受け付けるようになる。  

```bash
# webui-user.shに追加
export COMMANDLINE_ARGS="--use-cpu all --no-half --no-half-vae --skip-torch-cuda-test"
```
CPUのみで起動させる場合上記の環境変数をwebui-user.shに追加する。

```bash
http://0.0.0.0:7860
自分の環境では下記のIPアドレスへアクセス
http://192.168.11.254:7860
```

以降上記のコマンドを実行すればwebuiが立ち上がる。  

## 拡張プラグイン導入時の注意

拡張プラグインをWebUIから入れる場合listenやshareのオプションと衝突してプラグインをインストールできない場合がある。

```bash
# ウェブUI実行
./webui.sh
```

オプションをなくして実行し、VscodeのRemote Development機能を経由して、リダイレクトアクセスをするとよい。

## モデルの追加

- モデルファイル：  hogehoge.safetensors  
- VAEファイル：    hogehoge.vae.pt  

上記の二種類を「stable-diffusion-webui\models\Stable-diffusion」へ追加する。  
