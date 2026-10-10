[English](../en/product-info.md) | [简体中文](../zh-hans/product-info.md) | [繁體中文](../zh-hant/product-info.md) | [Deutsch](../de/product-info.md) | [Español](../es/product-info.md) | [Français](../fr/product-info.md) | [Italiano](../it/product-info.md) | 日本語 | [한국어](../ko/product-info.md) | [Português (BR)](../pt-br/product-info.md) | [Português (PT)](../pt-pt/product-info.md)

<title>製品情報</title>

# 製品概要

LeKiwi は、SIGRobotics-UIUC(イリノイ大学アーバナ・シャンペーン校のロボティクス関心グループ)の主導のもとで開発されています。教育、研究、産業オートメーションの分野でロボティクス技術の普及を促進する、低コストで柔軟性の高いオープンソースのロボットプラットフォームを提供します。ハードウェア設計(3Dプリントファイル)、ソフトウェアスタック(LeRobot フレームワーク互換)、チュートリアルはすべてオープンソースで、ユーザー定義の拡張にも対応しています。

LeKiwi は、移動プラットフォームとリーダー・フォロワーアームで構成されています。リーダー・フォロワーアームは、構造に3Dプリント部品を、駆動関節に6つの12V Feetech サーボを使用しています。リーダーアームは固定プラットフォーム上にあり、1つのサーボドライバ基板を使用して、USB-C 経由でコンピューターに接続します。フォロワーアームは移動プラットフォームに搭載され、3つの12V Feetech サーボで駆動されます。フォロワーアームは1つのサーボドライバ基板を使用し、Raspberry Pi に接続した USB-C 経由で制御します。

LeKiwi は LeRobot(Hugging Face のオープンソース ロボット機械学習フレームワーク)を深く統合し、模倣学習、データ収集、ポリシー学習をサポートしています。PyTorch 上に実装され、事前学習済みモデル、データセット、シミュレーション環境を含み、Stanford ALOHA などの著名なオープンソースデータセットと互換です。DORA フレームワーク(分散データフローエンジン)を使用して低遅延のハードウェア・アルゴリズム間通信を実現し(Python のパフォーマンスは ROS2 の17倍高速)、ホットリロードをサポートしているため、再起動せずにコードをリアルタイムで調整できます。

LeKiwi は教育と入門レベルの研究に非常によく適しています。ロボティクス入門教育では、組み立てやプログラミングから AI ポリシーのデプロイまでを網羅するエンドツーエンドのチュートリアルを提供します。研究検証では、模倣学習研究(例えば、VR で記録した人間の操作動画からロボットを学習させる)をサポートし、花粉ロボット Ready2 の事例では、15秒の動画50本で2時間学習するだけで、服を畳んだり鍵を差し込んだりといったタスクを学習しました。産業プロトタイピングでは、自動化ソリューション(例えばマテリアルハンドリングや精密組立)の低コストな検証を可能にします。

<sheet sheet-id="BZbDmJ" token="YJxcsShh0h3eBTtTl7Dc7yD6nMf"></sheet>

<sheet sheet-id="6Yh7Ph" token="YJxcsShh0h3eBTtTl7Dc7yD6nMf"></sheet>

<sheet sheet-id="tobJtD" token="YJxcsShh0h3eBTtTl7Dc7yD6nMf"></sheet>

<sheet sheet-id="VxQH4Y" token="YJxcsShh0h3eBTtTl7Dc7yD6nMf"></sheet>
