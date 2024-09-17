# Analyzing-Sazae-san-s-Rock-Paper-Scissors / サザエさんのじゃんけん予測モデル

## 概要
このリポジトリは、サザエさんのじゃんけん結果を予測するモデルの実装です。

## サザエさんじゃんけん予測 with LightGBM 

このリポジトリでは、LightGBMモデルを使用して、翌週のサザエさんのじゃんけんの手を予測するコードを提供しています。過去のじゃんけんの結果を学習データとして、年、月、日、曜日、過去のじゃんけんの手の履歴を特徴量として使用し、LightGBMモデルを学習します。

### 事前準備

1. **Google Colabを使用する場合:**
   - 下記のセルを実行してGoogle Driveをマウントし、実行ディレクトリに移動します。

   ```python
   from google.colab import drive, output
   output.clear()
   drive.mount('/content/drive')
   # データが置いてあるディレクトリのパスを入力して実行
   %cd /content/drive/My Drive/Colab Notebooks/サザエさん_じゃんけん
   ```

2. **ライブラリのインストール:**
   - 必要なライブラリをインストールします。

   ```bash
   pip install optuna-integration[lightgbm] pandas scikit-learn lightgbm 
   ```

3. **データ準備:**
   - じゃんけんの結果を記録したCSVファイル `traindata_サザエさんじゃんけん分析.csv` を用意します。
   - ファイルの形式は下記の通りです。

   ```
   放送回,放送日,出した手,備考
   601,2003年8月24日,パー,
   602,2003年8月31日,チョキ,
   ...
   ```

### 実行方法

1.  **データの読み込み:** 
    - `traindata_サザエさんじゃんけん分析.csv` を読み込みます。

    ```python
    df = pd.read_csv('traindata_サザエさんじゃんけん分析.csv')
    ```

2.  **特徴量エンジニアリング:** 
    - 日付情報から年、月、日、曜日を抽出し、特徴量として追加します。
    - 過去のじゃんけんの手の履歴を特徴量として追加します。

3.  **データ分割:** 
    - データを学習データとテストデータに分割します。

4.  **LightGBMモデルの構築と学習:**
    - LightGBMモデルを構築し、学習データを使って学習します。

5.  **予測:**
    - 学習済みモデルを使って、指定した日付のじゃんけんの手を予測します。
    - 予測結果（グー、チョキ、パーの確率）が出力されます。

### 注意点

-  このコードでは、過去のじゃんけんの結果のみを特徴量として使用しているため、予測精度には限界があります。
- 予測精度を向上させるためには、他の特徴量（例えば、季節、放送内容、国民的行事との関連性など）を追加したり、ハイパーパラメータチューニングを行ったりする必要があるかもしれません。
- このコードはあくまでもサンプルであり、実用的なじゃんけん予測システムを構築するためには、さらなる改良が必要となる可能性があります。
- 情報の正確性について確認はしておりますが，その内容について保証するものではありません
- 本codeの情報を用いた活動は、必ず自らの責任によって行ってください。
- 本codeの内容を使用したことによって発生する不利益等について、筆者および関係者はいかなる責任も負いません。

## ライセンス

このコードはMITライセンスで公開されています。

## 作者
yf591



