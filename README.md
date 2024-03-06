# 高知大学　R5年度　DS/DXセミナー　
## 統計基礎、bulk RNA-Seq解析ハンズオントレーニング

## 日時
2024年3月5日(火) 10:30−18:00\
2024年3月6日(水) 10:30−18:00

## 場所
高知大学　物部キャンパス　農場棟１階講義室

## 講義の概要と学習目標
公共データベースに格納されているbulk RNA-Seqデータを取得し、発現変動遺伝子（Differentially expressed genes; DEGs）の検出、DEGsを用いた各種エンリッチメント解析を行う。

## 用意するもの
インターネット接続可能なコンピュータ１台（OS: Windows 11, or macOS）

## スケジュール
#### １日目
10:30-12:00　統計学基礎\
13:00-18:00　bulk RNA-Seq解析ハンズオントレーニング事前説明
#### ２日目
10:30-12:00　bulk RNA-Seq解析ハンズオントレーニング\
13:00-18:00　bulk RNA-Seq解析ハンズオントレーニング

## 統計基礎講義資料
下記よりダウンロード下さい。\
[https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/blob/main/Kochi_DSDX_Seminar_20240305_compressed.pdf](https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/blob/main/Kochi_DSDX_Seminar_20240305_compressed.pdf)

# bulk RNA-Seq解析ハンズオントレーニング
## 目次
### [Windows 11](https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/blob/main/README.md#windows-11-1)
### [macOS](https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/blob/main/README.md#macos-1)
### [使用するデータ](https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/blob/main/README.md#2-%E4%BD%BF%E7%94%A8%E3%83%87%E3%83%BC%E3%82%BF)(これ以降は一部を除いてWindows 11, macOS間共通)

## 1. 環境構築
# Windows 11
Windows 11でUnix環境を構築するため、Cygwinを使用します。
#### - Cygwinのインストール
1. [https://www.cygwin.com/install.html](https://www.cygwin.com/install.html)にアクセス
2. 「setup-x86_64.exe」をクリックし、setup-x86_64.exeをダウンロード
3. ダウンロードディレクトリに保存された「setup-x86_64.exe」をダブルクリック
4. 「はい」をクリック

<img width="458" alt="スクリーンショット 2024-02-28 10 24 15" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/4f37a84c-1981-4e31-8b1c-4805ece4ff05">

5. 「次へ」をクリック

<img width="491" alt="スクリーンショット 2024-02-28 10 24 26" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/09d00ba9-f4db-46ed-ac4e-abe2e589049a">

6. 下記を選択し、「次へ」をクリック

<img width="491" alt="スクリーンショット 2024-02-28 10 24 59" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/69005d2c-d56f-467c-afb3-63afc9d8b1ac">

7. 下記のように選択し、「次へ」をクリック

<img width="491" alt="スクリーンショット 2024-02-28 10 25 08" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/7576a11b-3215-482a-a51c-d2b7dbce6f67">

8. 下記のように選択し、「次へ」をクリック。ただし、画面上の```xxx```は任意のユーザー名に変更すること。

<img width="492" alt="スクリーンショット 2024-02-28 10 26 05" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/e168c8b3-7890-47ff-8451-54259a7ceba0">

9. 下記のように選択し、「次へ」をクリック

<img width="492" alt="スクリーンショット 2024-02-28 10 26 21" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/fb307fb7-54af-476b-b71c-3169d0308cc8">

10. 日本のミラーサーバーを選択し、「次へ」をクリック

<img width="489" alt="スクリーンショット 2024-02-28 11 03 46" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/5b49fc79-2bbc-447c-b856-0afda5423a6d">

11. Cygwinはデフォルトでは、必要最低限のパッケージしかインストールしてくれません。解析に必要なパッケージを個別に指定してインストールします。指定するパッケージは下記の８つです。該当するパッケージの```Default```をプルダウンで```Install```に変更します。
- Admin
- Archive
- Base
- Devel
- Editors
- Graphics
- Libs
- Perl

<img width="1440" alt="スクリーンショット 2024-02-28 11 14 00" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/f5412eb3-35a2-43bf-bfe3-24bcd52b2c1d">

12. 下記のように選択し、「次へ」をクリック

<img width="487" alt="スクリーンショット 2024-02-28 11 16 57" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/d5697f6f-d667-43fb-aa48-868c5546acb5">

13. 「次へ」をクリック

<img width="489" alt="スクリーンショット 2024-02-28 11 17 09" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/ea1edca7-4541-44be-9eea-c67709d67424">

14. ダウンロードが開始されます。

<img width="491" alt="スクリーンショット 2024-02-28 11 18 18" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/85d79fff-bac2-4263-9329-cf1af7b2eb62">

15. 下記のようにダウンロードが完了しなかったパッケージが表示されることがありますので、ダウンロードが進んでいるか定期的にチェックして下さい。表示された場合は、「Retry」を選択し、再度インストールを開始します。

<img width="470" alt="スクリーンショット 2024-02-28 12 33 28" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/0f4ef331-f474-4cda-8e69-28731e774a13">

16. 再びダウンロードが開始されます。合計で２、３時間かかります。

<img width="489" alt="スクリーンショット 2024-02-28 12 47 35" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/84e3566c-af91-48d9-9ad7-f89e62a110a7">

17. 完了をクリック。
<img width="491" alt="スクリーンショット 2024-02-28 13 06 56" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/ed88ba1f-1aae-418a-a8cd-ee331115c4f1">

#### - 作業ディレクトリの作成
1. Cygwinを起動します。
2. ホームディレクトリ下に作業ディレクトリを作成するため、下記のコマンドを実行
```
cd
mkdir bulksem
```

#### - NCBI SRA Toolkitのインストール
1. 下記のコマンドを実行
```
cd ~/bulksem
curl -OL https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/3.0.10/sratoolkit.3.0.10-win64.zip
unzip ./sratoolkit.3.0.10-win64.zip
```
2. 今回使用するsratoolkitのプログラムは、```prefetch```と```fastq-dump```の２つです。\
解凍後、下記コマンドを実行します。
```
./sratoolkit.3.0.10-win64/bin/prefetch -V
```
```
./sratoolkit.3.0.10-win64/bin/fastq-dump -V
```
以下のメッセージがそれぞれ表示されれば、NCBI SRA Toolkitのインストールは完了です。

<img width="516" alt="スクリーンショット 2024-02-28 16 49 34" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/82c3de4e-6cfd-4a1c-ba2a-022fea9acffe">

<img width="535" alt="スクリーンショット 2024-02-28 16 49 49" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/4c9ff30d-5c1d-4c14-9539-6676a0c5a86f">

#### - FastQCのインストール
1. 下記コマンドを実行
```
cd ~/bulksem
curl -OL https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.12.1.zip
unzip fastqc_v0.12.1.zip
cd ./FastQC
./fastqc -v
```
2. ```FastQC v0.12.1```のメッセージが表示されれば、FastQCのインストールのインストール完了

**#2024年3月6日更新**
Windowsユーザーは下記サイトの```FastQC v0.11.9 (Win/Linux zip file) ```をクリックして、ファイルをダウンロードして下さい。\
[https://kb.10xgenomics.com/hc/en-us/articles/360048465032-When-to-run-FastQC](https://kb.10xgenomics.com/hc/en-us/articles/360048465032-When-to-run-FastQC)\
ダウンロードしたファイルは```bulksem```ディレクトリには移動させず、ダウンロードディレクト下に置いたまま解凍し、```run_fastqc.bat```をダブルクリックして実行して下さい。アプリケーションが起動されます。

#### - javaのインストール
1. Windowsにjavaがインストールされていない場合は、[https://www.java.com/ja/download/](https://www.java.com/ja/download/)にアクセスし、```jre-8u401-windows-x64.exe```をダウンロードする（2024年2月28日時点）。
2. ダウンロードディレクトリに保存された「jre-8u401-windows-x64.exe」をダブルクリック
3. 「はい」をクリック

<img width="457" alt="スクリーンショット 2024-02-28 13 10 18" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/fbba5ae2-01c9-46ab-8ae9-25bffd708a8d">

4. 「インストール」をクリック

<img width="702" alt="スクリーンショット 2024-02-28 13 11 15" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/35a4ee42-679b-4800-82e9-8ad993bf23ab">

5. インストール中

<img width="701" alt="スクリーンショット 2024-02-28 13 11 22" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/698f0543-af61-4b24-a251-5373f1cf87f7">

6. 「閉じる」をクリック

<img width="702" alt="スクリーンショット 2024-02-28 13 11 39" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/5d12a527-4d93-49d7-93b0-91f8ab73668f">

#### - Trimmomaticのインストール
1. 下記コマンドを実行
```
cd ~/bulksem
curl -OL http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/Trimmomatic-0.39.zip
unzip Trimmomatic-0.39.zip
java -jar ./Trimmomatic-0.39/trimmomatic-0.39.jar -version
```
2. 以下のメッセージが表示されれば、Trimmomaticのインストール完了

<img width="424" alt="スクリーンショット 2024-02-29 21 45 04" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/7e115832-705f-45d2-b392-2d76825b3145">

#### - HISAT2のインストールとコンパイル
1. [https://cloud.biohpc.swmed.edu/index.php/s/fE9QCsX3NH4QwBi/download](https://cloud.biohpc.swmed.edu/index.php/s/fE9QCsX3NH4QwBi/download)にアクセスして、```hisat2-2.2.1-source.zip```をダウンロードします。
2. ```ダウンロード```ディレクトリに保存された```hisat2-2.2.1-source.zip```を、作業ディレクトリである```C:\cygwin64\home\xxx\bulksem```にドラッグ・アンド・ドロップでして下さい（xxxは各端末で設定されている任意のユーザー名です。）
3. 下記コマンドを実行
```
cd　~/bulksem
unzip ./hisat2-2.2.1-source.zip
cd ./hisat2-2.2.1
make
```
```make```でのコンパイルには30分ほどかかります。

4. コンパイル後、下記コマンドを実行します。
```
./hisat2 -h
```
以下のメッセージが表示されれば、```hisat2```のインストール・コンパイルは完了です。\
（最初の数行のみ表示させています。）

<img width="642" alt="スクリーンショット 2024-02-28 16 16 23" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/5324d95d-74e2-41f5-97d3-8183613eaa60">

5. コンパイル後、下記コマンドを実行します。
```
./hisat2-build -h
```
以下のメッセージが表示されれば、```hisat2-build```のインストール・コンパイルは完了です。\
（最初の数行のみ表示させています。）

<img width="676" alt="スクリーンショット 2024-02-29 21 32 28" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/e65c3579-5ace-4276-9b72-b2c915e7e62c">

#### - featureCountsのインストール
1. [https://sourceforge.net/projects/subread/files/subread-2.0.6/subread-2.0.6-Windows-x86_64.tar.gz/download](https://sourceforge.net/projects/subread/files/subread-2.0.6/subread-2.0.6-Windows-x86_64.tar.gz/download)にアクセスし、```subread-2.0.6-Windows-x86_64.tar.gz```をダウンロードします。
2. ```ダウンロード```ディレクトリに保存された```subread-2.0.6-Windows-x86_64.tar.gz```を、作業ディレクトリである```C:\cygwin64\home\xxx\bulksem```にドラッグ・アンド・ドロップでして下さい（xxxは各端末で設定されている任意のユーザー名です。）
3. 下記コマンドを実行
```
cd ~/bulksem
tar -zxvf ./subread-2.0.6-Windows-x86_64.tar.gz
```
解凍後、下記コマンドを実行
```
./subread-2.0.6-Windows-x86_64/bin/featureCounts -v
```
以下のメッセージが表示されれば、featureCountsのインストール・コンパイルは完了です。

<img width="379" alt="スクリーンショット 2024-02-28 16 38 29" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/abbf2fb5-db94-45bc-b0ea-b2bf5f80afa4">

#### - PATHの追加
絶対PATHの入力を不要にするため、コマンドごとにPATHを追加しておきます。\
下記のコマンドを実行します。（ただし、xxxは各端末で設定されている任意のユーザー名に変更して下さい。）
```
export PATH=/home/xxx/bulksem/sratoolkit.3.0.10-win64/bin:/home/xxx/bulksem/FastQC:/home/xxx/bulksem/hisat2-2.2.1:/home/xxx/bulksem/subread-2.0.6-Windows-x86_64/bin:$PATH
```

ただし、Cygwinを終了するとリセットされるため、再度実行する必要があります。\
（Cygwin終了の有無に関わらずPATHを追加することも可能ですが、今回は行いません。）

#### - Rのインストール
##### データ解析の再現性
『再現性』とは、同一の結果が同一の実験手法・解析手法によって得られるとき、それら結果の一致の度合いの高さを示す。\
自分の解析結果を研究室内や会社内の他の人が同じ解析をする場合、エクセルなどの表計算ソフトにおけるメニュー操作やコピー＆ペーストを通して行ったデータの集計・加工・分析およびグラフ化（可視化）の作業は記録できず、結果の再現性が低い。\
一方、RやPythonといったプログラミング言語を用いた解析では、スクリプトを作成することでデータの読み込みから結果の出力まで、「手作業」を極力排除してデータ解析を自動化することができ、結果の再現性が高い。
##### Rについて
- Rはデータ分析や統計解析のために開発されたソフトウェアで、プログラミング言語としても十分な機能を備えている。
- プログラミング言語といってもCやJavaなどの言語よりも比較的簡単。順番に処理を記述していけば一通りの分析が可能であり、プログラミング言語としうより「分析ツール」という感覚で使用している人も多い。
- 無料で入手できる統計解析に特化したプログラミング言語で、統計解析で最も広く使われている。
- 基本的な統計解析機能が標準パッケージに含まれており、初期状態で一通りの統計分析を行うことが可能。
- 様々な分野に適した拡張パッケージが提供されており、適宜インストールして使用することが可能。
- Rは開発者のRoss Ihaka、Robert Clifford Gentlemanにより開発され、Rという名称は両者のイニシャルでもある。
- 現在は、R Development Core Teamによってメンテナンス・拡張がされている。
  
1. [https://www.r-project.org/](https://www.r-project.org/)をクリック。

2. 『download R』をクリック 
<img width="1281" alt="スクリーンショット 2023-05-12 17 58 31" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/4aac52a6-1dbc-4b02-8017-1884b22075ee">

3. 任意のミラーサイトのリンクをクリック
<img width="1282" alt="スクリーンショット 2023-05-12 17 59 28" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/6ce700c8-3208-4ecf-9b9b-d554208ca33f">

4. 『Download R for Windows』をクリック。**※以降のインストール方法はOSがWindowsの場合です。その他のOSの場合は、適切なリンクをクリック。**
<img width="1281" alt="スクリーンショット 2023-05-12 17 59 50" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/45d7a416-d118-4976-a01d-28b364377207">

5. 『install R for the first time』をクリック。
<img width="1281" alt="スクリーンショット 2023-05-12 18 00 20" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/0664941a-2ba9-4336-88be-1f89fe75e0b6">

6. 『Download R-4.3.0 for Windows』をクリック。
<img width="1280" alt="スクリーンショット 2023-05-12 18 00 36" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/115e9834-ed4e-40cf-8235-8c2f944805ec">

7. ダウンロードフォルダにある『R-4.3.0-win.exe』をダブルクリック。

8. 『はい』をクリック。
<img width="456" alt="スクリーンショット 2023-05-12 18 01 16" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/ce94e6cd-c523-469f-893a-fe8c88dc1383">

9. 『日本語』が選択されていることを確認して、『OK』をクリック
<img width="298" alt="スクリーンショット 2023-05-12 18 01 28" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/40b2ddeb-88ea-4c6e-85a6-15142f0427d3">

10. 『次へ』をクリック。
<img width="499" alt="スクリーンショット 2023-05-12 18 01 36" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/a2bf35e3-4e8d-455e-9362-e44937d6df86">

11. 『次へ』をクリック。
<img width="499" alt="スクリーンショット 2023-05-12 18 01 45" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/fe46d9ff-eec3-4809-9c09-b2e88f1951ba">

12. ３つともチェックされていることを確認して、『次へ』をクリック。
<img width="498" alt="スクリーンショット 2023-05-12 18 02 13" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/0196f8d4-7821-4a74-82e9-29ea036092d2">

13. 『いいえ』が選択されていることを確認して、『次へ』をクリック。
<img width="498" alt="スクリーンショット 2023-05-12 18 02 25" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/22efda67-df58-44ab-8c1c-06297ece2f84">

14. 『次へ』をクリック。
<img width="498" alt="スクリーンショット 2023-05-12 18 02 35" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/321ecf1e-54fb-410e-935b-502fa433dd4f">

15. 『次へ』をクリック。
<img width="498" alt="スクリーンショット 2023-05-12 18 03 01" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/08a9de90-28c9-4666-9c71-5765772b4206">

16. 『完了』をクリック。
<img width="499" alt="スクリーンショット 2023-05-12 18 03 28" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/d3a92ecd-fcae-4dcd-83d6-ca4f6d91e400">

#### - RStudioのインストール
Rは単独で実行することも可能ですが、統合開発環境（Integrated Development Environment; IDE）というプログラムの記述や実行、デバックなどに必要なツールが一体化されているツールを利用して使用する方が便利です。\
IDEとして、最も一般的なのが『**RStudio**』です。

1. [https://posit.co/download/rstudio-desktop/](https://posit.co/download/rstudio-desktop/)をクリック。
2. 『DOWNLOAD RSTUDIO DESKTOP FOR WINDOWS』をクリック。**※以降のインストール方法はOSがWindowsの場合です。その他のOSの場合は、適切なリンクをクリック。**
<img width="1689" alt="スクリーンショット 2023-05-12 18 06 09" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/1c73a85f-2e90-40d0-b688-72065f49efa7">

3. ダウンロードフォルダにある『RStudio-2023.03.0-386.exe』をダブルクリック。

4. 『はい』をクリック。
<img width="459" alt="スクリーンショット 2023-05-12 18 06 32" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/cdf85869-047e-4fd9-9b87-eb2fc029179b">

5. 『次へ』をクリック。
<img width="581" alt="スクリーンショット 2023-05-12 18 06 42" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/a3cde434-c58c-4ae4-afc8-754d7290502e">

6. 『次へ』をクリック。
<img width="581" alt="スクリーンショット 2023-05-12 18 06 50" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/b1b44146-1b25-4e86-af9b-4f1a639b6491">

7. 『インストール』をクリック。
<img width="581" alt="スクリーンショット 2023-05-12 18 07 01" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/bc1da0ca-1556-4dc7-9c8c-7f934a81cf85">

8. 『完了』をクリック。
<img width="581" alt="スクリーンショット 2023-05-12 18 08 00" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/755296ff-0098-4aff-896a-fc539b1b8ae1">

##### RStudioによるRの起動
1. デスクトップの左下にある検索窓に「**rstudio**」と入力。
<img width="833" alt="スクリーンショット 2023-05-12 19 26 40" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/ee077434-7271-4371-a408-b92b6aeb964f">

2. 『タスクバーにピン留めする』をクリック。
<img width="832" alt="スクリーンショット 2023-05-12 18 09 08" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/bb2fbd8b-49a8-46a0-af8b-8fa4731ef73b">

3. 『開く』をクリック。
<img width="833" alt="スクリーンショット 2023-05-12 18 09 19" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/8c237bbe-a88b-4bce-917d-be5648e3ec80">

4. 『Use your machine's default 64-bit version of R』が選択されていることを確認して、『OK』をクリック。
<img width="390" alt="スクリーンショット 2023-05-12 18 09 33" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/837e2729-a6c3-4b53-b57e-c04035d1442a">

5. クラッシュレポートを提供するかどうかを聞いている。どちらでもかまわない。
<img width="558" alt="スクリーンショット 2023-05-12 18 10 03" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/9594333a-d3a3-4783-a104-a90c4be3d925">

6. 以下の画面が表示されればインストール成功。
<img width="1186" alt="スクリーンショット 2023-05-12 18 10 25" src="https://github.com/yosui-nojima/statistics-C1_R/assets/85273234/c45549af-ddb6-42ac-93ab-083ce71c7434">

#### - Rパッケージのインストール
『Console』に直接入力して実行してもかまわないが、スクリプトとして記録・保存できないため、\
タブから、File → New File → R Scriptを選択し、クリック。\
下記コードを入力し、「Run」をクリック。
```
install.packages("BiocManager")
install.packages("ggplot2")
install.packages("reshape2")
BiocManager::install("GenomicFeatures")
BiocManager::install("clusterProfiler")
BiocManager::install("biomaRt")
BiocManager::install("org.Hs.eg.db")
BiocManager::install("DOSE")
```

# macOS
macOSはUnixベースのOSですので、Cygwinのインストールは必要ありません。\
また、javaはデフォルトでインストールされているため、基本的にはインストール不要です。

#### ターミナルの起動
まずはターミナルを立ち上げます。\
Finder > アプリケーション > ユーティリティ > ターミナル\
下記のアイコンのアプリケーションをダブルクリックして立ち上げます。\
<img width="184" alt="スクリーンショット 2022-03-18 14 59 09" src="https://user-images.githubusercontent.com/85273234/158946076-be0a751f-a8a5-41c7-99c3-6f76346f3ead.png">\
以降は、ターミナルでコマンドラインインターフェース（Command Line Interface; CLI）により各種解析を実行します。

#### - 作業ディレクトリの作成
ホームディレクトリ下に作業ディレクトリを作成するため、下記のコマンドを実行
```
cd
mkdir bulksem
```
#### - NCBI SRA Toolkitのインストール
1. [https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/3.0.10/sratoolkit.3.0.10-mac-x86_64.tar.gz](https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/3.0.10/sratoolkit.3.0.10-mac-x86_64.tar.gz)にアクセスし、```sratoolkit.3.0.10-mac-x86_64.tar.gz```をダウンロードします。
2. ```Downloads```ディレクトリにダウンロードされているため、下記コマンドを実行して作業ディレクトリに移動し、解凍します。
```
mv ~/Downloads/sratoolkit.3.0.10-mac-x86_64.tar.gz ~/bulksem
cd ~/bulksem
tar -zxvf ./sratoolkit.3.0.10-mac-x86_64.tar.gz
```
3. 下記コマンドを実行
```
cd ~/bulksem
cd ./sratoolkit.3.0.10-mac-x86_64/bin/
./prefetch -V
```
4. 実行後、以下のポップアップが表示された場合は、「キャンセル」をクリック

<img width="372" alt="スクリーンショット 2024-02-29 19 52 13" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/7498cf2c-00db-43ba-9ad0-d205107aeec7">


5. Finder > アプリケーション > システム環境設定 > セキュリティとプライバシーをクリックし、以下の画面が表示されているので、「このまま許可」をクリック

<img width="541" alt="スクリーンショット 2024-02-29 19 52 31" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/1efc80da-67dd-4bc3-98f8-0db3dcef717f">

6. 再度下記コマンドを実行
```
./prefetch -V
```

7. 以下の画面が表示されているので、「開く」をクリック

<img width="372" alt="スクリーンショット 2024-02-29 19 52 36" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/25866f3d-4f22-4878-bf37-7c21bfc5e1a4">

8. 以下の画面が表示されるので、「キャンセル」をクリック

<img width="372" alt="スクリーンショット 2024-02-29 19 52 40" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/83d996e8-2618-4d8d-a755-999b0d33328f">

9. 「システム環境設定」→「セキュリティとプライバシー」をクリックし、以下の画面が表示されているので、「このまま許可」をクリック

<img width="555" alt="スクリーンショット 2024-02-29 19 52 53" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/43bcccc3-acbc-4b09-9f60-d58b653fb780">

10. 再度下記コマンドを実行
```
./prefetch -V
```
11. 以下の画面が表示されているので、「開く」をクリック

<img width="372" alt="スクリーンショット 2024-02-29 19 52 58" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/1f927404-0673-42c2-ad9c-b2e15ff88245">

12. 以下のメッセージが表示されれば、```prefetch```コマンドが実行可能になります。

<img width="187" alt="スクリーンショット 2024-02-29 21 19 18" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/48b0c0ea-de8c-4ffc-9f9e-5845ee2556f0">

#### - FastQCのインストール
1. 下記コマンドを実行
```
cd ~/bulksem
curl -OL https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.12.1.zip
unzip fastqc_v0.12.1.zip
cd ./FastQC
./fastqc -v
```
2. ```FastQC v0.12.1```のメッセージが表示されれば、FastQCのインストールのインストール完了

#### - Trimmomaticのインストール
1. 下記コマンドを実行
```
cd ~/bulksem
curl -OL http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/Trimmomatic-0.39.zip
unzip Trimmomatic-0.39.zip
java -jar ./Trimmomatic-0.39/trimmomatic-0.39.jar -version
```
2. ```0.39```のメッセージが表示されれば、Trimmomaticのインストール完了

#### - HISAT2のインストール
1. [https://cloud.biohpc.swmed.edu/index.php/s/zMgEtnF6LjnjFrr/download](https://cloud.biohpc.swmed.edu/index.php/s/zMgEtnF6LjnjFrr/download)にアクセスし、```hisat2-2.2.1-OSX_x86_64.zip```をダウンロードします。
2. ```Downloads```ディレクトリにダウンロードされているため、下記コマンドを実行して作業ディレクトリに移動し、解凍します。
```
mv ~/Downloads/hisat2-2.2.1-OSX_x86_64.zip ~/bulksem
cd ~/bulksem
unzip ./hisat2-2.2.1-OSX_x86_64.zip
```
3. 下記コマンドを実行
```
cd ~/bulksem
cd ./hisat2-2.2.1
./hisat2 --version
```
4. NCBI SRA Toolkitの```prefetch```と同じ要領で```hisat2```に実行許可を与えます。
5. 再度下記コマンドを実行
```
./hisat2 --version
```
6. 以下のメッセージが表示されれば、```hisat2```コマンドが実行可能になります。

<img width="1035" alt="スクリーンショット 2024-02-29 21 31 40" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/2245efdd-561e-459e-9976-4c293a5a2a7b">

7. 下記コマンドを実行
```
./hisat2-build --version
```
8. 同じ要領で実行許可を与えます。
9. 再度下記コマンドを実行
```
./hisat2-build --version
```
10. 以下のメッセージが表示されれば、```hisat2-build```コマンドが実行可能になります。

<img width="873" alt="スクリーンショット 2024-02-29 21 28 27" src="https://github.com/yosui-nojima/bulk_RNA-Seq_Kochi_Univ._2024-0305-0306/assets/85273234/107c5277-d9f3-4d38-bf19-0daae2379424">

#### - featureCountsのインストール
1. [https://sourceforge.net/projects/subread/files/subread-2.0.6/subread-2.0.6-macOS-x86_64.tar.gz/download](https://sourceforge.net/projects/subread/files/subread-2.0.6/subread-2.0.6-macOS-x86_64.tar.gz/download)にアクセスし、```subread-2.0.6-macOS-x86_64.tar.gz```をダウンロードします。
2. ```Downloads```ディレクトリにダウンロードされているため、下記コマンドを実行して作業ディレクトリに移動し、解凍します。
```
mv ~/Downloads/subread-2.0.6-macOS-x86_64.tar.gz ~/bulksem
cd ~/bulksem
tar -zxvf  ./subread-2.0.6-macOS-x86_64.tar.gz
```
3. 下記コマンドを実行
```
cd ~/bulksem
cd ./subread-2.0.6-macOS-x86_64/bin
./featureCounts -v
```
4. NCBI SRA Toolkitの```prefetch```と同じ要領で```featureCounts```に実行許可を与えます。
5. 再度下記コマンドを実行
```
./featureCounts -v
```
6. ```featureCounts v2.0.6```のメッセージが表示されれば、```hisat2```コマンドが実行可能になります。

#### - PATHの追加
絶対PATHの入力を不要にするため、コマンドごとにPATHを追加しておきます。\
下記のコマンドを実行します。（ただし、xxxは各端末で設定されている任意のユーザー名に変更して下さい。）
```
export PATH=/Users/xxx/bulksem/sratoolkit.3.0.10-mac-x86_64/bin:/Users/xxx/bulksem/FastQC:/Users/xxx/bulksem/hisat2-2.2.1:/Users/xxx/bulksem/subread-2.0.6-macOS-x86_64/bin:$PATH
```
ただし、ターミナルを終了するとリセットされるため、再度実行する必要があります。\
（ターミナル終了の有無に関わらずPATHを追加することも可能ですが、今回は行いません。）

## 2. 使用データ
下記のpaired-endでシーケンスされた２サンプルのデータを使用します。\
今回のセミナー用に公共データから１サンプル１０万リードランダムサンプリングしたものです。\
下記のコマンドを実行
```
cd ~/bulksem
curl -OL https://github.com/nojima-q/2021-12-13-15_PBL_analysis/raw/main/sample1_1_100K.fastq.gz
curl -OL https://github.com/nojima-q/2021-12-13-15_PBL_analysis/raw/main/sample1_2_100K.fastq.gz
curl -OL https://github.com/nojima-q/2021-12-13-15_PBL_analysis/raw/main/sample2_1_100K.fastq.gz
curl -OL https://github.com/nojima-q/2021-12-13-15_PBL_analysis/raw/main/sample2_2_100K.fastq.gz
```

## 3. 公共データベースの紹介
![20190605_metacore](https://user-images.githubusercontent.com/85273234/144177090-bbba1e07-08de-4acf-bf6f-b7395a1e104d.jpg)
#### NCBI SRA (https://www.ncbi.nlm.nih.gov/sra)
<img width="1190" alt="スクリーンショット 2021-12-01 14 22 50" src="https://user-images.githubusercontent.com/85273234/144176897-1c463d7f-ca18-41cf-979e-b70fb2db9f0e.png">

####  DDBJ Sequence Read Archive (https://www.ddbj.nig.ac.jp/dra/index.html)
<img width="1792" alt="スクリーンショット 2021-12-01 14 23 16" src="https://user-images.githubusercontent.com/85273234/144177226-15d63718-b705-4f71-b103-dc84aa997a14.png">

####  EBI ENA (https://www.ebi.ac.uk/ena/browser/home)
<img width="1167" alt="スクリーンショット 2021-12-01 14 23 58" src="https://user-images.githubusercontent.com/85273234/144177440-38a84e15-0555-4ae3-9984-08590f751b7f.png">

####  ※データ検索は、スクリーン上で実演します。

## データ取得方法
１．解析したデータセットのAccession numberをNCBI SRA Run Selectorに入力し、『Search』をクリック。
<img width="1792" alt="スクリーンショット 2021-12-01 15 13 56" src="https://user-images.githubusercontent.com/85273234/144181792-1ac601bf-88d8-472e-a30f-d554e3b7d5a1.png">
２．データセット内の全てのデータを解析する場合は、Total行の『Accession List』をクリックし、サンプルごとのAccession numberが記載されたテキストファイル（SRR_Acc_List.txt）をダウンロードする。一部のデータのみ解析する場合は、必要なデータに☑をいれSelected行の『Accession List』をクリックし、SRR_Acc_List.txtをダウンロードする。
<img width="1792" alt="スクリーンショット 2021-12-01 15 19 26" src="https://user-images.githubusercontent.com/85273234/144182595-94ed6341-7722-4efb-8eec-5891f67ca4ae.png">
SRR_Acc_List.txtの内容\
<img width="201" alt="スクリーンショット 2021-12-01 15 24 07" src="https://user-images.githubusercontent.com/85273234/144183038-7209d17e-546a-43a9-8216-0f85d0b5d0b1.png">

SRA Toolkitの```prefetch```、```fastq-dump```を使ってデータを取得する。まず、```prefetch```でsraファイルがダウンロードされる。１つのsraファイルが20GBを超える場合は、-Xまたは--max-size 50Gなどのように最大数を変更する。--option-fileは使わずに直接Accession numberを入力して個別にダウンロードすることも可能です。
```
prefetch  --option-file ~/Downloads/SRR_Acc_list.txt
```
次に```fastq-dump```でsraファイルからfastqファイルを取得する。```PATH```にfastqファイルを格納したいディレクトリのパスを記載。\
```
find . -name '*.sra' -exec fastq-dump --gzip --split-files --outdir ./PATH {} \;
```
- --gzip：圧縮ファイルとして出力する
- --split-files：レイアウトがpaired-endの際に指定する。single-endのときは不要。

## 4. FASTQファイルの形式、クオリティーコントロールについて
### １．FASTQファイルとは
@SRR8615662.1 1 length=101\
TGATGGCCCTGCCTTCGTGGGAACAGAGGCTAAGGCCTTGAG\
+SRR8615662.1 1 length=101\
CCCFFFFFHHHHHJJJJIJJJJIJIJJJJJJJJJJJJJJJJJFIIGIJJIJIJJIJJJJJHHHHHFFFFF\
\
１行目：＠から始まり、リードIDが記載されている\
２行目：シーケンスしたリードの塩基配列\
３行目：＋を記載\
４行目：２行目に記述した各塩基のクオリティ値

### ２．FASTQファイルのクオリティーコントロール
FastQCを使って、FASTQファイルの品質を確認します。\
下記のコマンドを実行します。
```
cd ~/bulksem
mkdir fastqc_results
fastqc -t 4 -o ./fastqc_results/ ./sample1_1_100K.fastq.gz
```
- -t：スレッド数（使用するPC環境に合わせて設定して下さい。）
- -o：出力ディレクトリ

計算が終わると```Analysis complete for sample1_1_100K.fastq.gz```と表示れます。
```fastqc_results```ディレクトリに、```sample1_1_100K_fastqc.html```というファイルが作成されています。\
これを適当なWeb Browserで開いて下さい。

### 3. FastQC解析結果
各QC結果の説明は、下記のブログでよくまとめられています。\
https://imamachi-n.hatenablog.com/entry/2017/03/27/234350

#### Per base sequence quality
リードの各塩基のクオリティスコアを示しています。 Phred quality scoreがだいたいグリーンの領域（Scoreが28以上）に収まっているかどうか確認します。 結果として、クオリティが低いリードは含まれていないことが確認できます。\
<img width="882" alt="スクリーンショット 2021-12-03 12 19 30" src="https://user-images.githubusercontent.com/85273234/144539782-0ec533eb-3533-4e1a-94f6-7b25533e3463.png">

#### Per tile sequence quality
フローセルの各タイルごとのクオリティスコアを示しています。\
Illumina社製の次世代シーケンサーでは、「フローセル」と呼ばれるガラス基板上でDNA合成反応を行います。このフローセルは「タイル」と呼ばれる単位に区切られており、各タイルごとに塩基配列を決定しています。\
シーケンスをかけたときに、例えば特定のタイルに気泡やゴミが入っているとクオリティの低下が見られることがあります。\
特定のタイルで著しいクオリティの低下が見られる場合は、シークエンス時に上記のような問題があったと考えられます。

<img width="883" alt="スクリーンショット 2021-12-03 12 19 40" src="https://user-images.githubusercontent.com/85273234/144539828-47dd135b-650c-46ea-9c12-0467566b7cbf.png">

#### Per sequence quality scores
各リードの全長のクオリティスコアの分布を示しています。 
<img width="854" alt="スクリーンショット 2021-12-03 12 19 59" src="https://user-images.githubusercontent.com/85273234/144539876-2bb62a89-aed8-486b-892c-212b3e9943c9.png">

#### Per base sequence content
各塩基のA, T, G, Cの含有量を示しています。 RNA-seqの場合、それぞれの含有量はほぼ25%ずつになりますが、PAR-CLIPのようにRNA結合タンパク質と結合しているRNA配列を抽出してきている場合、それぞれの含有率に偏りが見られます。
<img width="882" alt="スクリーンショット 2021-12-03 12 20 10" src="https://user-images.githubusercontent.com/85273234/144539910-8ddb14a5-cba5-4ae3-bcb1-efe42fe7320f.png">

#### Per sequence GC content
リードのGC contentsの分布を示しています。 
<img width="861" alt="スクリーンショット 2021-12-03 12 20 18" src="https://user-images.githubusercontent.com/85273234/144539949-a255551b-f00c-4c80-907c-b5c93767308a.png">

#### Per base N content
各塩基中に含まれるNの含有率（塩基を読めなかった箇所）を示しています。 
<img width="880" alt="スクリーンショット 2021-12-03 12 20 28" src="https://user-images.githubusercontent.com/85273234/144540515-9f9c67a5-b570-4262-8097-4d8f36ab8279.png">

#### Sequence Length Distribution
リード長の分布を示しています。 
<img width="855" alt="スクリーンショット 2021-12-03 12 20 37" src="https://user-images.githubusercontent.com/85273234/144540533-0a74b05a-fc62-4892-aad9-50443deeed4c.png">

#### Sequence Duplication Levels
Duplidate readsの含まれている数を示しています。 
<img width="858" alt="スクリーンショット 2021-12-03 12 20 48" src="https://user-images.githubusercontent.com/85273234/144540550-89d8a421-a93c-4a71-96c0-66b0d764af24.png">

#### Overrepresented sequences
頻出する特徴配列が示されています。リード中にアダプター配列などが混入している場合、その配列が示されます。
<img width="879" alt="スクリーンショット 2021-12-03 13 17 24" src="https://user-images.githubusercontent.com/85273234/144544469-dc72869e-1df7-4de3-af65-a9d6d6ef6dc1.png">

#### Adapter Content
各塩基ごとに見たときのリード中に含まれているアダプターの割合を示しています。 あくまで、FastQCに登録されているアダプター配列しか確認していないので、登録されていないアダプター配列を使っていた場合、そのアダプター配列がリード中に混入していても確認できないことがあります。 
<img width="898" alt="スクリーンショット 2021-12-03 13 15 53" src="https://user-images.githubusercontent.com/85273234/144544371-74ddb7ed-97d1-4ffa-b934-50ef78ebd7e5.png">

## 4. アダプターの除去およびリードのトリミング
Trimmomaticを使って、アダプターの除去および低スコアな塩基のトリミングを同時に行います。
アダプター配列を記載したFATSAファイルは[ここ](https://github.com/nojima-q/2021-12-13-15_PBL_analysis/raw/main/Truseq_stranded_totalRNA_adapter.fa)からダウンロード可能です。（今回は、illumina社のTruSeqシリーズの配列を記載しています。自前データで実行する際は、ライブラリー作製キットで使用している配列が記載されたFASTAファイルを用意して実行して下さい。）\
下記はpaired-endでシーケンスしたFASTQファイルの場合です。
```
cd ~/bulksem
curl -OL https://github.com/nojima-q/2021-12-13-15_PBL_analysis/raw/main/Truseq_stranded_totalRNA_adapter.fa
java -jar ./Trimmomatic-0.39/trimmomatic-0.39.jar PE -threads 4 -phred33 ./sample1_1_100K.fastq.gz ./sample1_2_100K.fastq.gz ./sample1_1_100K_trim_paired.fastq.gz ./sample1_1_100K_trim_unpaired.fastq.gz ./sample1_2_100K_trim_paired.fastq.gz ./sample1_2_100K_trim_unpaired.fastq.gz ILLUMINACLIP:Truseq_stranded_totalRNA_adapter.fa:2:30:10 LEADING:20 TRAILING:20 SLIDINGWINDOW:4:20 MINLEN:25
```
- PE：レイアウトがpaired-endシーケンスのときに指定。single-endの場合はSEを指定します。
- -threads：スレッド数（使用するPC環境に合わせて設定して下さい。）
- ILLUMINACLIP：Truseq_stranded_totalRNA_adapter.faはillumina社のTruSeqシリーズのアダプター配列をFASTA形式で記載してもの。後ろの数字は、許容ミスマッチ数:palindrome clip threshold:simple clip thresholdを表す。
- LEADING：5'末端から設定したスコア値未満の塩基をトリム
- TRAILING：3'末端から設定したスコア値未満の塩基をトリム
- SLIDINGWINDOW：左の数字はウィンドウサイズ、右の数字は平均クオリティ値を表します。ウィンドウサイズの範囲内の塩基のスコア平均が設定値よりも低ければ、3'末端側の全ての塩基をトリム。\
- MINLEN：設定値未満の塩基数になったリードを除去する。

### awkコマンドを使ったバッチ処理
サンプル数が多い場合一つ一つコマンドを打って処理するのは面倒です。その場合、下記のようにawkコマンドを使って複数サンプルのコマンドを１つのシェルファイルに記載してバッチ処理することができます。\
変数部分が```%s```に該当します。```%s```の数だけ後部にカンマ区切りの```$1```を記載します。
```
ls sample*_100K.fastq.gz | cut -f1 -d_ | sort | uniq | awk '{printf ("java -jar ./Trimmomatic-0.39/trimmomatic-0.39.jar PE -threads 4 -phred33 %s_1_100K.fastq.gz %s_2_100K.fastq.gz %s_1_100K_trim_paired.fastq.gz %s_1_100K_trim_unpaired.fastq.gz %s_2_100K_trim_paired.fastq.gz %s_2_100K_trim_unpaired.fastq.gz ILLUMINACLIP:Truseq_stranded_totalRNA_adapter.fa:2:30:10 LEADING:20 TRAILING:20 SLIDINGWINDOW:4:20 MINLEN:25 2> %s_trim.txt \n", $1, $1, $1, $1, $1, $1, $1)}' > trim.sh
sh trim.sh
```

### リードトリミング後のFastQC結果
#### Per base sequence quality
リードの各塩基のクオリティスコアを示しています。 Phred quality scoreがだいたいグリーンの領域（Scoreが28以上）に収まっているかどうか確認します。 結果として、クオリティが低いリードは含まれていないことが確認できます。\
<img width="891" alt="スクリーンショット 2021-12-08 13 10 58" src="https://user-images.githubusercontent.com/85273234/145147570-d1b08712-befe-4826-81a4-35c60b3cf85d.png">

#### Per tile sequence quality
フローセルの各タイルごとのクオリティスコアを示しています。\
Illumina社製の次世代シーケンサーでは、「フローセル」と呼ばれるガラス基板上でDNA合成反応を行います。このフローセルは「タイル」と呼ばれる単位に区切られており、各タイルごとに塩基配列を決定しています。\
シーケンスをかけたときに、例えば特定のタイルに気泡やゴミが入っているとクオリティの低下が見られることがあります。\
特定のタイルで著しいクオリティの低下が見られる場合は、シークエンス時に上記のような問題があったと考えられます。

<img width="886" alt="スクリーンショット 2021-12-08 13 11 07" src="https://user-images.githubusercontent.com/85273234/145147294-8814525b-eca2-438c-875b-6e84172595d2.png">

#### Per sequence quality scores
各リードの全長のクオリティスコアの分布を示しています。 
<img width="868" alt="スクリーンショット 2021-12-08 13 11 16" src="https://user-images.githubusercontent.com/85273234/145147297-93a9b9e8-13e7-40a6-b471-1c800af9b62b.png">

#### Per base sequence content
各塩基のA, T, G, Cの含有量を示しています。 RNA-seqの場合、それぞれの含有量はほぼ25%ずつになりますが、PAR-CLIPのようにRNA結合タンパク質と結合しているRNA配列を抽出してきている場合、それぞれの含有率に偏りが見られます。
<img width="886" alt="スクリーンショット 2021-12-08 13 11 23" src="https://user-images.githubusercontent.com/85273234/145147305-7c91dfc9-83ac-474d-9612-8fec8b6d7804.png">

#### Per sequence GC content
リードのGC contentsの分布を示しています。 
<img width="865" alt="スクリーンショット 2021-12-08 13 11 30" src="https://user-images.githubusercontent.com/85273234/145147309-5eba3d04-d3aa-46c7-917b-c566df8bebbe.png">

#### Per base N content
各塩基中に含まれるNの含有率（塩基を読めなかった箇所）を示しています。 
<img width="886" alt="スクリーンショット 2021-12-08 13 11 37" src="https://user-images.githubusercontent.com/85273234/145147321-247d1c38-42ba-4965-a955-186cec9dbc52.png">

#### Sequence Length Distribution
リード長の分布を示しています。 
<img width="869" alt="スクリーンショット 2021-12-08 13 11 46" src="https://user-images.githubusercontent.com/85273234/145147326-bfaef550-03a7-4239-a344-9b06b5666dd1.png">

#### Sequence Duplication Levels
Duplidate readsの含まれている数を示しています。 
<img width="862" alt="スクリーンショット 2021-12-08 13 12 35" src="https://user-images.githubusercontent.com/85273234/145147340-515291c5-de1b-4894-a088-6e97fa8b0ef0.png">

#### Overrepresented sequences
頻出する特徴配列が示されています。リード中にアダプター配列などが混入している場合、その配列が示されます。
<img width="846" alt="スクリーンショット 2021-12-08 13 12 45" src="https://user-images.githubusercontent.com/85273234/145147348-7689cc33-8b84-4d69-9467-0b7218a7973d.png">

#### Adapter Content
各塩基ごとに見たときのリード中に含まれているアダプターの割合を示しています。 あくまで、FastQCに登録されているアダプター配列しか確認していないので、登録されていないアダプター配列を使っていた場合、そのアダプター配列がリード中に混入していても確認できないことがあります。\
<img width="862" alt="スクリーンショット 2021-12-08 13 13 07" src="https://user-images.githubusercontent.com/85273234/145147355-8b0a01f3-bbd7-4e5e-8e59-6e8745454f6c.png">

## 4 リファレンスゲノムファイル、アノテーションファイルの取得
**ゲノムデータのダウンロードはかなり時間を要するため、本セミナーでは実行しません。下記コマンドは今後の参考にして下さい。**

トリミングしたリードは全ゲノム配列が記載されたリファレンスゲノムファイルにマッピングします。\
[Ensembl](https://www.ensembl.org/)は、様々な生物種のゲノム配列情報が格納されているデータベースです。\
ここからヒトのリファレンスゲノムファイルとアノテーションファイル（遺伝子ごとにコードされている染色体と染色体内でのポジションが記載されたファイル）をダウンロードします。\
<img width="1792" alt="スクリーンショット 2021-12-08 14 21 31" src="https://user-images.githubusercontent.com/85273234/145152855-ee648e1f-ae56-4e90-9a53-681ee6f0b079.png">
- まずはEnsemblトップページの『Human』からをクリックします・
- 次のページの右側『Gene annotation』内の『Download FASTA』をクリック。
- ftpサイトの『dna』をクリックすると複数のファイルが閲覧できます。このうち、『Homo_sapiens.GRCh38.dna.primary_assembly.fa.gz』を使用します。
- 次はアノテーションファイルをダウンロードします。
- Humanトップページの『Gene annotation』内の『Download GTF』をクリック。
- ftpサイトの『Homo_sapiens.GRCh38.111.gtf.gz』をダウンロードします。
- リファレンスゲノムファイルとアノテーションファイルを解凍します。

または、下記のコマンドを実行することでもダウンロード・解凍が可能です。
```
cd ~/bulksem
curl -OL https://ftp.ensembl.org/pub/release-101/fasta/homo_sapiens/dna/Homo_sapiens.GRCh38.dna.primary_assembly.fa.gz
curl -OL https://ftp.ensembl.org/pub/release-101/gtf/homo_sapiens/Homo_sapiens.GRCh38.101.gtf.gz
gunzip Homo_sapiens.GRCh38.dna.primary_assembly.fa.gz
gunzip Homo_sapiens.GRCh38.101.gtf.gz
```
2024年3月1日現在の最新版は```release-111```になります。

## 5 リファレンスゲノムへのマッピング
### 5-1 リファレンスゲノムファイルのインデックス化
**ゲノムのインデックス化はかなり時間がかかるため、本セミナーでは実行しません。下記コマンドは今後の参考にして下さい。**

4でダウンロードしたリファレンスゲノムファイルをインデックス化します。一般的にゲノムデータのサイズは大きくなりがちでありそのままでは処理時間がかかってしまうため、インデックス（目次）ファイルを作成して高速にアクセスできるようにします。\
インデックス化に必要なプログラムは、多くの場合マッピングツールに含まれています。\
HISAT2に含まれる```hisat2-build```を使用します。\
インデックス化する前段階として、まずは下記を実行します。それぞれスプライシングサイト、エキソンサイトを抽出するpythonスクリプトです。
```
cd ~/bulksem
./hisat2-2.2.1/extract_splice_sites.py ./Homo_sapiens.GRCh38.101.gtf > ./Homo_sapiens.GRCh38.101.ss
./hisat2-2.2.1/extract_exons.py ./Homo_sapiens.GRCh38.101.gtf > ./Homo_sapiens.GRCh38.101.exon 
```
上記の２ファイルも使って、インデックス化します。
```
hisat2-build -p 4 --ss ./Homo_sapiens.GRCh38.101.ss --exon ./Homo_sapiens.GRCh38.101.exon ./Homo_sapiens.GRCh38.dna.primary_assembly.fa ./GRCh38.101
```
- -p：スレッド数（使用するPC環境に合わせて設定して下さい。）
- -ss：extract_splice_sites.pyで作成したファイルを指定
- -exon：extract_exons.pyで作成したファイルを指定

**本セミナーでは下記リンクからインデックス化済みリフェレンスゲノムファイルを取得して下さい。**

[https://www.dropbox.com/scl/fi/tjuf4u9s81rrg0wtya8s6/GRCh38.101.tar.gz?rlkey=63uz24zbvc7jjssez3tfdmpjl&dl=0](https://www.dropbox.com/scl/fi/tjuf4u9s81rrg0wtya8s6/GRCh38.101.tar.gz?rlkey=63uz24zbvc7jjssez3tfdmpjl&dl=0)\
ダウンロード後、```GRCh38.101.tar.gz```をWindows11の場合は```C:\cygwin64\home\xxx\bulksem```に、macOSの場合は```~/bulksem```に移動して下さい(```xxx```は任意のユーザー名に変更すること。)\
下記コマンドを実行
```
tar -zxvf GRCh38.101.tar.gz
```

### 5-2 マッピング
ゲノムへのマッピングを行います。今回は時間短縮のため、１０万リードランダムサンプリングしたFASTQファイル（最初にダウンロードしたファイル）を5-1で作成したインデックス化したリファレンスゲノムにマッピングします。
```
hisat2 -p 4 --dta -x ./GRCh38.101/GRCh38.101 -1 ./sample1_1_100K_trim_paired.fastq.gz -2 ./sample1_2_100K_trim_paired.fastq.gz -S sample1_hisat2.sam 2> sample1_hisat2_log.txt
```
- -p：スレッド数（使用するPC環境に合わせて設定して下さい。）
- --dta：アセンブラーなど下流の解析ツールを使用する際のオプション。またメモリ使用量を改善する。
- -x：インデックス化したリファレンスゲノムファイル
- -1：FowardリードのFastqファイルを指定
- -2：ReverseリードのFastqファイルを指定
- -S：出力するSAMファイル名
- 2>：標準エラー出力。Mapping rate等をテキストファイルとして出力する。

※バッチ処理をする場合は前述のawkコマンドを使用して下さい。

## 6 マッピングデータから遺伝子ごとにリードのカウントデータを取得する
マッピング結果であるSAMファイルからgeneごとまたはtranscriptごとにリードのカウント数を出力します。\
```featureCounts```を使用します。
```
curl -OL https://ftp.ensembl.org/pub/release-101/gtf/homo_sapiens/Homo_sapiens.GRCh38.101.gtf.gz
gunzip Homo_sapiens.GRCh38.101.gtf.gz
featureCounts -O -M -T 18 -p -t exon -g gene_id -a ./Homo_sapiens.GRCh38.101.gtf -o sample_count.txt sample*_hisat2.sam
```
- -O：複数のfeatureで定義されている特定のゲノム領域にマッピングされたリードもカウントする
- -M：マルチマッピングされたリードもカウントする
- -T：スレッド数（使用するPC環境に合わせて設定して下さい。）
- -p：paired-endの場合に指定（1リードペアを1カウントする。）
- -t：GTFファイルのfeature領域（3カラム目、exon, gene, CDS等）を指定
- -g：gene levelでカウントしたい場合は```gene_id```を、transcript levelでカウントしたい場合は```transcript_id```を指定する
- -a：アノテーションファイル（GTFファイル等）を指定
- -o：出力ファイル名を指定

遺伝子IDとカウント値のみを抽出します。
```
cut -f1,7- ./sample_count.txt | grep -v ^\# > ./featureCounts_output.txt 
```

## 7 カウントデータをTPM値に変換する
６で出力したファイルは本セミナー用のスモールデータです。ある疾患の公共RNA-Seqデータ（３９サンプル）のカウント値を出力したファイル[```featureCounts_all_output.txt```](https://github.com/nojima-q/2021-12-13-15_PBL_analysis/raw/main/featureCounts_all_output.txt)を用意しました。
下記コマンドをCygwin(Windows 11)またはターミナル(macOS)で実行してファイルをダウンロードします。

```
cd ~/bulksem
curl -OL https://github.com/nojima-q/2021-12-13-15_PBL_analysis/raw/main/featureCounts_all_output.txt
```

ここからはRStudioで作業します。\
RStudioを起動して下さい。\
まず初めに作業ディレクトリを移動します。\
下記コードを実行
### Windows 11の場合
```
setwd("C:/cygwin64/home/xxx/bulksem/") #xxxは任意のユーザー名に変更すること。
```

### macOSの場合
```
setwd("/User/xxx/bulksem/") #xxxは任意のユーザー名に変更すること。
```

featureCountsの出力ファイルからカウントデータを抽出したファイルを読み込みます。\
```
data <- read.table("./featureCounts_all_output.txt", header = TRUE, row.names = 1, sep = "\t")
```

続いて、GTFファイルからgene lengthを抽出します。```featureCounts_all_output.txt```を出力した際に使用したGTFファイルのバージョンがGRCh38.101だったため、そのバージョンのGTFファイルを指定しています。バージョンが違うとエラーになります。
**下記スクリプトの実行は少し時間がかかるため、、本セミナーでは実行しません。今後の参考にして下さい。**
```
library(GenomicFeatures)
txdb <- makeTxDbFromGFF("./Homo_sapiens.GRCh38.101.gtf", format = "gtf")
exons.list.per.gene <- exonsBy(txdb, by = 'gene', use.names = FALSE) #featureCountsでtranscriptレベルでカウントした場合は、by引数の'gene'を'tx'に、use.names引数をTRUEに変更します。
exonic.gene.sizes <- lapply(exons.list.per.gene, function(x){sum(width(reduce(x)))})
exonic.gene.sizes.2 <- as.numeric(exonic.gene.sizes)
names(exonic.gene.sizes.2) <- names(exonic.gene.sizes)
exonic.gene.sizes.2 <- data.frame(as.matrix(exonic.gene.sizes.2))
exonic.gene.sizes.2$ensembl_gene_id <- row.names(exonic.gene.sizes.2)

```

**今回は[事前に用意したファイル](https://github.com/nojima-q/2021-12-13-15_PBL_analysis/raw/main/exonic_gene_sizes_2_GRCh38.101.rds)を読み込んで使用します。**

下記コマンドをCygwin(Windows 11)またはターミナル(macOS)で実行してファイルをダウンロードします。
```
cd ~/bulksem
curl -OL https://github.com/nojima-q/2021-12-13-15_PBL_analysis/raw/main/exonic_gene_sizes_2_GRCh38.101.rds
```
RStudioに戻って
```
exonic.gene.sizes.2 <- readRDS("./exonic_gene_sizes_2_GRCh38.101.rds")
gene.len <- exonic.gene.sizes.2$as.matrix.exonic.gene.sizes.2.
names(gene.len) <- exonic.gene.sizes.2$ensembl_gene_id
gene.list.order <- row.names(data)
gene.len.sorted <- gene.len[gene.list.order]
tpm <- function(count, gene.len) {
  rate <- count / gene.len
  rate / sum(rate) * 1e6
}
```
カウントデータは、Transcript Per Million(TPM)値に変換します。TPMは、まずカウントデータを遺伝子長の長さで補正し、総リード数を100万リードにした値です。他にFPKMなどあり、こちらは先に総リード数を100万にしてから遺伝子長で補正します。したがって、最終的にサンプルごとに総リード数が異なることになるためサンプル間で比較する際はTPMの方が適しています。このような理由から最近ではTPM値を用いることが推奨されています。
```
tpms <- apply(data, 2, function(x) tpm(count = x, gene.len = gene.len.sorted))
```
サンプルの総リード数が１００万になっているか確認します。
```
colSums(tpms)
```
TPM値に1を足してlog2変換します。
```
tpms <- data.frame(log2(tpms + 1))
```

## 8 DEGsの検出
発現変動遺伝子（Differentially expressed genes; DEGs）の抽出を行います。\
今回の公共データは患者20人、健常者19人からなるデータです。

```
disease <- as.matrix(tpms[,1:20])
control <- as.matrix(tpms[,21:39])
r1 <- matrix(nrow = nrow(disease))
for(i in 1:nrow(disease)){
  r1[i,] <- t.test(disease[i,], control[i,], var.equal=F, paired=F, alternative = "two.sided")$p.value
}
wel <- data.frame(tpms, r1)
wel <- na.omit(wel)
library(ggplot2)
ggplot(wel, aes(x = r1)) + geom_histogram(position = "dodge", alpha = 1, binwidth = 0.01)
```
P値のヒストグラムから、小さなP値の比率が高いことから、患者・健常者間で発現差異のある遺伝子は多いと考えられます。\
![Rplot02](https://user-images.githubusercontent.com/85273234/145535858-c9cb15fc-1a55-4d8f-b5de-d125b51aa7fa.jpeg)
Benjamini and Hochberg法によるP値の補正
```
q.value <- data.frame(p.adjust(p = wel$r1, method = "BH")) #P値の補正
wel <- data.frame(wel, q.value) #元データと結合
```
Fold changeの算出
```
disease.mean <- rowMeans(wel[,1:20]) #患者サンプル
control.mean <- rowMeans(wel[,21:39]) #健常者サンプル
wel$FC <- disease.mean - control.mean #Fold changeの算出
```
基本的統計量が全て算出されましたので、DEGsを定義します。\
今回は、|FC| ≥ 1かつadjusted P-value < 0.05を満たす遺伝子群をDEGsとします。
```
wel$Color = ifelse(abs(wel$FC) >= 1 & wel$p.adjust.p...wel.r1..method....BH.. < 0.05, "DEG", "non-DEG")
```

Volcano plotでDEGsを可視化します。
```
ggplot(wel, aes(x=FC, y=-log10(p.adjust.p...wel.r1..method....BH..), colour=Color)) + theme(panel.background = element_blank(), axis.line=element_line(colour = "black"), panel.grid = element_line(colour = "gray")) +
  geom_point(alpha=1, size=3) + xlab(expression(log[2]("Disease / Control"))) + ylab(expression(-log[10]("adjusted P-value"))) +
  theme(legend.position = "right", plot.title = element_text(size = rel(1.5), hjust = 0.5), axis.title = element_text(size = rel(1.25))) +
  geom_hline(yintercept=1.30102999566, linetype="dashed", colour="#00ff00", size = 1) +
  geom_vline(xintercept=1, linetype="dashed", colour="#00ff00", size = 1) +
  geom_vline(xintercept=-1, linetype="dashed", colour="#00ff00", size = 1) +
  theme(legend.title=element_text(size=30, face = "plain") , legend.text=element_text(size=30, face = "plain")) +
  theme(plot.title=element_text(size=30, colour="black", face = "bold",hjust = 1.0), axis.text=element_text(size=25, colour="black", face = "plain"), axis.title=element_text(size=30, face = "plain"))
```
![Rplot01](https://user-images.githubusercontent.com/85273234/145540365-ae044914-6fc4-4d7f-845a-176f6f5c777b.jpeg)
赤が|FC| ≥ 1かつadjusted P-value < 0.05を満たす遺伝子群、青が満たさなかった遺伝子群です。\
縦の緑破線がFCの閾値、横の緑破線がadjusted P-valueの閾値を示します。

## 9 エンリッチメント解析
疾患データでどのような生物学的イベントが起きているのか、どのようなパスウェイが動いているのか調査します。\
DEGsを入力データとしてGene Ontology(GO)解析とKEGGパスウェイ解析について紹介します。\
今回の解析方法では、入力データとしてFC値とEntrez gene IDが必要です。\
そこで、biomaRtライブラリーを使ってEnsembl gene IDからEntrez gene IDに変換します。
```
library(biomaRt)
DEG <- data.frame(row.names(wel[wel$Color == "DEG",]), wel[wel$Color == "DEG",]$FC)
colnames(DEG) <- c("ensembl_gene_id", "FC")
db <- useMart("ensembl", dataset = "hsapiens_gene_ensembl")
hg <- useDataset("hsapiens_gene_ensembl", mart = db)
res.gene <- getBM(attributes = c("ensembl_gene_id", "entrezgene_id"), filters = "ensembl_gene_id", values = DEG, mart = hg, uniqueRows=T)
res.gene <- na.omit(res.gene)
DEG2 <- merge(res.gene, DEG, by = "ensembl_gene_id")
```
上記４、５行はbiomaRt側のサーバーが停止しているとエラーとなります。その場合は[事前に用意したRData](https://github.com/nojima-q/2021-12-13-15_PBL_analysis/raw/main/biomaRt_104.RData)を読み込んで使用して下さい。
```
load(file = "./biomaRt_104.RData")
```
### 9-1 GO解析
GO解析では、Biological Process(BP)、Molecular Function(MF)、Cellular Component(CC)の３種類があります。\
下記はBPを選択していますが、```ont```引数を変更すればMF、CCを選択可能です。```ALL```を指定すると全て解析対象となります。
棒グラフやネットワークグラフなど様々な方法で描写することが可能です。```showCategory```引数で表示するterm数を指定できます。\
```
library(clusterProfiler)
library(org.Hs.eg.db)
#GOエンリッチメント解析を実行
ego.result <- enrichGO(gene = as.character(DEG2$entrezgene_id),
                                        universe      = NULL,
                                        OrgDb         = org.Hs.eg.db,
                                        ont           = "BP", #"BP","CC","MF","ALL"から選択
                                        pAdjustMethod = "BH",
                                        pvalueCutoff  = 0.05,
                                        qvalueCutoff  = 0.05, 
                                        readable      = TRUE) #Gene IDを遺伝子名に変換

ego.result.simple <- simplify(ego.result) #GO termの冗長性を除去
barplot(ego.result.simple, drop=TRUE, showCategory=30)
dotplot(ego.result.simple)
emapplot(ego.result.simple)
goplot(ego.result.simple)
```
<img width="1147" alt="スクリーンショット 2021-12-12 18 06 39" src="https://user-images.githubusercontent.com/85273234/145706607-9a6d0792-cb9d-4ee4-b3e3-ffceb114c294.png">

### 9-2 KEGGパスウェイ解析
KEGG(Kyoto Encyclopedia of Genes and Genomes)パスウェイ解析を行います。\
GO解析と同様に様々な方法で描写可能です。```showCategory```引数で表示するterm数を指定できます。
```
ego.result.kegg <- enrichKEGG(gene = as.character(DEG2$entrezgene_id),
                                               universe      = NULL,
                                               organism = "hsa",
                                               keyType = "ncbi-geneid",
                                               pAdjustMethod = "BH",
                                               pvalueCutoff  = 0.05,
                                               qvalueCutoff  = 0.05)

barplot(ego.result.kegg, showCategory=10)
dotplot(ego.result.kegg, showCategory=10)
emapplot(ego.result.kegg, showCategory=10)
```
<img width="1146" alt="スクリーンショット 2021-12-12 18 14 53" src="https://user-images.githubusercontent.com/85273234/145706790-54ac8cc7-0ce1-440f-aeb9-2db8d6d95922.png">

### 9-3 Disease enrichment解析
Disease enrichment解析では、入力した遺伝子リストがどのような疾患に関わっているか調査することができます。
```
library(DOSE)
DEG3 <- DEG2[abs(DEG2$FC) >= 2,]
geneList2 <- DEG3[,3]
names(geneList2) <- DEG3$entrezgene_id
edo2 <- enrichDGN(DEG3$entrezgene_id)
barplot(edo2, showCategory=20, font.size = 12)
edox2 <- setReadable(edo2, 'org.Hs.eg.db', 'ENTREZID')
cnetplot(edox2, foldChange=geneList2, showCategory = 11, layout = "kk", fixed = TRUE, categorySize = "geneNum", max.overlaps = 1000)
```
<img width="1094" alt="スクリーンショット 2021-12-12 18 25 39" src="https://user-images.githubusercontent.com/85273234/145707105-d7924e1d-5333-4ccb-9f06-69078c9049eb.png">

## 今回使用したデータセット
### 元論文
特発性肺線維症(Idiopathic pulmonary fibrosis; IPF)のデータを使用しました。\
Disease enrichment解析では```Pulmonary Fibrosis```や```Idiopathic Pulmonary Fibrosis```といったタームがエンリッチしています。
<img width="999" alt="スクリーンショット 2021-12-12 18 27 39" src="https://user-images.githubusercontent.com/85273234/145707755-77fdddf0-1b47-41b0-b213-dc06dfa3d533.png">
### 再解析論文
<img width="965" alt="スクリーンショット 2021-12-13 10 02 57" src="https://user-images.githubusercontent.com/85273234/145737436-da0ac0eb-1c17-4b35-9f82-b82846251ff2.png">
<img width="594" alt="スクリーンショット 2021-12-13 10 06 14" src="https://user-images.githubusercontent.com/85273234/145737543-f383ff2b-0fe4-43c8-b35b-ffc72842a537.png">
